<template>
  <ul>
    <PaginationArrowButton
      :arrowName="arrowStringArray[0]"
      @click="decreasePageNum"
    />
    <PaginationPageButton
      v-for="pageNum in totalNumOfPages"
      :key="pageNum"
      @click="setCurrentPageNumber(pageNum)"
      :pageNum="pageNum"
      :class="{ active: currentPageNum === pageNum }"
    />
    <PaginationArrowButton
      :arrowName="arrowStringArray[1]"
      @click="increasPageNumber"
    />
  </ul>
</template>

<script>
import PaginationPageButton from "./PaginationPageButton.vue";
import PaginationArrowButton from "./PaginationArrowButton.vue";
export default {
  components: {
    PaginationPageButton,
    PaginationArrowButton,
  },
  props: {
    totalNumOfPages: {
      type: Array,
    },
    currentPageNum: {
      type: Number,
    },
  },
  data() {
    return {
      arrowStringArray: ["Önceki", "Sonraki"],
    };
  },
  methods: {
    setCurrentPageNumber(pageNum) {
      this.$emit("set-current-page-number", pageNum);
    },
    increasPageNumber() {
      this.$emit("increase-page-num");
    },
    decreasePageNum() {
      this.$emit("decrease-page-num");
    },
  },
};
</script>

<style scoped>
ul {
  display: flex;
  margin: 20px 0 20px 0;
}
</style>
