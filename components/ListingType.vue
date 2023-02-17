<template>
  	<section class="listingType pos--rel">
		<div class="listingType__container flex justifyC--between alignI--center">
			<div class="listingType__filterHolder flex alignI--center justifyC--start">
				<h4 class="listingType__heading fs--overpass fw--700 fs--18"><span>Showing</span> 399 cards</h4>
				<ul class="listingType__tagList flex">
          			<Button v-for="(filter, i) in filters" :key="filter + i" :class="[{'listingType__tag--isSelected': selectedLabel === i}, {'listingType__tag--isNew': newLabel === i}]" class="listingType__tag flex justifyC--start alignI--center pos--rel">
               			<p class="listingType__label fs--16 fw--400 fc--grey ff--sfPro">{{ filter.label }}</p>
					</Button>
        		</ul>
			</div>
			<div class="listingType__dropdownHolder">
				<button class="listingType__filter flex alignI--center" @click.prevent="toggleDropdown()">
					<input class="listingType__filterLabel fs--16 fw--400 fc--grey ff--sfPro" :placeholder="'Lowest Price'" :value="currentInput"/>
					<CaretIconDown class="listingType__caretDown"/>
				</button>
				<BaseDropdown :dropdownItems="dropdownItems" :class="{ 'baseDropdown--open': isDropdownOpen === true }"/>
			</div>
		</div>
	</section>
</template>
  
<script>
	import CaretIconDown from '~/assets/svgs/interface/caret-down.svg?inline'
  export default {
  name: 'ListingType',
	components: {
		CaretIconDown
	},
	data() {
		return {
			isDropdownOpen: false,
			selectedLabel: 0,
			currentInput:'',
			newLabel: 2,
			filters: [
				{
					label: 'All'
				},
				{
					label: 'Used'
				},
				{
					label: 'New'
				},
				{
					label: 'Offers'
				}
			],
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
			]
		}
	},
	methods: {
		toggleDropdown() {
      this.isDropdownOpen = !this.isDropdownOpen
    }
	}
}
</script>
  
<style lang="scss">
  .listingType {
		width: 100%;

		&__heading {
			margin-right: 30px;
			line-height: 24px;
		}

		&__tag {
			border: 1px solid #D1D6E0;
			background: none;
     	border-radius: 12px;
      padding: 3px 25px;
			margin-right: 10px;
			transition: background 0.3s ease, border 0.3s ease;

			&:nth-last-child(1) {
				margin-right: 0;
			}

      &--isSelected {
				background: $purple;
				border: 1px solid $purple;


				.listingType__label {
					color: $white;
				}
      }

			&:hover {
				cursor: pointer;
				background: $purple;
				border: 1px solid $purple;

				.listingType__label {
          color: $white;
        }		
			}


			&--isNew {
				background: none;
			  	border: 1px solid $black;

				.listingType__label {
					color: $black;
				}
				
      }

		}

		&__label {
			line-height: 24px;
			transition: color 0.3s ease;
		}

		&__filter {
			background: #F6F7FB;
			border-radius: 16px;
			border: none;
			padding: 13px;
			pointer-events: all;
			width: 100%;

			&:hover {
				cursor: pointer;
				.listingType__caretDown {
					transform: translateY(2px);
				}
			}
		}

		&__filterLabel {
			line-height: 24px;
			margin-right: 14px;
			background: none;
			border: none;
			padding: 0;
			width: 96px;

		}

		&__caretDown {
			transition: transform 0.3s ease;
		}

		&__tagList {
			padding: 0;
		}
  }

	//----------------------------------------//
	// 1080
	@include breakpoint(xl) {
		.listingType {

			&__heading {
				margin-right: 30px;
				span {
					display: none;
				}
			}

			&__tag {
				margin-right: 5px;
			}

			&__dropdownHolder {
				max-width: 150px;
			}
		}
	}

	//----------------------------------------//
	// 750
	@include breakpoint(m) {
		.listingType {
			&__tagList {
				display: none;
			}
		}
	}

	//----------------------------------------//
	// 500
	@include breakpoint(xs) {
		.listingType {
			&__tagList {
				display: none;
			}

			&__heading {
				font-weight: 400;
				font-size: 14px;
				line-height: 21px;
			}

			&__filter {
				background: none;
				padding: 0;
			}

			&__filterLabel {
				color: $black;
				font-size: 14px;
				line-height: 21px;
				max-width: 84px;
			}
		}
	}
</style>
  