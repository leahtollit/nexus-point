<template>
  	<section class="listingGrid pos--rel">
		<div class="listingGrid__container flex justifyC--between alignI--center">
			<BaseCard v-for="(el, i) in pagedCards" :key="el + i"
        :image="el.image"
				:image_carousel="el.image_carousel"
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
				:label_one="el.label_one"
				:label_two="el.label_two"
				:placeholder_one="el.placeholder_one"
				:placeholder_two="el.placeholder_two"
				:value_car="el.value_car"
				class="listingGrid__card"/>
		</div>
		<div class="listingGrid__nav flex alignI--center justifyC--between">
			<button class="listingGrid__backBtn fc--grey fs--16 fw--400 ff--sfPro" @click.prevent="scrollToElement('#listings')">Back to top</button>
			<div class="listingGrid__pageNav flex">
				<button @click="showLess()" class="listingGrid__pageNavItem listingGrid__pageNavItem--prev">
					<CaretIcon class="listingGrid__caret listingGrid__caret--left"/>
				</button>
				<button @click.prevent="changePage()" :class="{'listingGrid__pageNavItem--isSelected': this.isCurrentPage === true}" class="listingGrid__pageNavItem fs--16 fw--400 ff--sfPro">1</button>
				<button class="listingGrid__pageNavItem fs--16 fw--400 ff--sfPro">2</button>
				<button class="listingGrid__pageNavItem fs--16 fw--400 ff--sfPro">3</button>
				<button class="listingGrid__pageNavItem">
					<CaretIcon class="listingGrid__caret listingGrid__caret--right"/>
				</button>
				<button @click="showMore()" class="listingGrid__pageNavItem listingGrid__pageNavItem--next">
					<CaretIcon class="listingGrid__caret listingGrid__caret--right"/>
					<CaretIcon class="listingGrid__caret listingGrid__caret--right"/>
				</button>
			</div>
			<div class="listingGrid__dropdownHolder pos--rel">
				<button class="listingGrid__filter flex alignI--center" @click.prevent="toggleDropdown()">
					<p class="listingGrid__filterLabel fs--16 fw--400 fc--grey ff--sfPro">Lowest Price</p>
					<CaretIconDown class="listingGrid__caretDown"/>
				</button>
				<BaseDropdown :dropdownItems="dropdownItems" :class="{ 'baseDropdown--open': isDropdownOpen === true }"/>
			</div>
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
				isDropdownOpen: false,
				dropdownItems: [
					{
						label: 'Lowest Price'
					},
					{
						label: 'Highest Price'
					},
					{
						label: 'Whats New'
					}
				],
				cards: [
					{
						header: '2014 (64) Mercedes-Benz',
						subheading: 'CLA 250e Coupe Shooting Break',
						price_per_month: '??550.90',
						price: '??23,300',
						advert_classification: 'Used',
						image_carousel: [ 
							{
								image: '/images/thumbnails/car-one.jpg'
							},
							{
								image: '/images/thumbnails/car-one.jpg'
							},
							{
								image: '/images/thumbnails/car-one.jpg'
							}
						],
						image: '/images/thumbnails/car-one.jpg',
						calculate_label: 'calculate',
						tags: [ '32k miles', 'Hybrid', 'Manual', 'SUV']
					},
					{
						header: '2020 (20) Peugeot 208',
						subheading: '1.2 PureTech 100 GT-Line',
						price_per_month: '??550.90',
						price: '??23,300',
						advert_classification: 'New',
						image: '/images/thumbnails/car-two.jpg',
						image_carousel: [ 
							{
								image: '/images/thumbnails/car-two.jpg'
							},
							{
								image: '/images/thumbnails/car-two.jpg'
							},
							{
								image: '/images/thumbnails/car-two.jpg'
							}
						],
						calculate_label: 'calculate finance',
						tags: [ 'Petrol', 'Automatic', 'Hatchback']
					},
					{
						header: '2019 (19) Renault Zoe',
						subheading: 'i R135 Rapid Charge ZE50',
						price_per_month: '??550.90',
						price: '??23,300',
						is_discounted: true,
						has_view_btn: true,
						new_price: '??23,300',
						advert_classification: 'Used',
						image: '/images/thumbnails/car-three.jpg',
						image_carousel: [ 
							{
								image: '/images/thumbnails/car-three.jpg'
							},
							{
								image: '/images/thumbnails/car-three.jpg'
							},
							{
								image: '/images/thumbnails/car-three.jpg'
							}
						],
						calculate_label: 'calculate finance',
						tags: [ '325 miles', 'EV', 'Automatic', 'Hatchback']
					},
					{
						header: '2020 (20) Peugeot 208',
						subheading: '1.2 PureTech 100 GT-Line',
						price_per_month: '??550.90',
						price: '??23,300',
						advert_classification: 'New',
						image: '/images/thumbnails/car-two.jpg',
						image_carousel: [ 
							{
								image: '/images/thumbnails/car-two.jpg'
							},
							{
								image: '/images/thumbnails/car-two.jpg'
							},
							{
								image: '/images/thumbnails/car-two.jpg'
							}
						],
						calculate_label: 'calculate finance',
						tags: [ 'Petrol', 'Automatic', 'Hatchback']
					},
					{
						header: 'Value your car',
						value_car: true,
						subheading: 'Find out the value of your car in just a few minutes.',
						label_one: 'VRM',
						placeholder_one: 'Enter VRM',
						label_two: 'Mileage',
						placeholder_two: 'Enter mileage',
						btn_label: 'Value my car',
						btn_link: '/'
					},
					{
						header: '2014 (64) Mercedes-Benz',
						subheading: 'CLA 250e Coupe Shooting Break',
						price_per_month: '??550.90',
						price: '??23,300',
						advert_classification: 'Used',
						image: '/images/thumbnails/car-one.jpg',
						image_carousel: [ 
							{
								image: '/images/thumbnails/car-one.jpg'
							},
							{
								image: '/images/thumbnails/car-one.jpg'
							},
							{
								image: '/images/thumbnails/car-one.jpg'
							}
						],
						calculate_label: 'calculate',
						tags: [ '32k miles', 'Hybrid', 'Manual', 'SUV']
					},
					{	
						header: '2019 (19) Renault Zoe',
						subheading: 'i R135 Rapid Charge ZE50',
						price_per_month: '??550.90',
						price: '??23,300',
						is_discounted: true,
						new_price: '??23,300',
						advert_classification: 'Used',
						image: '/images/thumbnails/car-three.jpg',
						image_carousel: [ 
							{
								image: '/images/thumbnails/car-three.jpg'
							},
							{
								image: '/images/thumbnails/car-three.jpg'
							},
							{
								image: '/images/thumbnails/car-three.jpg'
								}
						],
						calculate_label: 'calculate finance',
						tags: [ '325 miles', 'EV', 'Automatic', 'Hatchback']
					},
					{
						header: '2014 (64) Mercedes-Benz',
						subheading: 'CLA 250e Coupe Shooting Break',
						price_per_month: '??550.90',
						price: '??23,300',
						advert_classification: 'Used',
						image: '/images/thumbnails/car-one.jpg',
						image_carousel: [ 
							{
								image: '/images/thumbnails/car-one.jpg'
							},
							{
								image: '/images/thumbnails/car-one.jpg'
							},
							{
								image: '/images/thumbnails/car-one.jpg'
							}
						],
						calculate_label: 'calculate',
						tags: [ '32k miles', 'Hybrid', 'Manual', 'SUV']
					},
					{
						header: '2020 (20) Peugeot 208',
						subheading: '1.2 PureTech 100 GT-Line',
						price_per_month: '??550.90',
						price: '??23,300',
						advert_classification: 'New',
						image: '/images/thumbnails/car-two.jpg',
						image_carousel: [ 
							{
								image: '/images/thumbnails/car-two.jpg'
							},
							{
								image: '/images/thumbnails/car-two.jpg'
							},
							{
								image: '/images/thumbnails/car-two.jpg'
							}
						],
						calculate_label: 'calculate finance',
						tags: [ 'Petrol', 'Automatic', 'Hatchback']
					},
					{
						header: '2014 (64) Mercedes-Benz',
						subheading: 'CLA 250e Coupe Shooting Break',
						price_per_month: '??550.90',
						price: '??23,300',
						advert_classification: 'Used',
						image: '/images/thumbnails/car-one.jpg',
						image_carousel: [ 
							{
								image: '/images/thumbnails/car-one.jpg'
							},
							{
								image: '/images/thumbnails/car-one.jpg'
							},
							{
								image: '/images/thumbnails/car-one.jpg'
							}
						],
						calculate_label: 'calculate',
						tags: [ '32k miles', 'Hybrid', 'Manual', 'SUV']
					},
					{
						header: '2020 (20) Peugeot 208',
						subheading: '1.2 PureTech 100 GT-Line',
						price_per_month: '??550.90',
						price: '??23,300',
						advert_classification: 'New',
						image: '/images/thumbnails/car-two.jpg',
						image_carousel: [ 
							{
								image: '/images/thumbnails/car-two.jpg'
							},
							{
								image: '/images/thumbnails/car-two.jpg'
							},
							{
								image: '/images/thumbnails/car-two.jpg'
							}
						],
						calculate_label: 'calculate finance',
						tags: [ 'Petrol', 'Automatic', 'Hatchback']
					},
					{
						header: '2019 (19) Renault Zoe',
						subheading: 'i R135 Rapid Charge ZE50',
						price_per_month: '??550.90',
						price: '??23,300',
						is_discounted: true,
						new_price: '??23,300',
						advert_classification: 'Used',
						image: '/images/thumbnails/car-three.jpg',
						image_carousel: [ 
							{
								image: '/images/thumbnails/car-three.jpg'
							},
							{
								image: '/images/thumbnails/car-three.jpg'
							},
							{
								image: '/images/thumbnails/car-three.jpg'
							}
						],
						calculate_label: 'calculate finance',
						tags: [ '325 miles', 'EV', 'Automatic', 'Hatchback']
					},
					{
						header: '2014 (64) Mercedes-Benz',
						subheading: 'CLA 250e Coupe Shooting Break',
						price_per_month: '??550.90',
						price: '??23,300',
						advert_classification: 'Used',
						image: '/images/thumbnails/car-one.jpg',
						image_carousel: [ 
							{
								image: '/images/thumbnails/car-one.jpg'
							},
							{
								image: '/images/thumbnails/car-one.jpg'
							},
							{
								image: '/images/thumbnails/car-one.jpg'
							}
						],
						calculate_label: 'calculate',
						tags: [ '32k miles', 'Hybrid', 'Manual', 'SUV']
					},
					{
						header: '2020 (20) Peugeot 208',
						subheading: '1.2 PureTech 100 GT-Line',
						price_per_month: '??550.90',
						price: '??23,300',
						advert_classification: 'New',
						image: '/images/thumbnails/car-two.jpg',
						image_carousel: [ 
							{
								image: '/images/thumbnails/car-two.jpg'
							},
							{
								image: '/images/thumbnails/car-two.jpg'
							},
							{
								image: '/images/thumbnails/car-two.jpg'
							}
						],
						calculate_label: 'calculate finance',
						tags: [ 'Petrol', 'Automatic', 'Hatchback']
					},
					{
						header: '2019 (19) Renault Zoe',
						subheading: 'i R135 Rapid Charge ZE50',
						price_per_month: '??550.90',
						price: '??23,300',
						is_discounted: true,
						has_view_btn: true,
						new_price: '??23,300',
						advert_classification: 'Used',
						image: '/images/thumbnails/car-three.jpg',
						image_carousel: [ 
							{
								image: '/images/thumbnails/car-three.jpg'
							},
							{
								image: '/images/thumbnails/car-three.jpg'
							},
							{
								image: '/images/thumbnails/car-three.jpg'
							}
						],
						calculate_label: 'calculate finance',
						tags: [ '325 miles', 'EV', 'Automatic', 'Hatchback']
					},
					{
						header: '2020 (20) Peugeot 208',
						subheading: '1.2 PureTech 100 GT-Line',
						price_per_month: '??550.90',
						price: '??23,300',
						advert_classification: 'New',
						image: '/images/thumbnails/car-two.jpg',
						image_carousel: [ 
							{
								image: '/images/thumbnails/car-two.jpg'
							},
							{
								image: '/images/thumbnails/car-two.jpg'
							},
							{
								image: '/images/thumbnails/car-two.jpg'
							}
						],
						calculate_label: 'calculate finance',
						tags: [ 'Petrol', 'Automatic', 'Hatchback']
					},
					{
						header: 'EMPTY',
						subheading: '1.2 PureTech 100 GT-Line',
						price_per_month: '??550.90',
						price: '??23,300',
						advert_classification: 'New',
						image: '/images/thumbnails/car-two.jpg',
						image_carousel: [ 
							{
								image: '/images/thumbnails/car-two.jpg'
							},
							{
								image: '/images/thumbnails/car-two.jpg'
							},
							{
								image: '/images/thumbnails/car-two.jpg'
							}
						],
						tags: [ 'Petrol', 'Automatic', 'Hatchback']
					},
					{
						header: '2014 (64) Mercedes-Benz',
						subheading: 'CLA 250e Coupe Shooting Break',
						price_per_month: '??550.90',
						price: '??23,300',
						advert_classification: 'Used',
						image: '/images/thumbnails/car-one.jpg',
						image_carousel: [ 
							{
								image: '/images/thumbnails/car-one.jpg'
							},
							{
								image: '/images/thumbnails/car-one.jpg'
							},
							{
								image: '/images/thumbnails/car-one.jpg'
							}
						],
						calculate_label: 'calculate',
						tags: [ '32k miles', 'Hybrid', 'Manual', 'SUV']
					},
					{
						header: '2019 (19) Renault Zoe',
						subheading: 'i R135 Rapid Charge ZE50',
						price_per_month: '??550.90',
						price: '??23,300',
						is_discounted: true,
						new_price: '??23,300',
						advert_classification: 'Used',
						image: '/images/thumbnails/car-three.jpg',
						image_carousel: [ 
							{
								image: '/images/thumbnails/car-three.jpg'
							},
							{
								image: '/images/thumbnails/car-three.jpg'
							},
							{
								image: '/images/thumbnails/car-three.jpg'
							}
						],
						calculate_label: 'calculate finance',
						tags: [ '325 miles', 'EV', 'Automatic', 'Hatchback']
					},
					{
						header: '2014 (64) Mercedes-Benz',
						subheading: 'CLA 250e Coupe Shooting Break',
						price_per_month: '??550.90',
						price: '??23,300',
						advert_classification: 'Used',
						image: '/images/thumbnails/car-one.jpg',
						image_carousel: [ 
							{
								image: '/images/thumbnails/car-one.jpg'
							},
							{
								image: '/images/thumbnails/car-one.jpg'
							},
							{
								image: '/images/thumbnails/car-one.jpg'
							}
						],
						calculate_label: 'calculate',
						tags: [ '32k miles', 'Hybrid', 'Manual', 'SUV']
					},
					{
						header: '2020 (20) Peugeot 208',
						subheading: '1.2 PureTech 100 GT-Line',
						price_per_month: '??550.90',
						price: '??23,300',
						advert_classification: 'New',
						image: '/images/thumbnails/car-two.jpg',
						image_carousel: [ 
							{
								image: '/images/thumbnails/car-two.jpg'
							},
							{
								image: '/images/thumbnails/car-two.jpg'
							},
							{
								image: '/images/thumbnails/car-two.jpg'
							}
						],
						calculate_label: 'calculate finance',
						tags: [ 'Petrol', 'Automatic', 'Hatchback']
					},
					{
						header: '2014 (64) Mercedes-Benz',
						subheading: 'CLA 250e Coupe Shooting Break',
						price_per_month: '??550.90',
						price: '??23,300',
						advert_classification: 'Used',
						image: '/images/thumbnails/car-one.jpg',
						image_carousel: [ 
							{
								image: '/images/thumbnails/car-one.jpg'
							},
							{
								image: '/images/thumbnails/car-one.jpg'
							},
							{
								image: '/images/thumbnails/car-one.jpg'
							}
						],
						calculate_label: 'calculate',
						tags: [ '32k miles', 'Hybrid', 'Manual', 'SUV']
					},
					{
						header: '2020 (20) Peugeot 208',
						subheading: '1.2 PureTech 100 GT-Line',
						price_per_month: '??550.90',
						price: '??23,300',
						advert_classification: 'New',
						image: '/images/thumbnails/car-two.jpg',
						image_carousel: [ 
							{
								image: '/images/thumbnails/car-two.jpg'
							},
							{
								image: '/images/thumbnails/car-two.jpg'
							},
							{
								image: '/images/thumbnails/car-two.jpg'
							}
						],
						calculate_label: 'calculate finance',
						tags: [ 'Petrol', 'Automatic', 'Hatchback']
					},
					{
						header: '2019 (19) Renault Zoe end',
						subheading: 'i R135 Rapid Charge ZE50',
						price_per_month: '??550.90',
						price: '??23,300',
						is_discounted: true,
						new_price: '??23,300',
						advert_classification: 'Used',
						image: '/images/thumbnails/car-three.jpg',
						image_carousel: [ 
							{
								image: '/images/thumbnails/car-three.jpg'
							},
							{
								image: '/images/thumbnails/car-three.jpg'
							},
							{
								image: '/images/thumbnails/car-three.jpg'
							}
						],
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
			window.addEventListener('resize', () => {
				if (window.innerWidth <= 500) {
					this.perPage = 6
				} else {
					this.perPage = 12
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
			},
			// dropdown toggle
			toggleDropdown() {
				this.isDropdownOpen = !this.isDropdownOpen
    	}
		}
	}
</script>
  
  <style lang="scss">
  .listingGrid {
		width: 100%;
		margin: 30px 0 30px;

		&__container {
			align-items: stretch;
		}

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
			pointer-events: all;

			&:hover {
				cursor: pointer;
				.listingGrid__caretDown {
					transform: translateY(2px);
				}
			}
		}

		&__caretDown {
			transition: transform 0.3s ease;
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
		margin-top: 26px;

		&__tagList {
			display: none;
		}

		&__filter {
			display: none;
		}

		&__nav {
			flex-direction: column-reverse;
		}
		
		&__pageNav {
			width: 100%;
			margin-bottom: 30px;
		}

		&__pageNavItem {
			margin-right: 5px;
			width: 15%;
		}
	}
}
  </style>
  