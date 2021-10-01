<template>
  <li>{{ pageNum }}</li>
</template>

<script>
export default {
  props: {
    pageNum: {
      type: Number,
    },
  },
};
</script>

<style scoped>
li {
  display: inline;
  list-style: none;
  width: 1rem;
  height: 1rem;
  margin: 0 0.2rem 0 0;
  padding: 0.2rem 0.2rem 0.2rem 0.2rem;
  border-radius: 6px;
  border: solid 1px #7f9af9;
  background-color: #fff;
  cursor: pointer;
  font-size: 12px;
  font-weight: 600;
  color: #555665;
  text-align: center;
  user-select: none;
}
.active {
  background-color: #7f9af9;
  color: #fff;
}
</style>
