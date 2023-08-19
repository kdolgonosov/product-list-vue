<template>
    <form @submit.prevent class="addForm">
        <h4 class="addForm__title">Добавление продукта</h4>
        <input
            v-model="product.title"
            class="addForm__input"
            type="text"
            placeholder="Наименование"
        />
        <button class="addForm__button" @click="addProduct" :disabled="!product.title">
            Добавить
        </button>
    </form>
</template>

<script>
export default {
    data() {
        return {
            product: {
                id: null,
                title: '',
                active: true,
            },
        };
    },
    methods: {
        addProduct() {
            this.product.id = Date.now();
            this.$emit('add', this.product);
            this.product = {
                title: '',
                active: true,
            };
        },
    },
};
</script>

<style scoped>
.addForm {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    height: 135px;
    margin-bottom: 30px;
    padding-top: 15px;
}
.addForm__title {
    font-size: 24px;
}
.addForm__input {
    padding: 10px;
}
.addForm__button {
    height: 35px;
    width: 300px;
    /* justify-self: flex-end; */
    align-self: end;
}
.addForm__button:hover {
    cursor: pointer;
}
</style>
