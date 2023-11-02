<template>
    <div class="filter__body">
        <div>
            <check-box-element title="Магазини:" :dataArray="shops" v-model="checkedShop" />
            <!-- @click="changeShops" /></div> -->
        </div>
        <div>
            <check-box-element title="Бренди:" :dataArray="brands" v-model="checkedBrands" />
            <!-- @click="changeBrands" />+ -->
        </div>
    </div>
</template>

<script>
import CheckBoxElement from './CheckBoxElement.vue'

export default {
    name: 'ProductsFilters',

    components: {
        CheckBoxElement,
    },
    data() {
        return {
            shops: null,
            brands: null,
            checkedShop: [],
            checkedBrands: [],
        }
    },
    props: {
        dataNotebooks: {
            type: Array,
            default: () => [],
        },
    },
    watch: {
        checkedShop(newValue) {
            this.$emit('clickCheckShop', newValue)
        },
        checkedBrands(newValue) {
            this.$emit('clickCheckBrand', newValue)
        },
    },
    methods: {
        sortShops() {
            let set = new Set()
            this.dataNotebooks.forEach((element) => {
                set.add(element.shop)
            })
            this.shops = set
        },
        sortBrands() {
            let set = new Set()
            this.dataNotebooks.forEach((element) => {
                set.add(element.brand)
            })
            this.brands = set
        },
    },
    created() {
        this.sortShops()
        this.sortBrands()
    },
}
</script>

<style lang="scss" scoped></style>
