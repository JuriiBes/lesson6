<template>
    <div class="task">
        <span>Задача 1.</span> Розробити компонент для введення віку користувача (з підтримкою v-model). При заданні
        модифікатора check не допускати введення некоректного віку (вік не може бути більшим за 150). При заданні
        модифікатора setColor задавати фон (вік менше 10 – зелений, від 10 до 21 – жовтий, інакше – оранжевий).
    </div>
    <div class="custom__body">
        <input-custom v-model="ageValue" />
    </div>
</template>

<script>
import InputCustom from '@/components/TaskOne/InputCustom.vue'
export default {
    name: 'TaskOne',
    components: {
        InputCustom,
    },
    data() {
        return {
            ageValue: null,
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
