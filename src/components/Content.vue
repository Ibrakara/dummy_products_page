<template>
  <div class="content-page">
    <div v-if="pageName === 'Ürünlerim' && currentSubLink === 'Tüm Ürünlerim'">
      <div class="product-stats">
        <ProductFilter
          v-for="productFilter in productFilters"
          :key="productFilter"
          :filterTitle="productFilter.filterTitle"
          :filterCount="allProducts.length"
          @filterProducts="filterProducts"
          :class="{ active: currentFilter === productFilter.filterTitle }"
        />
      </div>
      <SearchContainer
        v-if="currentFilter === 'Tüm Ürünlerim'"
        @make-search="searchProducts"
      />
      <div class="product-table" v-if="currentFilter === 'Tüm Ürünlerim'">
        <ProductTable
          :allProducts="allProducts"
          :currentProducts="currentProducts"
          :currentFilter="currentFilter"
          :currentSubLink="currentSubLink"
        />
        <Pagination
          v-if="currentProducts.length > 0"
          @set-current-page-number="setCurrenPageNumber"
          :totalNumOfPages="totalNumOfPages"
          @click="setCurrentProducts"
          @increase-page-num="increasePageNumber"
          @decrease-page-num="decreasePageNumber"
          :currentPageNum="currentPageNumber"
        />
      </div>
    </div>

    <h1 class="no-content" v-if="pageName !== 'Ürünlerim'">No Content</h1>
    <h1 v-if="pageName === 'Ürünlerim' && currentSubLink !== 'Tüm Ürünlerim'">
      Other Product Related Pages
    </h1>
  </div>
</template>

<script>
import Pagination from "./Pagination.vue";
import ProductFilter from "./ProductFilter.vue";
import ProductTable from "./ProductTable.vue";
import SearchContainer from "./SearchContainer.vue";
export default {
  components: {
    ProductTable,
    ProductFilter,
    Pagination,
    SearchContainer,
  },
  props: {
    pageName: {
      type: String,
    },
    currentSubLink: {
      type: String,
    },
  },
  data() {
    return {
      allProducts: [],
      fetchedProducts: [],
      currentProducts: [],
      currentPageNumber: 1,
      numOfProductPerPage: 11,
      currentFilter: "",
      productFilters: [
        {
          filterTitle: "Tüm Ürünlerim",
          filterCount: "x",
        },
        { filterTitle: "Stoğu Bitenler", filterCount: "XXÜrün Sayısı" },
        { filterTitle: "Satıştaki Ürünler", filterCount: "XXÜrün Sayısı" },
        { filterTitle: "Değişiklik Bekleyenler", filterCount: "XXÜrün Sayısı" },
        { filterTitle: "Onay Bekleyenler", filterCount: "XXÜrün Sayısı" },
      ],
    };
  },
  methods: {
    async fetchProducts() {
      const res = await fetch(
        "https://raw.githubusercontent.com/BestBuyAPIs/open-data-set/master/products.json"
      );
      const data = await res.json();
      this.fetchedProducts = data.slice(0, 200);
      this.allProducts = data.slice(0, 200);
      this.setCurrentProducts();
      console.log(this.allProducts);
    },
    filterProducts(title) {
      this.currentFilter = title;
    },
    setCurrentProducts() {
      this.currentProducts = this.allProducts.slice(
        this.indexOfCurrentPageFirstProduct,
        this.indexOfCurrentPageLastProduct
      );
    },
    setCurrenPageNumber(pageNum) {
      this.currentPageNumber = pageNum;
    },
    increasePageNumber() {
      if (this.currentPageNumber < this.totalNumOfPages.length) {
        this.currentPageNumber++;
      }
    },
    decreasePageNumber() {
      if (this.currentPageNumber > 1) {
        this.currentPageNumber--;
      }
    },
    makeProductNameSearch(searchInput) {
      this.allProducts = this.allProducts.filter((product) => {
        return product.name.match(searchInput);
      });
    },
    makeProductBrandSearch(searchInput) {
      this.allProducts = this.allProducts.filter((product) => {
        return product.manufacturer.match(searchInput);
      });
    },
    makeProductCodeSearch(searchInput) {
      this.allProducts = this.allProducts.filter((product) => {
        return product.upc.match(searchInput);
      });
    },

    searchProducts({ searchText, searchLabel }) {
      this.allProducts = this.fetchedProducts;
      if (searchLabel === "Ürün Kodu ile Arama") {
        this.makeProductCodeSearch(searchText);
      } else if (searchLabel === "Marka Adı ile Arama") {
        this.makeProductBrandSearch(searchText);
      } else if (searchLabel === "Ürün Adı ile Arama") {
        this.makeProductNameSearch(searchText);
      }
      this.setCurrentProducts();
    },
  },
  created() {
    this.fetchProducts();
  },
  computed: {
    numOfAllProducts() {
      return this.allProducts.length;
    },
    indexOfCurrentPageLastProduct() {
      return this.currentPageNumber * this.numOfProductPerPage;
    },
    indexOfCurrentPageFirstProduct() {
      return this.indexOfCurrentPageLastProduct - this.numOfProductPerPage;
    },
    totalNumOfPages() {
      let pageNumArr = [];
      for (
        let index = 1;
        index <= Math.ceil(this.allProducts.length / this.numOfProductPerPage);
        index++
      ) {
        pageNumArr.push(index);
      }
      return pageNumArr;
    },
  },
};
</script>

<style scoped>
.content-page {
  display: flex;
  flex-direction: column;
  background-color: #f1f1f2;
  padding: 0 2rem 0 2rem;
  min-height: 80vh;
}
.product-table {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  align-items: center;
  min-height: 65vh;
}
.product-stats {
  display: flex;
  flex-direction: row;
  align-items: center;
  margin: 2rem 0 2rem 0;
  height: 3rem;
  border-radius: 10px;
  width: fit-content;
  background-color: #f1f1f2;
  overflow: hidden;
}
.no-content {
  font-size: 10rem;
}
</style>
