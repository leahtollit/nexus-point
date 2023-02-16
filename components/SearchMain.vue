<template>
  <section class="searchMain container pos--rel">
		<div class="searchMain__grid grid ">
			<!-- sidebar on left with filters -->
			<SearchSidebar class="searchMain__sidebar" />
			<!-- main listing feed -->
			<ListingFeed class="searchMain__listings" />
		</div>
	</section>
</template>
  
<script>
  export default {
    name: 'searchMain'
  }
</script>
  
<style lang="scss">
  .searchMain {
		width: 100%;
		height: 100%;
		margin: 42.5px 0 50px 0;

		&__grid {
	    column-gap: 50px;
		  width: 100%;
		  grid-template-areas: 
			  "sidebar listing";
			height: 100%;
		}

		&__sidebar {
			grid-area: sidebar;
			width: 100%;
		}

		&__listings {
			grid-area: listing;
			width: 100%;
		}
  }

//----------------------------------------//
// 960
@include breakpoint(l) {
  .searchMain {

		&__grid {
	    column-gap: 0;
		  grid-template-areas: 
			  "listing";
		}

		&__sidebar {
			display: none;
		}
		
	}
}

//----------------------------------------//
// 500
@include breakpoint(xs) {
  .searchMain {
		margin-bottom: 30px;
	}
}
</style>
  