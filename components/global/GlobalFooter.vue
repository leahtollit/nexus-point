<template>
  <footer class="globalFooter">
    <div class="globalFooter__main"></div>
    <div class="globalFooter__companyInfo"></div>

  </footer>
</template>

<script>
export default {
  name: 'GlobalFooter'
}
</script>

<style lang="scss">
.globalFooter {

  &__main {
    background: var(--blueDark);
    height: 396px;
    border-radius: 0px 50px 0px 0;
  }

  &__companyInfo {
    background: var(--grey);
    height: 199px;

  }

}
</style>

