<template>
    <div class="task__body">
        <div class="task__item"><task-one /></div>
        <div class="task__item"><task-two /></div>
        <div class="task__item"><task-three /></div>
        <div class="task__item"><task-four /></div>
        <div class="task__item"><task-five /></div>
        <div class="task__item"><task-six /></div>
    </div>
</template>

<script>
import TaskOne from '@/components/TaskOne/index.vue'
import TaskTwo from '@/components/TaskTwo/index.vue'
import TaskThree from '@/components/TaskThree/index.vue'
import TaskFour from '@/components/TaskFour/index.vue'
import TaskFive from '@/components/TaskFive/index.vue'
import TaskSix from '@/components/TaskSix/index.vue'
export default {
    name: 'App',
    components: {
        TaskOne,
        TaskTwo,
        TaskThree,
        TaskFour,
        TaskFive,
        TaskSix,
    },
}
</script>

<style lang="scss">
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 30px;
}

.task {
    // .task__body
    &__body {
        display: flex;
        flex-direction: column;
        row-gap: 25px;
    }
    // .task__item
    &__item {
        border-radius: 25px;
        border: 2px solid yellowgreen;
        box-shadow: 1px 1px 10px 1px yellowgreen;
        padding: 10px;
    }
}
</style>
