<template>
    <div class="financeBanner pos--rel">
   
    </div>
  </template>
  
  <script>
  export default {
    name: 'FinanceBanner'
  }
  </script>
  
  <style lang="scss">
  .financeBanner {
		background: var(--blueDark);
		height: 137px;
		border-radius: 0px 0px 0px 50px;
    
  }

//----------------------------------------//
// 960
@include breakpoint(xl) {
  .financeBanner {
		display: none;
	}
}
  </style>
  