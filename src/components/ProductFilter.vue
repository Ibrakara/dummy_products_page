<template>
  <div class="product-filter">
    <span class="title" @click="filterProducts(filterTitle)">{{
      filterTitle
    }}</span>
    <strong>{{
      filterTitle === "Tüm Ürünlerim" ? filterCount : "Ürün Sayısı"
    }}</strong>
  </div>
</template>

<script>
export default {
  props: {
    filterTitle: {
      type: String,
    },
    filterCount: {},
  },
  methods: {
    filterProducts(title) {
      this.$emit("filterProducts", title);
    },
  },
};
</script>

<style scoped>
.product-filter {
  display: flex;
  flex-direction: column;
  justify-content: center;
  padding: 0 1.5rem 0 1rem;
  background-color: #ffff;
  margin-right: 3px;
  height: 3rem;
  user-select: none;
}

.title {
  font-size: 12px;
  color: #8e8f99;
  margin: 2px;
  font-weight: bold;
  cursor: pointer;
}
div > strong {
  font-size: 14px;
  font-weight: 600;
}
.active > .title {
  color: white;
}
.active {
  background-color: #7f9af9;
  color: white;
}
</style>
