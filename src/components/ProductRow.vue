<template>
  <tr class="product-row">
    <td>{{ productDetail.name }}</td>
    <td>{{ productDetail.upc }}</td>
    <td>{{ productDetail.manufacturer }}</td>
    <td>{{ productDetail.category[0].name }}</td>
    <td>1</td>
    <td>Var</td>
    <td>{{ productDetail.price }}</td>
    <td>{{ calculateCostFromPrice }}</td>
    <td>{{ calculateStockFromSKU }}</td>
    <td>İçerik Kontrol Edildi</td>
    <td>Düzenle</td>
  </tr>
</template>

<script>
export default {
  props: {
    productDetail: {
      type: Object,
    },
  },
  computed: {
    //Stok bilgisi olmadığı için SKU değerinden random stok oluşturuldu
    calculateCostFromPrice() {
      return Math.round(this.productDetail.price * 0.8);
    },
    calculateStockFromSKU() {
      return Math.round(this.productDetail.sku * Math.random() * 0.001);
    },
  },
};
</script>

<style scoped>
.product-row {
  font-size: 12px;
}
td {
  background-color: white;
  padding: 0 0.3rem 0 0.3rem;
  vertical-align: middle;
  height: 3rem;
  text-align: left;
  border-right: 1px solid #f1f1f2;
  border-bottom: 1px solid #f1f1f2;
  color: #1d1e32;
  min-width: 3rem;
  max-width: 15rem;
}
</style>
