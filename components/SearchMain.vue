<template>
    <section class="searchMain container pos--rel">
			<div class="searchMain__grid grid ">
			  <SearchSidebar class="searchMain__sidebar" />
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
		height: 100vh;
		margin: 42.5px 0 50px 0;

		&__grid {
	    column-gap: 50px;
		  width: 100%;
		  // grid-template-columns: auto;
		  grid-template-areas: 
			  "sidebar listing listing listing";
			height: 100%;
		}

			&__sidebar {
				grid-area: sidebar;
				max-width: 298px;
			}

			&__listings {
				grid-area: listing;
				width: 100%;
			}

	
		
    
  }
  </style>
  