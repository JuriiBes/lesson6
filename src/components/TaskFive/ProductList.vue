<template>
    <div class="product__list">
        <product-card v-for="product in productFilterData" :key="product.id" :elementCard="product" />
    </div>
</template>

<script>
import ProductCard from '@/components/TaskFive/ProductCard.vue'
export default {
    name: 'ProductList',
    components: {
        ProductCard,
    },
    props: {
        productFilterData: {
            type: Array,
            default: () => [],
        },
    },
}
</script>

<style lang="scss" scoped>
.product__list {
    display: flex;
    flex-wrap: wrap;
    gap: 20px;
}
</style>
