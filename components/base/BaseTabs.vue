<template>
  <div class="baseTabs">
      <button class="baseTabs__tab buttonReset" :class="{ active: activeTab === i }"  @click="changeTab(i)">
        <p class="baseTabs__label ff--sfPro fs--14 fc--grey fw--400"><slot/></p>
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
      tabs: {
        type: Array,
        default: null
      }
    },
    data() {
      return {
        activeTab: this.active,
      }
    },
    methods: {
      changeTab(i) {
        this.activeTab = i
  
        this.$emit('onTabChange', i)
      }
    }
  }
</script>
  
<style lang="scss">
  .baseTabs {
    &__tab {
      width: 100%;
      padding: 10px 0 10px 0;
      margin-right: 4px;
      border-bottom: 1px solid #D1D6E0;
  
      &.active {
        border-bottom: 3px solid $purple;
      }
    }

    &__label {
      line-height: 21px;
    }
  }
</style>
  