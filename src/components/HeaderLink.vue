<template>
  <li class="header-nav-list-item">
    {{ title }}
  </li>
</template>

<script>
export default {
  components: {},
  props: {
    title: {
      type: String,
    },
    subLinkTitles: {
      type: Array,
    },
  },
};
</script>

<style scoped>
.header-nav-list-item {
  padding: 1.7rem 1rem 1.7rem 1rem;
  font-size: 12px;
  color: #1d1e32;
  cursor: pointer;
  font-weight: normal;
}

.active {
  border-bottom: 0.2rem solid #0137f3;
  padding-bottom: 1.5rem;
  color: #0137f3;
  font-weight: bold;
}
</style>
