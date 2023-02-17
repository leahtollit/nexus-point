<template>
		<!-- base card desktop layout -->
		<div v-if="value_car === false && desktop === true"  :class="'baseCard__card--desktop'" class="baseCard pos--rel">
			<div class="baseCard__imgHolder pos--rel">
				<img :src="image" class="baseCard__img pos--abs" alt="">
				<BaseTag class="baseCard__tag pos--abs baseTag"> {{ advert_classification }} </BaseTag>
					<div class="baseCard__tagHolder flex pos--abs">
						<BaseLabel v-for="(el, i) in tags" :key="el + i" class="baseCard__label"> {{ el }} </BaseLabel>
					</div>
			</div>
			<div class="baseCard__contentHolder flex flex--dir-c">
				<div class="baseCard__headerHolder flex justifyC--between alignI--center">
					<p class="baseCard__header fs--16 fw--400 lh--150 ff--sfPro"> {{ header }} </p>
					<button class="baseCard__favouriteBtn" @click.prevent="favouriteOption()">
						<IconStar class="baseCard__star"  :class="{
								'baseCard__star--isFavourite': this.isFavourite === true
							}" ref="star"/>
					</button>
				</div>
				<p class="baseCard__subheading fs--12 fc--grey ff--sfPro">{{ subheading }} </p>
				<!-- if car is discounted, display new price and the view btn -->
				<div v-if="is_discounted === true" class="baseCard__priceCalculation flex justifyC--between">
					<div class="baseCard__col flex flex--dir-c">
						<p class="baseCard__pricePerMonth ff--sfPro"> <span>{{ price_per_month }}</span> <span>/mo (PCP)</span></p>
						<div class="baseCard__priceHolder flex alignI--center">
							<p class="baseCard__newPrice fs--12 fw--400 fc--red ff--sfPro">{{ new_price }}</p>
							<p class="baseCard__price baseCard__price--discounted fs--12 fw--400 fc--grey ff--sfPro">{{ price }}</p>
							<button class="baseCard__calculator fs--12 fw--400 fc--purple ff--sfPro">{{ calculate_label }}</button>
						</div>
					</div>
					<button v-if="has_view_btn" class="baseCard__viewBtn flex alignI--center">
						<p class="baseCard__btnLabel fs--16 fw--600 fc--white ff--overpass">View</p>
					</button>
				</div>
				<!-- otherwise, just show the cars price -->
				<div v-else class="baseCard__priceCalculation flex flex--dir-c">
					<p class="baseCard__pricePerMonth ff--sfPro"> <span>{{ price_per_month }}</span> <span>/mo (PCP)</span></p>
					<div class="baseCard__priceHolder flex alignI--center">
						<p class="baseCard__price fs--12 fw--400 ff--sfPro">{{ price }}</p>
								<button class="baseCard__calculator fs--12 fw--400 fc--purple ff--sfPro"> {{ calculate_label }}</button>
					</div>
				</div>
			</div>
  	</div>
		<!-- value your car card - ideally i would build this as it's own component -->
		<div v-else-if="value_car === true" class="baseCard__value flex flex--dir-c justifyC--center">
			<p class="baseCard__valueHeader ff--overpass fs--24 fw--600 fc--black"> {{ header }} </p>
			<p class="baseCard__valueSubheading ff--sfPro fs--16 fw--400 fc--black"> {{ subheading }} </p>
			<form class="baseCard__valueForm">
				<div class="baseCard__valueRow flex flex--dir-c pos--rel">
					<label for="VRM" class="baseCard__valueLabel fs--12 fc--black fw--400 ff--sfPro pos--abs flex">
						VRM 
						<IconAstrix class="baseCard__caret" />
					</label>
					<input class="baseCard__valueInput fs--16 fc--black fw--400 fc--greyLightest" type="text" id="vrmValue" name="VRM" :placeholder="'Enter VRM'">
				</div>
				<div class="baseCard__valueRow flex flex--dir-c pos--rel">
					<label for="VRM" class="baseCard__valueLabel fs--12 fc--black fw--400 ff--sfPro pos--abs flex">
						Mileage
						<IconAstrix class="baseCard__caret" />
					</label>
					<input class="baseCard__valueInput fs--16 fc--black fw--400 fc--greyLightest"  type="text" id="mileage" name="mileage" :placeholder="'Enter mileage'">
				</div>
				<input class="baseCard__submitBtn fs--16 fw--600 fc--white ff--overpass" type="submit" value="Value my car"/>
			</form>
		</div>

		<!-- base card mobile layout -->
		<div v-else :class="'baseCard__card--mobile'" class="baseCard pos--rel">
			<SliderGallery :image_carousel="image_carousel"/>
			<div class="baseCard__contentHolder flex flex--dir-c">
				<div class="baseCard__headerHolder flex justifyC--between alignI--center">
					<p class="baseCard__header fs--16 fw--400 ff--sfPro"> {{ header }} </p>
					<div class="baseCard__tagContainer flex">
						<BaseTag class="baseCard__tag pos--abs baseTag"> {{ advert_classification }} </BaseTag>
						<button class="baseCard__favouriteBtn" @click.prevent="favouriteOption()">
							<IconStar class="baseCard__star"  :class="{
									'baseCard__star--isFavourite': this.isFavourite === true
								}" ref="star"/>
						</button>
					</div>
				</div>
				<p class="baseCard__subheading fs--12 fc--grey ff--sfPro">{{ subheading }} </p>
				<!-- if car is discounted, display new price and the view btn -->
				<div v-if="is_discounted === true" class="baseCard__cardDetails flex">
					<div class="baseCard__tags flex">
						<p v-for="(el, i) in tags" :key="el + i" class="baseCard__tag baseCard__tag--mobile fs--12 fw--400 fc--grey"> {{ el }} </p>
					</div>
					<div class="baseCard__priceCalculation flex justifyC--between">
						<div class="baseCard__col flex flex--dir-c">
							<p class="baseCard__pricePerMonth ff--sfPro"> <span>{{ price_per_month }}</span> <span>/mo (PCP)</span></p>
							<div class="baseCard__priceHolder flex alignI--center">
								<p class="baseCard__newPrice fs--12 fw--400 fc--red ff--sfPro">{{ new_price }}</p>
								<p class="baseCard__price baseCard__price--discounted fs--12 fw--400 fc--grey ff--sfPro">{{ price }}</p>
							</div>
						</div>
					</div>
				</div>
				<!-- otherwise, just show the cars price -->
				<div v-else class="baseCard__carDetails flex">
					<div class="baseCard__tags flex">
						<p v-for="(el, i) in tags" :key="el + i" class="baseCard__tag baseCard__tag--mobile fs--12 fw--400 fc--grey"> {{ el }} </p>
					</div>
					<div  class="baseCard__priceCalculation flex flex--dir-c">
						<p class="baseCard__pricePerMonth ff--sfPro"> <span>{{ price_per_month }}</span> <span>/mo (PCP)</span></p>
						<div class="baseCard__priceHolder flex alignI--center">
							<p class="baseCard__price fs--12 fw--400 ff--sfPro">{{ price }}</p>
						</div>
					</div>
				</div>
			</div>
		</div>
</template>

<script>
import IconStar from '~/assets/svgs/interface/star.svg?inline'
import IconAstrix from '~/assets/svgs/interface/astrix.svg?inline'


export default {
	name: 'BaseCard',
	components: {
		IconStar,
		IconAstrix
	},
	props: {
		image: {
			type: String,
			default: ''
		},
		header: {
			type: String,
			default: ''
		},
		is_discounted: {
			type: Boolean,
			default: false
		},
		new_price: {
			type: String,
			default: ''
		},
		subheading: {
			type: String,
			default: ''
		},
		advert_classification: {
			type: String,
			default: ''
		},
		has_view_btn: {
			type: Boolean,
			default: true
		},
		price_per_month: {
			type: String,
			default: ''
		},
		price: {
			type: String,
			default: ''
		},
		tags: {
			type: Array,
			default: () => []
		},
		image_carousel: {
			type: Array,
			default: () => []
		},
		calculate_label: {
			type: String,
			default: ''
		},
		label_one: {
			type: String,
			default: ''
		},
		placeholder_one: {
			type: String,
			default: ''
		},
		label_two: {
			type: String,
			default: ''
		},
		value_car: {
			type: Boolean,
			default: false
		}
	}, 
	data() {
		return {
			isFavourite: false,
			desktop: true
		}
	},
	methods: {
		favouriteOption() {
			this.isFavourite = !this.isFavourite;
		}
  },
	mounted() {
		window.addEventListener('resize', () => {
			if (window.innerWidth < 500) {
				this.desktop = false
			} 
		})
	}
}
</script>

<style lang="scss">
.baseCard {

	&__card {

		&--desktop {
			background: $white;
		}

		&--desktop, .baseCard__value {
			box-shadow: 0px 6px 25px rgba(0, 0, 0, 0.15);
			border-radius: 16px;
			width: calc(33.33% - 15px);
			margin: 0 15px 15px 0;
		}

		&--mobile {
			// display: none;
			width: 100%;
		}
	}

	&__value {
		background: #F6F7FB;
		border: 1px solid #D1D6E0;
		border-radius: 16px;
		padding: 30px;
		width: calc(33.33% - 15px);
		margin: 0 15px 15px 0;
	}

	&__valueHeader {
		text-align: center;
		margin-bottom: 10px;
		line-height: 24px;
	}

	&__valueSubheading {
		text-align: center;
		line-height: 24px;
		margin-bottom: 25px;
	}
		

	&:nth-child(3n + 3) {
		margin-right: 0;
	}


	&__imgHolder {
		width: 100%;
		padding-bottom: 77%;
		// height: 250px;
	}

	&__tag {
		top: 10px;
		left: 10px;
	}

	&__img {
		width: 100%;
		height: 100%;
		object-fit: cover;
		border-top-left-radius: 16px;
		border-top-right-radius: 16px;
	}

	&__contentHolder {
		padding: 10px 11px 10px 10px;
	}

	&__subheading {
		line-height: 18px;
		margin-bottom: 10px;
	}

	&__pricePerMonth {
		span {
			line-height: 24px;
			font-weight: 700;

			&:nth-child(2) {
				font-weight: 400;
        font-size: 12px;
        line-height: 18px;
			}
		}
	}

	&__newPrice {
		margin-right: 8px;
	}

	&__price {
		line-height: 18px;

		&--discounted {
			text-decoration: line-through;
		}
	}

	&__calculator {
		margin-left: 8px;
		line-height: 18px;
		background: none;
		border: none;
		padding: none;
	}

	&__tagHolder {
		bottom: 6px;
		left: 10px;
	}

	&__favouriteBtn {
		background: none;
		border: none;
	}

	&__star {
		stroke: $black;

		&:hover {
			cursor: pointer;
		}

		&--isFavourite {
			fill: $purple;
			stroke: $purple;
		}
	}

	&__viewBtn, &__submitBtn {
		background: $purple;
		padding: 6px 25px 7px;
		border: 1px solid $purple;
		border-radius: 16px;
		transition: background 0.3s ease;

		&:hover {
			cursor: pointer;
			background: $white;
			color: $purple;
			
			.baseCard__btnLabel {
				color: $purple;
			}
		}

		&__btnLabel, &__submitLabel {
			line-height: 27px;
			transition: color 0.3s ease;

		}
	}


	// value box 
	// ideally i'd make this it's own component however to save time I'm nesting it within the basecard component
	&__valueRow {
		margin-bottom: 15px;
	}

	&__valueForm, &__valueInput {
		width: 100%;
	}

	&__valueLabel {
		background: #F6F7FB;
		line-height: 18px;
		border-radius: 100px;
		padding: 0 6px;
		margin-left: 7px;
		top: -9px;
		height: 18px;
	}

	&__valueInput {
		background: #FFFFFF;
		border-radius: 16px;
		border: none;
		height: 50px;
		padding: 13px;

		&::placeholder {
			font-weight: 400;
			font-size: 16px;
			line-height: 24px;
			font-family: $sfPro;
		}
	}

	&__submitBtn {
		width: 100%;
		padding: 11px 0 12px;
		line-height: 27px;
	}

	&__caret {
		margin-left: 2px;
		margin-top: 4px;
	}

}

//----------------------------------------//
// 1400
@include breakpoint(xxl) {
  .baseCard {

		&__viewBtn {
			margin-top: 7px;
		}
	}
}

//----------------------------------------//
// 1080
@include breakpoint(xl) {
  .baseCard {
		width: calc(50% - 15px);
	  margin: 0 15px 15px 0;

		&__value {
			width: calc(50% - 15px);
			margin: 0 15px 15px 0;
		}

		&:nth-child(2n + 2) {
			margin-right: 0;
			width: 50%;
		}
	}
}

//----------------------------------------//
// 500
@include breakpoint(xs) {
  .baseCard {
		margin-right: 0;
		width: 100%;

		&__card {

			&--desktop {
				display: none;
			}

		}

		&__value {
			display: none;
			
		}

		&:nth-child(2n + 2) {
			width: 100%;
		}

		&__tag {
			position: relative;
			top: unset;
			left: unset;
			margin-right: 11px;

			&--mobile {
				line-height: 18px;
				position: relative;

				&:nth-child(1), &:nth-child(3) {
					&::after {
						position: absolute;
						content: '';
						background: #D1D6E0;
						width: 1px;
						height: 9px;
						right: -5px;
						top: 40%;
						transform: translateY(-50%);
					}
				}
			}
		}

		&__tags {
			width: calc(50% - 44.5px);
			margin-right: 44.5px;
		}

		&__priceCalculation {
			width: 50%;
		}

		&__imgHolder {
			width: 33.33%;
			height: 84px;
		}

		&__header {
			font-size: 14px;
			line-height: 21px;
			font-weight: 400;
		}

		&__subheading {
			font-size: 12px;
			line-height: 18px;
			font-weight: 400;
		}

		&__contentHolder {
			padding-top: 20px;
		}

	}
}
</style>
