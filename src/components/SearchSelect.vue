<template>
  <div class="search-select-container">
    <label class="search-select-label">{{ selectLabel }}</label>
    <select class="search-select">
      <option
        v-for="selectOption in selectOptions"
        :key="selectOption"
        :value="selectOption"
      >
        {{ selectOption }}
      </option>
    </select>
  </div>
</template>

<script>
export default {
  props: {
    selectOptions: {
      type: Array,
    },
    selectLabel: {
      type: String,
    },
  },
};
</script>

<style scoped>
.search-select-container {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  width: 12rem;
  height: 4rem;
  margin-left: 0.4rem;
}
.search-select-label {
  font-size: 12px;
  font-weight: bold;
  text-align: left;
  color: #1d1e32;
}
.search-select {
  width: 11rem;
  height: 2.3rem;
  border-radius: 4px;
  border: solid 1px #e3e3e5;
  background-color: #fff;
  color: #1d1e32;
  font-size: 12px;
  font-weight: normal;
  cursor: pointer;
}
.search-select:focus {
  outline: none;
  color: #1d1e32;
  font-size: 12px;
  font-weight: normal;
}
</style>
