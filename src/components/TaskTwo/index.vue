<template>
    <div class="task">
        <span>Задача 2.</span> Розробити компонент (з підтримкою v-model), який дозволяє вводити шлях до файлу js (URL,
        що закінчується розширенням js). При заданні модифікатора checkPath відображати червоним фоном input, якщо шлях
        некоректний.
    </div>
    <div>
        <input-link-to-j-s v-model="fileLink" />
    </div>
</template>

<script>
import InputLinkToJS from '@/components/TaskTwo/InputLinkToJS.vue'
export default {
    name: 'TaskTwo',
    components: {
        InputLinkToJS,
    },
    data() {
        return {
            fileLink: null,
        }
    },
}
</script>

<style lang="scss" scoped>
.task {
    padding: 10px;
    text-align: justify;
    margin-bottom: 15px;
    & span {
        font-size: 20px;
        color: goldenrod;
    }
}
</style>
