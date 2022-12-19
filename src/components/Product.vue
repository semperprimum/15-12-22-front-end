<template>
  <div class="product">

    <h3>{{product.text}}
        <i @click="$emit('delete-product')" class="fas fa-times"></i>
    </h3>
    <p>Кол-во: {{product.qt}} шт.</p>
    <p>Дата принятия: {{product.date}}</p>
    <p>Цена за шт: {{product.price}} тг.</p>
    <p>Общая цена: {{product.totalPrice}} тг.</p>
  </div>
</template>

<script>
    export default {
        name: 'Product',
        props: {
            product: Object,
        },
        methods: {
            onDelete(id) {
                this.$emit('delete-product', id)
            },
        },
    }
</script>

<style scope>
.fas {
  color: red;
}
.product {
  background: #f4f4f4;
  margin: 5px;
  padding: 10px 20px;
  cursor: pointer;
}
.product h3 {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>