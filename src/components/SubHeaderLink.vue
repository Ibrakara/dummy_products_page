<template>
  <li class="sub-header-link">
    {{ subHeaderLink }}
  </li>
</template>

<script>
export default {
  props: {
    subHeaderLink: {
      type: String,
    },
  },
};
</script>

<style scoped>
.sub-header-link {
  color: #8e8f99;
  font-size: 14px;
  padding: 1.7rem 0 1.7rem 0;
  margin-right: 2rem;
  cursor: pointer;
}
.active {
  border-bottom: 0.2rem solid #7f9af9;
  padding-bottom: 1.5rem;
  color: #7f9af9;
  font-weight: bold;
}
</style>
