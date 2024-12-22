<template>
    <div class="todo-item">
        <input type="checkbox" v-model="completed" @change="toggleComplete" />
        <span :class="{ completed: completed }">{{ text }}</span>
        <button @click="$emit('remove', id)">Удалить</button>
    </div>
</template>

<script>
export default {
    props: {
        id: Number,
        text: String,
        completed: Boolean
    },
    data() {
        return {
            completed: this.completed
        };
    },
    methods: {
        toggleComplete() {
            this.$emit('toggle', this.id);
        }
    }
};
</script>

<style scoped>
.completed {
    text-decoration: line-through;
}

.todo-item {
    border: 1px solid #85b813;
    border-radius: 5px;
    padding: 10px;
    display: flex;
    align-items: center;
    width: 100%;
}

input {
    margin-right: 10px;
}

button {
    margin-left: auto;
    background: #8d1c2c;
}
</style>