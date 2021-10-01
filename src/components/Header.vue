<template>
  <header class="header">
    <h3>Şirket</h3>
    <nav class="nav-bar">
      <ul class="nav-links">
        <HeaderLink
          v-for="headerTitle in headerTitles"
          :key="headerTitle"
          :title="headerTitle"
          :class="{ active: activeSection === headerTitle }"
          @click="[navigatePage(headerTitle), toggleLinkActive(headerTitle)]"
        />
      </ul>
    </nav>
    <div class="user">
      <span class="icon">
        <i class="fas fa-bell"></i>
      </span>
      <span class="icon"><i class="fas fa-user-circle"></i> </span>
      <h4>Samsung A.Ş</h4>
      <span class="icon"><i class="fas fa-chevron-down"></i></span>
    </div>
  </header>
</template>

<script>
import HeaderLink from "./HeaderLink.vue";
export default {
  data() {
    return {
      activeSection: "",
    };
  },
  components: {
    HeaderLink,
  },
  props: {
    headerTitles: {
      type: Array,
    },
  },

  methods: {
    toggleLinkActive(pageName) {
      this.activeSection = pageName;
    },
    navigatePage(pageName) {
      this.$emit("choose-page", pageName);
    },
  },
  computed: {},
};
</script>

<style scoped>
.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 2rem 0 2rem;
  height: 4rem;
  box-shadow: 0 3px 6px 0 rgba(0, 0, 0, 0.16);
  background-color: #fff;
  margin-bottom: 1px;
}
.nav-links {
  display: flex;
  list-style: none;
  justify-items: center;
  justify-content: center;
  align-items: center;
}
h4 {
  font-size: 12px;
}
.user {
  width: 9rem;
  display: flex;
  justify-content: space-between;
  cursor: pointer;
}
.icon {
  color: #7f9af9;
}
</style>
