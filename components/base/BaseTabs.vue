<template>
  <div class="baseTabs">
    <button
      v-for="(el, i) in items"
      :key="el + i"
      :class="{ active: activeTab === i }"
      class="baseTabs__tab buttonReset"
      @click="changeTab(i)">
      <p class="baseTabs__label">{{ el }}</p>
    </button>
  </div>
</template>

<script>
export default {
  name: 'BaseTabs',
  props: {
    active: {
      type: Number,
      default: 0
    },
    items: {
      type: Array,
      default: null
    }
  },
  data() {
    return {
      activeTab: this.active
    }
  },
  methods: {
    changeTab(index) {
      this.activeTab = index

      this.$emit('onTabChange', i)
    }
  }
}
</script>

<style lang="scss">
.baseTabs {
  &__tab {
    padding: 12px 24px 12px;
    margin-right: 4px;

    &.active {
      background: $white;
      border-bottom: 2px solid $black;
      padding-bottom: 10px;
    }
  }
}
</style>
