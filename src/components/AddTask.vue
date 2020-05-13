<!--Этот компонент - форма для добавления новых ел-тов основного списка-->
<template>
    <form @submit.prevent="addTask">
        <input type="text" v-model="title" placeholder="Enter note name">
        <button type="submit">Add New {{task}}{{subtasks}}</button>
    </form>
</template>

<script>
    export default {
        data() {
            return {
                title: ""
            };
        },
        props: ['task', 'subtasks'],
        // props: {
        //   task: {
        //       required: true
        //   },
        //     subtasks: {
        //       required: true
        //     }
        // },
        methods: {
            addTask() {
                if (this.title.trim()) {
                    const id = Math.floor(Math.random() * 10)
                    const task = {
                        id,
                        title: this.title,
                        subtasks: []
                    };
                    this.$emit("add-main-list", task);
                    this.title = "";
                }
            }
        }
    };
</script>

<style>
    form {
        width: 50%;
        display: flex;
        justify-content: space-between;
    }
    input {
        width: 50%;
    }
</style>