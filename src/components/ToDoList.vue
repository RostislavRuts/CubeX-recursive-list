<template>
    <ul class="todolist">
        <ToDoItem
                :item="item"
                :index="index"
                v-for="(item, index) in items"
                :key="item.id"
                @deleteTask="deleteTask"/>

        <AddTask
                @add-main-list="addTask"
                :task="task"
        />
    </ul>
</template>

<script>
    import ToDoItem from '@/components/ToDoItem';
    import AddTask from '@/components/AddTask';
    export default {
        components: {
            ToDoItem,
            AddTask
        },
        data() {
            return {
                items: [],
                task: 'Task'
            }
        },
        methods: {
            addTask(task) {
                this.items.push(task)
                console.log(this.items)
            },
            deleteTask(index) {
                this.items.splice(index, 1)
            }
        }
    }
</script>