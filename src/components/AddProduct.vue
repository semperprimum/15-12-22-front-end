<template>
  <form @submit="onSubmit" class="add-form">
    <div class="form-control">
      <label>Название Товара</label>
      <input type="text" v-model="text" name="text" placeholder="Добвить название товара" required />
    </div>
    <div class="form-control">
      <label>Количество</label>
      <input
        type="text"
        v-model="qt"
        name="qt"
        placeholder="Добавить количество"
        required
      />
    </div>
    <div class="form-control">
      <label>Дата</label>
      <input
        type="date"
        v-model="date"
        name="date"
        required
      />
    </div>
    <div class="form-control">
      <label>Цена</label>
      <input
        type="text"
        v-model="price"
        name="price"
        placeholder="Добавить цену за 1 шт."
        required
      />
    </div>
    <input type="submit" value="Добавить Продукт" class="btn btn-block" />
  </form>
</template>

<script>
    export default {
        name: 'AddProduct',
        data() {
            return {
                text: '',
                qt: '',
            }
        },
        methods: {
            onSubmit(e) {
                e.preventDefault()

                if(!this.text) {
                    alert('Пожалуйста добавьте товар')
                    return
                }

                const newProduct = {
                    id: Math.floor(Math.random() * 100000),
                    text: this.text,
                    qt: this.qt,
                    date: this.date,
                    price: this.price,
                    totalPrice: this.price * this.qt,
                }

                this.$emit('add-product', newProduct)

                this.text = ''
                this.qt = ''
                this.date = ''
                this.price = ''
            }
        }
    }
</script>

<style scoped>
.add-form {
  margin-bottom: 40px;
}
.form-control {
  margin: 20px 0;
}
.form-control label {
  display: block;
}
.form-control input {
  width: 100%;
  height: 40px;
  margin: 5px;
  padding: 3px 7px;
  font-size: 17px;
}
.form-control-check {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.form-control-check label {
  flex: 1;
}
.form-control-check input {
  flex: 2;
  height: 20px;
}
</style>