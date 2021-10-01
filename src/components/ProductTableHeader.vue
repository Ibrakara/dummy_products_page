<template>
  <thead class="table-header-container">
    <tr>
      <th class="table-header-title">Ürün Adı</th>
      <th class="table-header-title">Barkod</th>
      <th class="table-header-title">Marka</th>
      <th class="table-header-title">Kategori</th>
      <th class="table-header-title">Görüntülenme Sayısı</th>
      <th class="table-header-title">Varyant Durumu</th>
      <th class="table-header-title">Fiyat</th>
      <th class="table-header-title">Maliyet</th>
      <th class="table-header-title">Stok</th>
      <th class="table-header-title">Kontrol</th>
      <th class="table-header-title">Değiştir</th>
    </tr>
  </thead>
</template>

<script>
export default {};
</script>

<style scoped>
.table-header-container {
  background-color: #f1f1f2;
  color: white;
}
td:first-child,
th:first-child {
  border-radius: 10px 0 0 0;
}
td:last-child,
th:last-child {
  border-radius: 0 10px 0 0;
}
th {
  background-color: #7f9af9;
  font-size: 10px;
  font-weight: bold;
  padding: 0 0.3rem 0 0.3rem;
  vertical-align: middle;
  height: 3rem;
  text-align: left;
  border-right: 1px solid #f1f1f2;
}
</style>
