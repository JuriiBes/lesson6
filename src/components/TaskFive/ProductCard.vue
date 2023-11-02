<template>
    <div class="card">
        <a :href="elementCard.href" class="card__img-link">
            <img :src="elementCard.img" alt="image product" class="card__img" />
        </a>
        <a :href="elementCard.href" class="card__title">{{ elementCard.title }}</a>
        <div class="card__price">{{ elementCard.price }} ₴</div>
    </div>
</template>

<script>
export default {
    name: 'ProductCard',
    props: {
        elementCard: {
            type: Object,
            default: () => ({}),
        },
    },
}
</script>

<style lang="scss" scoped>
.card {
    display: flex;
    flex-direction: column;
    row-gap: 25px;
    max-width: 250px;
    padding: 15px 8px 10px;
    border-radius: 5px;
    border: 1px solid rgb(179, 176, 176);

    &:hover {
        .card__img {
            transform: scale(1.02);
        }
    }
    // .card__img-link
    &__img-link {
        position: relative;
        width: 100%;
        padding-top: 85%;
        overflow: hidden;
        object-fit: cover;
    }
    // .card__img
    &__img {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        transition: 0.3s;
    }
    // .card__title
    &__title {
        color: rgb(46, 45, 45);
        text-decoration: none;
        max-height: 35px;
        overflow: hidden;
        transition: 0, 3s;
        &:hover {
            color: rgb(14, 181, 223);
        }
    }

    // .card__price
    &__price {
        font-size: 25px;
        color: red;
    }
}
</style>
