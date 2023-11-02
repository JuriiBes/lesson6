<template>
    <div class="task">
        <span>Задача 4.</span> Розробити компонент для вводу віку користувача та імені. Робити форматування при заданні
        відповідних модифікаторів відповідних полів input:
        <ul>
            <li>ім’я користувача - у випадку порожнього поля (червони фон)</li>
            <li>вік (вік менший за 18 – колір фону червоний, інакше – зелений).</li>
        </ul>
    </div>
    <div class="custom__body">
        <form-name-age-user v-model:nameUser="userName" v-model:ageUser="userAge" />
    </div>
</template>

<script>
import FormNameAgeUser from '@/components/TaskFour/FormNameAgeUser.vue'
export default {
    name: 'TaskFour',
    components: {
        FormNameAgeUser,
    },
    data() {
        return {
            userName: null,
            userAge: null,
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
