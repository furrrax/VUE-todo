<template>
    <div>
        <form @submit.prevent="addTodo">
            <input class="text-input" v-model="newTodoText" placeholder="Новая задача" />
            <button class="btn" type="submit">Добавить</button>
        </form>
        <div class="todo-list">
            <TodoItem v-for="todo in todos" :key="todo.id" :id="todo.id" :text="todo.text" :completed="todo.completed" @remove="removeTodo" @toggle="toggleTodo" />
        </div>
    </div>
</template>

<script>
import TodoItem from './TodoItem.vue';

export default {
    components: {
        TodoItem
    },
    data() {
        return {
            newTodoText: '',
            todos: [],
            nextId: 1
        };
    },
    methods: {
        addTodo() {
            if (this.newTodoText.trim() === '') return;
            this.todos.push({
                id: this.nextId++,
                text: this.newTodoText,
                completed: false
            });
            this.newTodoText = '';
        },
        removeTodo(id) {
            this.todos = this.todos.filter(todo => todo.id !== id);
        },
        toggleTodo(id) {
            const todo = this.todos.find(todo => todo.id === id);
            if (todo) {
                todo.completed = !todo.completed;
            }
        }
    }
};
</script>

<style scoped>
form {
    display: flex;
    align-items: center;
    gap: 20px;
    margin-bottom: 20px;
    border-radius: 10px;
    padding: 20px;
    border: 1px solid #000000;
    box-shadow: 0px 4px 4px rgba(255, 255, 255, 0.25);
}

.text-input {
    border: 1px solid #000000;
    background: #ffffff;
    padding: 10px;
    border-radius: 5px;
    color: #000000;
}

.btn {
    background: #85b813;
}

.todo-list {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 15px;
}
</style>