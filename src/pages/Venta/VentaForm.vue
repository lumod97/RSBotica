<!-- eslint-disable vue/no-mutating-props -->
<template>
  <card>
    <h5 slot="header" class="title">Realizar Venta</h5>
    <div class="row">
      <div class="col-md-4 pr-md-1">
        <base-input label="Codigo" placeholder="Codigo" v-model="product.code" @keyup="obtenerProducto">
        </base-input>
      </div>
      <div class="col-md-8 pr-md-1">
        <base-input
          label="Producto"
          placeholder="Producto"
          v-model="product.description"
        >
        </base-input>
      </div>
    </div>
    <div class="row">
      <div class="col-md-3 pr-md-1">
        <base-input label="Precio" placeholder="Precio" v-model="product.price">
        </base-input>
      </div>
      <div class="col-md-3 pr-md-1">
        <base-input
          label="Vencimiento"
          v-model="product.expirationDate"
          placeholder="##-##-####"
        >
        </base-input>
      </div>
      <div class="col-md-3 pl-md-1">
        <base-input label="Stock" placeholder="##" v-model="product.stock">
        </base-input>
      </div>
      <div class="col-md-3 pl-md-1">
        <base-input
          label="Cantidad"
          v-model="product.quantity"
          placeholder="##"
        >
        </base-input>
      </div>
    </div>
    <!-- <div class="row">
      <div class="col-md-4 pl-md-1">
        <base-input label="Lote" v-model="product.lot" placeholder="Lote">
        </base-input>
      </div>
    </div> -->
    <!-- <div class="row">
      <div class="col-md-12">
        <base-input
          label="Address"
          v-model="product.address"
          placeholder="Home Address"
        >
        </base-input>
      </div>
    </div>
    <div class="row">
      <div class="col-md-4 pr-md-1">
        <base-input label="City" v-model="product.city" placeholder="City">
        </base-input>
      </div>
      <div class="col-md-4 px-md-1">
        <base-input
          label="Country"
          v-model="product.country"
          placeholder="Country"
        >
        </base-input>
      </div>
      <div class="col-md-4 pl-md-1">
        <base-input label="Postal Code" placeholder="ZIP Code"> </base-input>
      </div>
    </div>
    <div class="row">
      <div class="col-md-8">
        <base-input>
          <label>About Me</label>
          <textarea
            rows="4"
            cols="80"
            class="form-control"
            placeholder="Here can be your description"
            v-model="product.about"
          >
          </textarea>
        </base-input>
      </div>
    </div> -->
    <div class="d-flex w-100 justify-content-end mt-3">
      <base-button type="success" fill @click="agregarProducto">Enviar</base-button>
    </div>
  </card>
</template>
<script>
export default {
  props: {
    model: {
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
        actions: ""
      },
      productData: {
        imageRoute: '',
        description: '',
        lab: '',
        comment: ''
      },
      listProducts: []
    };
  },
  methods:{
    agregarProducto(){
      this.$emit('agregarProducto', this.product)
      this.$emit('obtenerDatosCardProducto', {})
      this.product = {}
      this.productData = {}
    },
    obtenerProducto(key){
    if(this.product.code.length > 0 && key.key == 'Enter'){
      this.productData.imageRoute = 'https://boticaportugal.com/cdn/shop/products/9342026347_345x@2x.png?v=1654017776'
      this.productData.description = this.product.description
      this.productData.comment = 'Para todo tipo de dolores de cualquier intensidad, esta vaina te la cura así no tenga cura'
      this.productData.lab = 'Portugal'
      this.$emit('obtenerDatosCardProducto', this.productData)
      console.log(this.productData)
    }
  }
  },
};
</script>
<style></style>
