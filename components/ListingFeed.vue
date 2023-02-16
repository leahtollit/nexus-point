<template>
    <section class="listingFeed pos--rel" id="listings">
      <!-- filters above grid -->
			<ListingType />
      <!-- grid of cards -->
			<ListingGrid :selectedTherapies="selectedTherapies"/>
      <!-- representative section -->
      <RepresentativeContent />
		</Section>
  </template>
  
  <script>
  export default {
    name: 'listingFeed',
    data() {
      return {
        selectedTherapies: [],
      }
    }
  }
  </script>
  
  <style lang="scss">
  .listingFeed {
		width: 100%;
		height: 100%;
    
  }
  </style>
  