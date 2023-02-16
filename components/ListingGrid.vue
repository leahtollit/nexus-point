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
            header: '2020 (20) Peugeot 208',
						subheading: '1.2 PureTech 100 GT-Line',
						price_per_month: '£550.90',
						price: '£23,300',
						advert_classification: 'New',
						image: '/images/thumbnails/car-two.jpg',
						tags: [ 'Petrol', 'Automatic', 'Hatchback']
          },
					{
            header: '2019 (19) Renault Zoe',
						subheading: 'i R135 Rapid Charge ZE50',
						price_per_month: '£550.90',
						price: '£23,300',
						is_discounted: true,
						new_price: '£23,300',
						advert_classification: 'Used',
						image: '/images/thumbnails/car-three.jpg',
						tags: [ '325 miles', 'EV', 'Automatic', 'Hatchback']
          },
					{
            header: '2020 (20) Peugeot 208',
						subheading: '1.2 PureTech 100 GT-Line',
						price_per_month: '£550.90',
						price: '£23,300',
						advert_classification: 'New',
						image: '/images/thumbnails/car-two.jpg',
						tags: [ 'Petrol', 'Automatic', 'Hatchback']
          },
					{
            header: 'EMPTY',
						subheading: '1.2 PureTech 100 GT-Line',
						price_per_month: '£550.90',
						price: '£23,300',
						advert_classification: 'New',
						image: '/images/thumbnails/car-two.jpg',
						tags: [ 'Petrol', 'Automatic', 'Hatchback']
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
            header: '2019 (19) Renault Zoe',
						subheading: 'i R135 Rapid Charge ZE50',
						price_per_month: '£550.90',
						price: '£23,300',
						is_discounted: true,
						new_price: '£23,300',
						advert_classification: 'Used',
						image: '/images/thumbnails/car-three.jpg',
						tags: [ '325 miles', 'EV', 'Automatic', 'Hatchback']
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
            header: '2020 (20) Peugeot 208',
						subheading: '1.2 PureTech 100 GT-Line',
						price_per_month: '£550.90',
						price: '£23,300',
						advert_classification: 'New',
						image: '/images/thumbnails/car-two.jpg',
						tags: [ 'Petrol', 'Automatic', 'Hatchback']
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
            header: '2020 (20) Peugeot 208',
						subheading: '1.2 PureTech 100 GT-Line',
						price_per_month: '£550.90',
						price: '£23,300',
						advert_classification: 'New',
						image: '/images/thumbnails/car-two.jpg',
						tags: [ 'Petrol', 'Automatic', 'Hatchback']
          },
					{
            header: '2019 (19) Renault Zoe',
						subheading: 'i R135 Rapid Charge ZE50',
						price_per_month: '£550.90',
						price: '£23,300',
						is_discounted: true,
						new_price: '£23,300',
						advert_classification: 'Used',
						image: '/images/thumbnails/car-three.jpg',
						tags: [ '325 miles', 'EV', 'Automatic', 'Hatchback']
          },
				
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
  