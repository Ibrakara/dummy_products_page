<template>
  <div class="search-input-container">
    <label class="search-label">{{ searchLabel }}</label>
    <input
      type="text"
      v-model="searchValue"
      @input="inputValue"
      class="search-box"
      :disabled="searchValue === '' && isOtherInputsDisabled"
    />
  </div>
</template>

<script>
export default {
  props: {
    searchLabel: {
      type: String,
    },
    isOtherInputsDisabled: {
      type: Boolean,
    },
    containerSearchValue: {
      type: String,
    },
  },
  data() {
    return {
      searchValue: "",
    };
  },
  methods: {
    inputValue() {
      this.$emit("input-value", {
        searchText: this.searchValue,
        searchLabel: this.searchLabel,
      });
    },
    clearInput() {
      this.searchValue = this.containerSearchValue;
    },
  },
  watch: {
    containerSearchValue: function () {
      if (this.containerSearchValue === "") {
        this.clearInput();
      }
    },
  },
};
</script>

<style scoped>
.search-input-container {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  width: 14rem;
  height: 4rem;
  margin-right: 0.4rem;
}
.search-label {
  font-size: 12px;
  font-weight: bold;
  text-align: left;
  color: #1d1e32;
}
.search-box {
  width: 12rem;
  height: 2rem;
  margin: 4px 0 0;
  border-radius: 4px;
  border: solid 1px #e3e3e5;
  background-color: #fff;
  color: #1d1e32;
  font-size: 10px;
  font-weight: normal;
}
.search-box:focus {
  outline: none;
  color: #1d1e32;
  font-size: 10px;
  font-weight: normal;
}
</style>
