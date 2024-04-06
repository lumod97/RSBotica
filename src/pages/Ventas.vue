<template>
  <div>
    <div class="row">
      <div class="col-md-8">
        <div class="row">
          <venta-form :model="model" @agregarProducto="agregarProducto" @obtenerDatosCardProducto="enviarDataCard"> </venta-form>
          <venta-table :products="listProducts" ref="listProductsTable">
          </venta-table>
        </div>
      </div>
      <div class="col-md-4">
        <product-card :productData="productCardData"></product-card>
      </div>
    </div>
    <!-- <div class="row">
      <venta-form :model="model"> </venta-form>
    </div> -->
  </div>
</template>
<script>
import VentaForm from "./Venta/VentaForm";
import VentaTable from "./Venta/VentaTable";
import ProductCard from "./Venta/ProductCard";
export default {
  components: {
    VentaForm,
    ProductCard,
    VentaTable
  },
  data() {
    return {
      model: {
        company: "Creative Code Inc.",
        email: "mike@email.com",
        username: "michael23",
        firstName: "Mike",
        lastName: "Andrew",
        address: "Bld Mihail Kogalniceanu, nr. 8 Bl 1, Sc 1, Ap 09",
        city: "Melbourne",
        country: "Australia",
        about:
          "Lamborghini Mercy, Your chick she so thirsty, I'm in that two seat Lambo.",
      },
      user: {
        fullName: "Mike Andrew",
        title: "Ceo/Co-Founder",
        description: `Do not be scared of the truth because we need to restart the human foundation in truth And I love you like Kanye loves Kanye I love Rick Owens’ bed design but the back is...`,
      },
      listProducts: [],
      productCardData: {},
    };
  },
  methods:{
    agregarProducto(producto){
      console.log(this.$refs.listProductsTable)
      this.listProducts.push(producto)
    },
    enviarDataCard(item){
      this.productCardData = item
    }
  }
};
</script>
<style></style>
