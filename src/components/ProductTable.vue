<template>
  <h1 v-if="currentFilter !== 'Tüm Ürünlerim'">Need Product Parameter</h1>
  <table
    v-if="currentFilter === 'Tüm Ürünlerim'"
    class="product-table-container"
  >
    <ProductTableHeader />
    <tbody>
      <ProductRow
        v-for="product in currentProducts"
        :key="product.sku"
        :productDetail="product"
      />
    </tbody>
  </table>
</template>

<script>
import ProductTableHeader from "./ProductTableHeader.vue";
import ProductRow from "./ProductRow.vue";
export default {
  components: {
    ProductTableHeader,
    ProductRow,
  },
  props: {
    allProducts: {
      type: Array,
    },
    currentFilter: {
      type: String,
    },
    currentSubLink: {
      type: String,
    },
    currentProducts: {
      type: Array,
    },
  },
};
</script>

<style scoped>
.product-table-container {
  min-width: 95vw;
}
</style>
