<template>
  <main class="theContent">
    <FinanceBanner />
    <SearchMain />
  </main>
</template>

<script>
import { transitions } from '~/mixins/transitions'

export default {
  name: 'PageHome',
  mixins: [
    transitions,
  ]
}
</script>
