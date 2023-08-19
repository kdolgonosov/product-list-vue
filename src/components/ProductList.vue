<template>
    <ul v-if="products.length > 0" class="product-list">
        <li
            class="product"
            :class="{ product_notActive: !product.active }"
            v-for="product in products"
            :key="product.id"
        >
            <p class="product__name" :class="{ product__name_notActive: !product.active }">
                {{ product.title }}
            </p>
            <button
                class="product__delete-btn"
                v-if="product.active"
                @click="$emit('remove', product)"
            >
                Удалить
            </button>
        </li>
    </ul>
    <h2 v-else class="product-list-empty">Список пуст! Попробуйте добавить новый продукт</h2>
</template>

<script>
export default {
    props: {
        products: {
            type: Array,
            required: true,
        },
    },
};
</script>

<style scoped>
.product-list {
    list-style: none;
}
.product-list-empty {
    text-align: center;
    /* color: red; */
}
.product {
    padding: 10px;
    border: 2px solid #3d0b37;
    border-radius: 35px;
    background-color: #cbeaa6;
    display: flex;
    flex-direction: row;
    justify-content: space-between;
}
.product__delete-btn:hover {
    cursor: pointer;
}
.product_notActive {
    background-color: #fff;
}
.product__name_notActive {
    text-decoration: line-through;
}
</style>
