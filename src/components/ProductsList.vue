<template>
    <div v-if="products.length > 0">
        <TransitionGroup name="products-list">
            <ProductItem
            v-for="product in products"
            :product="product"
            :key="product.id"
            @remove="$emit('remove', product)"
            />
        </TransitionGroup>
        
    </div>
    <h2 v-else style="color: red;">
        List of products is empty
    </h2>
</template>

<script>
import ProductItem from './ProductItem.vue';

export default {
    props: {
        products: {
            type: Array,
            required: true
        }
    },
    components: { ProductItem }
}
</script>

<style scoped>
    .products-list-item {
        display: inline-block;
        margin-right: 10px;
    }

    .products-list-enter-active,
    .post-list-leave-active {
        transition: all 0.4s ease;
    }

    .products-list-enter-from,
    .products-list-leave-to {
        opacity: 0;
        transform: translateX(130px);
    }

    .products-list-move {
        transition: transform 0.8s ease;
    }
</style>