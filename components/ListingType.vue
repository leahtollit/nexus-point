<template>
  <section class="listingType pos--rel">
		<div class="listingType__container flex justifyC--between alignI--center">
			<div class="listingType__filterHolder flex alignI--center justifyC--start">
				<h4 class="listingType__heading">Showing 399 cards</h4>
				<ul class="listingType__tagList flex">
          <Button
					  v-for="(filter, i) in filters" :key="filter + i"
							:class="[{
              'listingType__tag--isSelected': selectedLabel === i
          }, {
              'listingType__tag--isNew': newLabel === i
            }]"
						@onSelect="selectType"

              class="listingType__tag flex justifyC--start alignI--center pos--rel">
               <p class="listingType__label fs--24 fc--grey">{{ filter.label }}</p>
					</Button>
        </ul>
			</div>
			<button class="listingType__filter flex alignI--center">
				<p class="listingType__filterLabel fs--16 fw--400 fc--grey">Lowest Price</p>
				<CaretIconDown class="listingGrid__caretDown"/>
			</button>
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
				selectedLabel: 0,
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
			  ]
			}
		},
		methods: {
				selectType(filter) {
				this.selectedFilter = []
				filter.forEach((el) => {
					this.selectedFilter.push(el.slug)
				})
				this.$emit('onSelect', filter)
			},
	}
    
  }
  </script>
  
  <style lang="scss">
  .listingType {
		width: 100%;

		&__heading {
			margin-right: 30px;
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
		}

		&__filterLabel {
			line-height: 24px;
			margin-right: 14px;
		}
  }

	//----------------------------------------//
// 500
@include breakpoint(xs) {
  .listingType {
		&__tagList {
			display: none;
		}
	}
}
  </style>
  