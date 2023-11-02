<template>
    <div class="task">
        <span>Задача 5.</span> Спробуйте відтворити фрагмент. Компонент ProductsFilters через v-model повертає 2
        значення фільтра: продавець, бренд. При заданні модифікатора “check” відображати секцію зеленою рамкою, якщо
        фільтр з відповідної секції (продавець чи бренд) не обрано.
    </div>
    <div class="product__body">
        <products-filters
            :dataNotebooks="notebooksData"
            class="product__filter"
            @clickCheckShop="selectShop"
            @clickCheckBrand="selectBrand"
        />
        <product-list :productFilterData="filterProduct()" class="product__list" />
    </div>
</template>

<script>
import ProductsFilters from './ProductsFilters.vue'
import ProductList from './ProductList.vue'
import { notebooksData } from '@/constants/notebooksData.js'
export default {
    name: 'TaskFive',
    components: {
        ProductsFilters,
        ProductList,
    },
    data() {
        return { notebooksData, selectShops: [], selectBrands: [] }
    },
    methods: {
        selectShop(arr) {
            this.selectShops = [...arr]
            console.log('selectShops')
            console.log(this.selectShops)
        },
        selectBrand(arr) {
            this.selectBrands = [...arr]
            console.log('selectBrands')
            console.log(this.selectBrands)
        },
        filterCard(arrToFilter, arrFilter, category) {
            return arrToFilter.filter((card) => {
                for (const elem of arrFilter) {
                    if (elem === card[category]) return card
                }
            })
        },
        filterDataProduct() {
            let result = this.filterCard(this.notebooksData, this.selectShops, 'shop')
            return this.filterCard(result, this.selectBrands, 'brand')
        },

        filterProduct() {
            if (this.selectShops.length === 0 && this.selectBrands.length === 0) return this.notebooksData
            else if (this.selectShops.length !== 0 && this.selectBrands.length === 0)
                return this.filterCard(this.notebooksData, this.selectShops, 'shop')
            else if (this.selectShops.length === 0 && this.selectBrands.length !== 0)
                return this.filterCard(this.notebooksData, this.selectBrands, 'brand')
            else return this.filterDataProduct()
        },
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
.product {
    // .product__body
    &__body {
        display: flex;
        gap: 20px;
    }
    // .product__filter
    &__filter {
        flex: 0 0 20%;
        padding: 10px;
        border: 2px solid rgb(179, 176, 176);
    }
    // .product__list
    &__list {
        flex: 1 0 20%;
        padding: 10px;
        border: 2px solid rgb(179, 176, 176);
        justify-content: center;
    }
}
</style>
