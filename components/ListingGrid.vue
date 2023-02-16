<template>
  <section class="listingGrid pos--rel">
		<div class="listingGrid__container flex justifyC--between alignI--center">
			<BaseCard v-for="(el, i) in pagedCards" :key="el + i"
        :image="el.image"
        :header="el.header"  
				:subheading="el.subheading"
				:advert_classification="el.advert_classification"
				:price="el.price"
				:price_per_month="el.price_per_month"
				:tags="el.tags"
				:is_discounted="el.is_discounted"
				:new_price="el.new_price"
				:has_view_btn="el.has_view_btn"
				:calculate_label="el.calculate_label"
				class="listingGrid__card"/>
			</div>
			<div class="listingGrid__nav flex alignI--center justifyC--between">
				<button class="listingGrid__backBtn fc--grey fs--16 fw--400" @click.prevent="scrollToElement('#listings')">Back to top</button>
				<div class="listingGrid__pageNav">
					<button @click="showLess()" class="listingGrid__pageNavItem listingGrid__pageNavItem--prev">
						<CaretIcon class="listingGrid__caret listingGrid__caret--left"/>
					</button>
					<button @click.prevent="changePage()" :class="{
              'listingGrid__pageNavItem--isSelected': this.isCurrentPage === true
            }" class="listingGrid__pageNavItem fs--16 fw--400">1</button>
					<button class="listingGrid__pageNavItem fs--16 fw--400">2</button>
					<button class="listingGrid__pageNavItem fs--16 fw--400">3</button>
					<button class="listingGrid__pageNavItem">
						<CaretIcon class="listingGrid__caret listingGrid__caret--right"/>
					</button>
					<button @click="showMore()" class="listingGrid__pageNavItem listingGrid__pageNavItem--next">
						<CaretIcon class="listingGrid__caret listingGrid__caret--right"/>
						<CaretIcon class="listingGrid__caret listingGrid__caret--right"/>
					</button>
				</div>
				<button class="listingGrid__filter flex alignI--center">
					<p class="listingGrid__filterLabel fs--16 fw--400 fc--grey">Lowest Price</p>
					<CaretIconDown class="listingGrid__caretDown"/>
				</button>

			</div>
		</section>
  </template>
  
  <script>
	import CaretIcon from '~/assets/svgs/interface/caret.svg?inline'
	import CaretIconDown from '~/assets/svgs/interface/caret-down.svg?inline'

  export default {
    name: 'ListingGrid',
		components: {
			CaretIcon,
			CaretIconDown
		},
		data() {
			return {
				selectedPage: 0,
				isCurrentPage: false,
				page: 1,
				perPage: 12,
				selectedLabels: [],
				cards: [
          {
            header: '2014 (64) Mercedes-Benz',
						subheading: 'CLA 250e Coupe Shooting Break',
						price_per_month: '£550.90',
						price: '£23,300',
						advert_classification: 'Used',
						image: '/images/thumbnails/car-one.jpg',
						calculate_label: 'calculate',
						tags: [ '32k miles', 'Hybrid', 'Manual', 'SUV']
          },
					{
            header: '2020 (20) Peugeot 208',
						subheading: '1.2 PureTech 100 GT-Line',
						price_per_month: '£550.90',
						price: '£23,300',
						advert_classification: 'New',
						image: '/images/thumbnails/car-two.jpg',
						calculate_label: 'calculate finance',
						tags: [ 'Petrol', 'Automatic', 'Hatchback']
          },
					{
            header: '2019 (19) Renault Zoe',
						subheading: 'i R135 Rapid Charge ZE50',
						price_per_month: '£550.90',
						price: '£23,300',
						is_discounted: true,
						has_view_btn: true,
						new_price: '£23,300',
						advert_classification: 'Used',
						image: '/images/thumbnails/car-three.jpg',
						calculate_label: 'calculate finance',
						tags: [ '325 miles', 'EV', 'Automatic', 'Hatchback']
          },
					{
            header: '2020 (20) Peugeot 208',
						subheading: '1.2 PureTech 100 GT-Line',
						price_per_month: '£550.90',
						price: '£23,300',
						advert_classification: 'New',
						image: '/images/thumbnails/car-two.jpg',
						calculate_label: 'calculate finance',
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
						calculate_label: 'calculate',
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
						calculate_label: 'calculate finance',
						tags: [ '325 miles', 'EV', 'Automatic', 'Hatchback']
          },
					{
            header: '2014 (64) Mercedes-Benz',
						subheading: 'CLA 250e Coupe Shooting Break',
						price_per_month: '£550.90',
						price: '£23,300',
						advert_classification: 'Used',
						image: '/images/thumbnails/car-one.jpg',
						calculate_label: 'calculate',
						tags: [ '32k miles', 'Hybrid', 'Manual', 'SUV']
          },
					{
            header: '2020 (20) Peugeot 208',
						subheading: '1.2 PureTech 100 GT-Line',
						price_per_month: '£550.90',
						price: '£23,300',
						advert_classification: 'New',
						image: '/images/thumbnails/car-two.jpg',
						calculate_label: 'calculate finance',
						tags: [ 'Petrol', 'Automatic', 'Hatchback']
          },
					{
            header: '2014 (64) Mercedes-Benz',
						subheading: 'CLA 250e Coupe Shooting Break',
						price_per_month: '£550.90',
						price: '£23,300',
						advert_classification: 'Used',
						image: '/images/thumbnails/car-one.jpg',
						calculate_label: 'calculate',
						tags: [ '32k miles', 'Hybrid', 'Manual', 'SUV']
          },
					{
            header: '2020 (20) Peugeot 208',
						subheading: '1.2 PureTech 100 GT-Line',
						price_per_month: '£550.90',
						price: '£23,300',
						advert_classification: 'New',
						image: '/images/thumbnails/car-two.jpg',
						calculate_label: 'calculate finance',
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
						calculate_label: 'calculate finance',
						tags: [ '325 miles', 'EV', 'Automatic', 'Hatchback']
          },
					{
            header: '2014 (64) Mercedes-Benz',
						subheading: 'CLA 250e Coupe Shooting Break',
						price_per_month: '£550.90',
						price: '£23,300',
						advert_classification: 'Used',
						image: '/images/thumbnails/car-one.jpg',
						calculate_label: 'calculate',
						tags: [ '32k miles', 'Hybrid', 'Manual', 'SUV']
          },
					{
            header: '2020 (20) Peugeot 208',
						subheading: '1.2 PureTech 100 GT-Line',
						price_per_month: '£550.90',
						price: '£23,300',
						advert_classification: 'New',
						image: '/images/thumbnails/car-two.jpg',
						calculate_label: 'calculate finance',
						tags: [ 'Petrol', 'Automatic', 'Hatchback']
          },
					{
            header: '2019 (19) Renault Zoe',
						subheading: 'i R135 Rapid Charge ZE50',
						price_per_month: '£550.90',
						price: '£23,300',
						is_discounted: true,
						has_view_btn: true,
						new_price: '£23,300',
						advert_classification: 'Used',
						image: '/images/thumbnails/car-three.jpg',
						calculate_label: 'calculate finance',
						tags: [ '325 miles', 'EV', 'Automatic', 'Hatchback']
          },
					{
            header: '2020 (20) Peugeot 208',
						subheading: '1.2 PureTech 100 GT-Line',
						price_per_month: '£550.90',
						price: '£23,300',
						advert_classification: 'New',
						image: '/images/thumbnails/car-two.jpg',
						calculate_label: 'calculate finance',
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
						calculate_label: 'calculate',
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
						calculate_label: 'calculate finance',
						tags: [ '325 miles', 'EV', 'Automatic', 'Hatchback']
          },
					{
            header: '2014 (64) Mercedes-Benz',
						subheading: 'CLA 250e Coupe Shooting Break',
						price_per_month: '£550.90',
						price: '£23,300',
						advert_classification: 'Used',
						image: '/images/thumbnails/car-one.jpg',
						calculate_label: 'calculate',
						tags: [ '32k miles', 'Hybrid', 'Manual', 'SUV']
          },
					{
            header: '2020 (20) Peugeot 208',
						subheading: '1.2 PureTech 100 GT-Line',
						price_per_month: '£550.90',
						price: '£23,300',
						advert_classification: 'New',
						image: '/images/thumbnails/car-two.jpg',
						calculate_label: 'calculate finance',
						tags: [ 'Petrol', 'Automatic', 'Hatchback']
          },
					{
            header: '2014 (64) Mercedes-Benz',
						subheading: 'CLA 250e Coupe Shooting Break',
						price_per_month: '£550.90',
						price: '£23,300',
						advert_classification: 'Used',
						image: '/images/thumbnails/car-one.jpg',
						calculate_label: 'calculate',
						tags: [ '32k miles', 'Hybrid', 'Manual', 'SUV']
          },
					{
            header: '2020 (20) Peugeot 208',
						subheading: '1.2 PureTech 100 GT-Line',
						price_per_month: '£550.90',
						price: '£23,300',
						advert_classification: 'New',
						image: '/images/thumbnails/car-two.jpg',
						calculate_label: 'calculate finance',
						tags: [ 'Petrol', 'Automatic', 'Hatchback']
          },
					{
            header: '2019 (19) Renault Zoe end',
						subheading: 'i R135 Rapid Charge ZE50',
						price_per_month: '£550.90',
						price: '£23,300',
						is_discounted: true,
						new_price: '£23,300',
						advert_classification: 'Used',
						image: '/images/thumbnails/car-three.jpg',
						calculate_label: 'calculate finance',
						tags: [ '325 miles', 'EV', 'Automatic', 'Hatchback']
          },
			  ]
			}
		},
		computed: {
			pagedCards() {
				return this.cards.slice(0, this.perPage * this.page)
			},
			maxPages() {
				return this.cards.length / this.perPages
			}
		},
		mounted() {
			window.addEventListener('scroll', () => {
				if (window.scrollY > 10) {
					this.collapsed = true
				} else {
					this.collapsed = false
				}
			})
    },
		methods: {
			// handles scroll to top btn 
			// finds element # 
			scrollToElement(element) {
				const offset = document.querySelector(element).offsetTop
				const headerHeight = document.querySelector('.globalHeader').clientHeight

				window.scrollTo({
					top: offset - headerHeight,
					behavior: 'smooth'
				})
			},
			changePage() {
				this.isCurrentPage = !this.isCurrentPage;
			},
			showMore() {
      	this.page++
    	},
			showLess() {
      	this.page--
    	}
		}
  }
  </script>
  
  <style lang="scss">
  .listingGrid {
		width: 100%;
		margin: 30px 0 43px;

		&__nav {
			margin-top: 30px;
		}

		&__pageNavItem {
			border: 1px solid #D1D6E0;
			background: none;
			border-radius: 8px;
			padding: 8px; 
			margin-right: 8px;

			&:nth-last-child(1) {
				margin-right: 0;
			}

			&--isSelected {
				background: $purple;
				border: 1px solid $purple;
				color: $white;
			}
		}

		&__caret {

			&--left {
				transform: scaleX(-1);
			}
		}

		&__backBtn {
			background: none;
			border: none;
			position: relative;
			line-height: 24px;
			padding: 0;

			&::after {
				position: absolute;
				content: '';
				width: 100%;
				height: 1px;
				background: $grey;
				left: 0;
				bottom: 0;
				z-index: -1;
				transform: scaleX(1);
				transition: transform 0.3s cubic-bezier(0.25, 0.1, 0.25, 1);
			}

			&:hover {
				cursor: pointer;

				&::after {
      		transform: scaleX(0);
    		}
			}
		}
		
		&__filter {
			background: #F6F7FB;
			border-radius: 16px;
			border: none;
			padding: 13px;
		}

		&__filterLabel {
			line-height: 24px;
			margin-right: 14px;
		}
		
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
  