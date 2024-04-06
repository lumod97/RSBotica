<!-- eslint-disable vue/no-mutating-props -->
<template>
  <card class="w-100 overflow-auto">
    <h5 slot="header" class="title">Realizar Venta</h5>
    <base-table :columns="columns" ref="lists" :data="products">
      <template #price="{item}">
        <base-input v-model="item.price" class="w-auto">
        </base-input>
      </template>
      <template #quantity="{item}">
        <base-input v-model="item.quantity" class="w-auto">
        </base-input>
      </template>
      <template #actions="{ item }">
        <base-button type="primary" block @click="eliminarProducto(item.code)">
          +
        </base-button>
      </template>
    </base-table>
  </card>
</template>
<script>
export default {
  props: {
    products: {
      type: Object,
      default: () => {
        return {};
      },
    },
  },
  data() {
    return {
      product: {
        code: "",
        description: "",
        price: "",
        stock: "",
        expirationDate: "",
        quantity: "",
      },
      columns: [
        {
          key: "code",
          label: "Código",
        },
        {
          key: "description",
          label: "Producto",
        },
        {
          key: "price",
          label: "Precio",
        },
        {
          key: "expirationDate",
          label: "Vencimiento",
        },
        {
          key: "stock",
          label: "Stock",
        },
        {
          key: "quantity",
          label: "Cantidad",
        },
        {
          key: "actions",
          label: "Acciones",
        },
      ],
      items: [
        {
          code: "001",
          description: "PRODUCTO 1",
          price: "10.00",
          expiration: "2024-04-06",
          stock: "3",
          quantity: "2",
        },
        {
          code: "002",
          description: "PRODUCTO 2",
          price: "5.00",
          expiration: "2024-04-08",
          stock: "120",
          quantity: "50",
        },
      ],
    };
  },
  methods:{
    eliminarProducto(id){
      alert(id)
    }
  }
};
</script>
<style></style>
