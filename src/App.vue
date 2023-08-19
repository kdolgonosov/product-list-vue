<template>
    <div class="app">
        <div class="page">
            <product-add-form @add="addProduct" />
            <product-list :products="products" @remove="removeProduct" />
        </div>
    </div>
</template>

<script>
import ProductAddForm from './components/ProductAddForm';
import ProductList from './components/ProductList';
export default {
    components: {
        ProductAddForm,
        ProductList,
    },
    data() {
        return {
            products: [
                // { id: 1, title: 'Картофель', active: true },
                // { id: 2, title: 'Мясо', active: true },
                // { id: 3, title: 'Морковь', active: true },
                // { id: 4, title: 'Лук', active: true },
            ],
        };
    },
    mounted() {
        if (localStorage.getItem('products')) {
            this.products = JSON.parse(localStorage.getItem('products'));
        }
    },
    methods: {
        addProduct(newProduct) {
            this.products.unshift(newProduct);
            this.saveProducts();
        },
        removeProduct(product) {
            // this.products = this.products;
            console.log('test');
            product.active = false;
            this.products.push(this.products.splice(this.products.indexOf(product), 1)[0]);
            this.saveProducts();
        },
        saveProducts() {
            localStorage.setItem('products', JSON.stringify(this.products));
        },
    },
};
</script>

<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
.app {
    background-color: #f3f9d2;
    min-height: 100vh;
}
.page {
    /* padding: 0 350px; */
    margin: 0 auto;
    max-width: 1280px;
}
</style>
