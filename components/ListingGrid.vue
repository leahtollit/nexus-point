<template>
  <section class="listingGrid pos--rel">
		<div class="listingType__container flex justifyC--between alignI--center">
			<BaseCard v-for="(el, i) in cards" :key="el + i"
        :image="el.image"
        :header="el.header"  
				:subheading="el.subheading"
				:advert_classification="el.advert_classification"
				:price="el.price"
				:price_per_month="el.price_per_month"
				:tags="el.tags"
				class="listingType__card"/>

			</div>
		</section>
  </template>
  
  <script>
  export default {
    name: 'ListingGrid',
		data() {
			return {
				cards: [
          {
            header: '2014 (64) Mercedes-Benz',
						subheading: 'CLA 250e Coupe Shooting Break',
						price_per_month: '£550.90',
						price: '£23,300',
						advert_classification: 'Used',
						image: '/images/thumbnails/car-one.jpg',
						tags: [ '32k miles', 'Hybrid', 'Manual', 'SUV']
          },
					{
            header: '2014 (64) Mercedes-Benz',
						subheading: 'CLA 250e Coupe Shooting Break',
						price_per_month: '£550.90',
						price: '£23,300',
						advert_classification: 'Used',
						image: '/images/thumbnails/car-one.jpg',
						tags: [ '32k miles', 'Hybrid', 'Manual', 'SUV']
          },
					{
            header: '2014 (64) Mercedes-Benz',
						subheading: 'CLA 250e Coupe Shooting Break',
						price_per_month: '£550.90',
						price: '£23,300',
						advert_classification: 'Used',
						image: '/images/thumbnails/car-one.jpg',
						tags: [ '32k miles', 'Hybrid', 'Manual', 'SUV']
          },
					{
            header: '2014 (64) Mercedes-Benz',
						subheading: 'CLA 250e Coupe Shooting Break',
						price_per_month: '£550.90',
						price: '£23,300',
						advert_classification: 'Used',
						image: '/images/thumbnails/car-one.jpg',
						tags: [ '32k miles', 'Hybrid', 'Manual', 'SUV']
          },
					{
            header: '2014 (64) Mercedes-Benz',
						subheading: 'CLA 250e Coupe Shooting Break',
						price_per_month: '£550.90',
						price: '£23,300',
						advert_classification: 'Used',
						image: '/images/thumbnails/car-one.jpg',
						tags: [ '32k miles', 'Hybrid', 'Manual', 'SUV']
          },
					{
            header: '2014 (64) Mercedes-Benz',
						subheading: 'CLA 250e Coupe Shooting Break',
						price_per_month: '£550.90',
						price: '£23,300',
						advert_classification: 'Used',
						image: '/images/thumbnails/car-one.jpg',
						tags: [ '32k miles', 'Hybrid', 'Manual', 'SUV']
          },
					{
            header: '2014 (64) Mercedes-Benz',
						subheading: 'CLA 250e Coupe Shooting Break',
						price_per_month: '£550.90',
						price: '£23,300',
						advert_classification: 'Used',
						image: '/images/thumbnails/car-one.jpg',
						tags: [ '32k miles', 'Hybrid', 'Manual', 'SUV']
          },
					{
            header: '2014 (64) Mercedes-Benz',
						subheading: 'CLA 250e Coupe Shooting Break',
						price_per_month: '£550.90',
						price: '£23,300',
						advert_classification: 'Used',
						image: '/images/thumbnails/car-one.jpg',
						tags: [ '32k miles', 'Hybrid', 'Manual', 'SUV']
          },
					{
            header: '2014 (64) Mercedes-Benz',
						subheading: 'CLA 250e Coupe Shooting Break',
						price_per_month: '£550.90',
						price: '£23,300',
						advert_classification: 'Used',
						image: '/images/thumbnails/car-one.jpg',
						tags: [ '32k miles', 'Hybrid', 'Manual', 'SUV']
          },
					{
            header: '2014 (64) Mercedes-Benz',
						subheading: 'CLA 250e Coupe Shooting Break',
						price_per_month: '£550.90',
						price: '£23,300',
						advert_classification: 'Used',
						image: '/images/thumbnails/car-one.jpg',
						tags: [ '32k miles', 'Hybrid', 'Manual', 'SUV']
          },
					{
            header: '2014 (64) Mercedes-Benz',
						subheading: 'CLA 250e Coupe Shooting Break',
						price_per_month: '£550.90',
						price: '£23,300',
						advert_classification: 'Used',
						image: '/images/thumbnails/car-one.jpg',
						tags: [ '32k miles', 'Hybrid', 'Manual', 'SUV']
          },
					{
            header: '2014 (64) Mercedes-Benz',
						subheading: 'CLA 250e Coupe Shooting Break',
						price_per_month: '£550.90',
						price: '£23,300',
						advert_classification: 'Used',
						image: '/images/thumbnails/car-one.jpg',
						tags: [ '32k miles', 'Hybrid', 'Manual', 'SUV']
          }
			  ]
			}
		},
    
  }
  </script>
  
  <style lang="scss">
  .listingGrid {
		width: 100%;
		margin: 30px 0 43px;

		
  }

	//----------------------------------------//
// 500
@include breakpoint(xs) {
  .listingGrid {
		&__tagList {
			display: none;
		}
	}
}
  </style>
  