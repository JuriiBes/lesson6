<template>
    <div class="task">
        <span>Задача 3.</span> Розробити компонент (з підтримкою v-model), який дозволяє вводити e-mail з домену “edu”
        (приклад: ivan-hopko@inv.mn.edu). Частинка «@inv.mn.edu» додається автоматично (користувач не вводить її). При
        заданні модифікатора check відображати червоним фоном input, якщо некоректний.
    </div>
    <div class="custom__body"><input-e-mail v-model="userMail" /></div>
</template>

<script>
import InputEMail from '@/components/TaskThree/InputEMail.vue'
export default {
    name: 'TaskThree',
    components: {
        InputEMail,
    },
    data() {
        return {
            userMail: null,
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
