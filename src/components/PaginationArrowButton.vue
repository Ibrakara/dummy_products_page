<template>
  <li>
    {{ arrowName }}
  </li>
</template>

<script>
export default {
  props: {
    arrowName: {
      type: String,
    },
  },
};
</script>

<style scoped>
li {
  display: inline;
  list-style: none;
  width: 3rem;
  height: 1rem;
  margin: 0 0.2rem 0 0;
  padding: 0.2rem 0.2rem 0.2rem 0.2rem;
  border-radius: 6px;
  border: solid 1px #7f9af9;
  background-color: #fff;
  cursor: pointer;
  font-size: 12px;
  text-align: center;
  user-select: none;
}
</style>
