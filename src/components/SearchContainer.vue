<template>
  <div class="search-container">
    <SearchInput
      searchLabel="Ürün Kodu ile Arama"
      @input-value="inputValue"
      :isOtherInputsDisabled="isOtherInputsDisabled"
      :containerSearchValue="searchValue.searchText"
    />
    <SearchInput
      searchLabel="Marka Adı ile Arama"
      @input-value="inputValue"
      :isOtherInputsDisabled="isOtherInputsDisabled"
      :containerSearchValue="searchValue.searchText"
    />
    <SearchInput
      searchLabel="Ürün Adı ile Arama"
      @input-value="inputValue"
      :isOtherInputsDisabled="isOtherInputsDisabled"
      :containerSearchValue="searchValue.searchText"
    />
    <SearchButton
      buttonTitle="Ara"
      buttonType="search"
      @click="handleSearchButtonClick"
    />
    <SearchButton
      buttonTitle="Temizle"
      buttonType="clean"
      @click="handleSearchButtonClick"
    />
    <SearchSelect
      :selectOptions="['Eklenme Tarihi', 'Güncelleme Tarihi']"
      selectLabel="Sıralama"
    />
    <SearchSelect :selectOptions="['Excel Olarak İndir']" />
  </div>
</template>

<script>
import SearchInput from "./SearchInput.vue";
import SearchButton from "./SearchButton.vue";
import SearchSelect from "./SearchSelect.vue";
export default {
  components: {
    SearchInput,
    SearchButton,
    SearchSelect,
  },
  data() {
    return {
      searchValue: { searchText: "", searchLabel: "" },
    };
  },
  methods: {
    inputValue(item) {
      this.searchValue = item;
    },
    handleSearchButtonClick(e) {
      if (e.target.innerText === "Temizle") {
        this.clearInput();
      } else {
        this.makeSearch();
      }
    },
    makeSearch() {
      this.$emit("make-search", this.searchValue);
    },

    clearInput() {
      this.searchValue.searchText = "";
      this.searchValue.searchLabel = "";
      this.makeSearch();
    },
  },
  computed: {
    isOtherInputsDisabled() {
      return this.searchValue.searchText !== "";
    },
  },
};
</script>

<style scoped>
.search-container {
  display: flex;
  height: 4rem;
  min-width: 95vw;
  justify-content: space-between;
  align-items: flex-end;
  margin-bottom: 1rem;
}
</style>
