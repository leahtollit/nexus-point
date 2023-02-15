<template>
  <header class="globalHeader pos--rel z--max">
    <div class="globalHeader__container container">
  
    </div>
  </header>
</template>

<script>
export default {
  name: 'GlobalHeader'
}
</script>

<style lang="scss">
.globalHeader {
  height: 100px;
  background: var(--grey);
  
}

//----------------------------------------//
// 960
@include breakpoint(l) {
  .globalHeader {
		height: 80px;
	}
}

//----------------------------------------//
// 375
@include breakpoint(t) {
  .globalHeader {
		height: 60px;
	}
}
</style>
