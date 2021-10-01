<template>
  <div class="button" :class="buttonType">{{ buttonTitle }}</div>
</template>

<script>
export default {
  props: {
    buttonTitle: {
      type: String,
    },
    buttonType: {
      type: String,
    },
  },
};
</script>

<style scoped>
.button {
  width: 7rem;
  height: 2rem;
  margin-right: 0.4rem;
  opacity: 0.9;
  border-radius: 6px;
  color: white;
  display: flex;
  justify-content: center;
  align-items: center;
  cursor: pointer;
  user-select: none;
  padding: 1px 0;
  font-weight: 600;
  font-size: 12px;
}
.clean {
  background-color: #ff2508;
}
.search {
  background-color: #0137f3;
}
</style>
