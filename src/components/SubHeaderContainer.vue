<template>
  <ul class="sub-header-nav" v-if="currentPage.length > 0">
    <SubHeaderLink
      v-for="currentSubHeaderLinkTitle in currentSubHeaderLinkTitles"
      :key="currentSubHeaderLinkTitle"
      :subHeaderLink="currentSubHeaderLinkTitle"
      :class="{ active: activeSubLink === currentSubHeaderLinkTitle }"
      @click="[toggleSubLinkActive($event), setCurrentSubLink()]"
    />
  </ul>
</template>

<script>
import SubHeaderLink from "./SubHeaderLink.vue";
export default {
  components: {
    SubHeaderLink,
  },
  props: {
    currentPage: {
      type: String,
    },
  },
  data() {
    return {
      activeSubLink: "",
      currentSubHeaderLinkTitles: [],
      subHeaderLinkTitle: {
        myProducts: [
          "Tüm Ürünlerim",
          "Tek Ürün Yükleme",
          "Toplu Ürün İşlemleri İptaller",
          "Katalogtan Ekleme",
          "Görsellerim",
        ],
        currentStatus: [
          "Lorem Ipsum1",
          "Lorem Ipsum2",
          "Lorem Ipsum3",
          "Lorem Ipsum4",
        ],
        orderManagement: ["Order1", "Order2", "Order3"],
        paymentAndBills: ["Ödeme", "Faturalar"],
        reports: ["Report1", "Reports2", "Reports3"],
        promotions: ["Promotion1", "Promotion2", "Promotion3"],
      },
    };
  },
  methods: {
    toggleSubLinkActive(e) {
      this.activeSubLink = e.target.childNodes[0].nodeValue;
    },
    transformCurrentPageName(name) {
      if (name === "Güncel Durum") {
        this.currentSubHeaderLinkTitles = this.subHeaderLinkTitle.currentStatus;
      } else if (name === "Ürünlerim") {
        this.currentSubHeaderLinkTitles = this.subHeaderLinkTitle.myProducts;
      } else if (name === "Sipariş Yönetimi") {
        this.currentSubHeaderLinkTitles =
          this.subHeaderLinkTitle.orderManagement;
      } else if (name === "Ödeme ve Faturalar") {
        this.currentSubHeaderLinkTitles =
          this.subHeaderLinkTitle.paymentAndBills;
      } else if (name === "Raporlar") {
        this.currentSubHeaderLinkTitles = this.subHeaderLinkTitle.reports;
      } else if (name === "Kampanya") {
        this.currentSubHeaderLinkTitles = this.subHeaderLinkTitle.promotions;
      }
    },
    setCurrentSubLink() {
      this.$emit("set-current-sub-link", this.activeSubLink);
    },
  },
  updated() {
    this.transformCurrentPageName(this.currentPage);
  },
};
</script>

<style scoped>
.sub-header-nav {
  display: flex;
  box-shadow: 0 3px 6px 0 rgba(0, 0, 0, 0.16);
  background-color: #fff;
  padding-left: 2rem;
  height: 4rem;
  justify-content: flex-start;
  align-items: center;
}
</style>
