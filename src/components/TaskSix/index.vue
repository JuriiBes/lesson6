<template>
    <div class="task">
        <span>Задача 6.</span> Створити компонент - форму для вводу даних кредитної карти (на зразок поданого прикладу).
        При вводі “EXPIRY DATE” розділювач додається автоматично.
    </div>
    <card-input
        v-model:cardNumber.digitsOnly.separate4Digits="numberCard"
        v-model:cardDateExpiry.digitsOnly.separate2Digits="dateExpiryCard"
    />
</template>

<script>
import CardInput from '@/components/TaskSix/CardInput.vue'
export default {
    name: 'TaskSix',
    components: {
        CardInput,
    },
    data() {
        return {
            numberCard: null,
            dateExpiryCard: null,
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
