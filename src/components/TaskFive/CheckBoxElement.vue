<template>
    <h3>{{ title }}</h3>
    <div class="form__check">
        <label v-for="(element, index) in dataArray" :key="index">
            <input type="checkbox" :value="element" v-model="checkedBox" />
            {{ element }}</label
        >
    </div>
</template>

<script>
export default {
    name: 'CheckBoxElement',
    props: {
        title: {
            type: String,
        },
        dataArray: {
            type: Object,
            default: () => ({}),
        },
        modelTitle: {
            type: String,
        },
        modelValue: {
            type: Array,
            default: () => [],
        },
    },
    computed: {
        checkedBox: {
            get() {
                return this.modelValue
            },
            set(val) {
                this.$emit('update:modelValue', val)
            },
        },
    },
}
</script>

<style lang="scss" scoped>
.form__check {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    row-gap: 5px;
}
</style>
