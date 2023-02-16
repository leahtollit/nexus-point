<template>
	<div class="baseCard pos--rel">

    <div class="baseCard__imgHolder pos--rel"> 
			<img :src="image" class="baseCard__img pos--abs" alt="">
			<BaseTag class="baseCard__tag pos--abs baseTag"> {{ advert_classification }} </BaseTag>
			  <div class="baseCard__tagHolder flex pos--abs">
				  <BaseLabel v-for="(el, i) in tags" :key="el + i" class="baseCard__label"> {{ el }} </BaseLabel>
			  </div>
		</div> 

		<div class="baseCard__contentHolder flex flex--dir-c">
			<div class="baseCard__headerHolder flex justifyC--between alignI--center">
			  <p class="baseCard__header fs--16 fw--400 lh--150"> {{ header }} </p>
				<button class="baseCard__favouriteBtn" @click.prevent="favouriteOption()">
				  <IconStar class="baseCard__star"  :class="{
              'baseCard__star--isFavourite': this.isFavourite === true
            }" ref="star"/>
				</button>
			</div>
			<p class="baseCard__subheading fs--12 fc--grey">{{ subheading }} </p>
			<!-- if car is discounted, display new price and the view btn -->
			<div v-if="is_discounted === true" class="baseCard__priceCalculation flex justifyC--between">
				<div class="baseCard__col flex flex--dir-c">
					<p class="baseCard__pricePerMonth"> <span>{{ price_per_month }}</span> <span>/mo (PCP)</span></p>
					<div class="baseCard__priceHolder flex alignI--center">
						<p class="baseCard__newPrice fs--12 fw--400 fc--red">{{ new_price }}</p>
						<p class="baseCard__price baseCard__price--discounted fs--12 fw--400 fc--grey">{{ price }}</p>
						<button class="baseCard__calculator fs--12 fw--400 fc--purple">{{ calculate_label }}</button>
					</div>
				</div>
				<button v-if="has_view_btn" class="baseCard__viewBtn">
					<p class="baseCard__btnLabel fs--16 fw--600 fc--white">View</p>
				</button>

			</div>
			<!-- otherwise, just show the cars price -->
			<div v-else class="baseCard__priceCalculation flex flex--dir-c">
				<p class="baseCard__pricePerMonth"> <span>{{ price_per_month }}</span> <span>/mo (PCP)</span></p>
				<div class="baseCard__priceHolder flex alignI--center">
					<p class="baseCard__price fs--12 fw--400">{{ price }}</p>
							<button class="baseCard__calculator fs--12 fw--400 fc--purple"> {{ calculate_label }}</button>
				</div>
			</div>
		</div>
		
	</div>
</template>

<script>
import IconStar from '~/assets/svgs/interface/star.svg?inline'

export default {
	name: 'BaseCard',
	components: {
		IconStar 
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
		calculate_label: {
			type: String,
			default: ''
		}
	},
	data() {
		return {
			isFavourite: false
		}
	},
	methods: {
		favouriteOption() {
			this.isFavourite = !this.isFavourite;
		}
  },
}
</script>

<style lang="scss">
.baseCard {
	background: $white;
  box-shadow: 0px 6px 25px rgba(0, 0, 0, 0.15);
  border-radius: 16px;
	width: calc(33.33% - 15px);
	margin: 0 15px 15px 0;

	&:nth-child(3n + 3) {
		margin-right: 0;
	}


	&__imgHolder {
		width: 100%;
		padding-bottom: 66%;
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
	}

	&__tagHolder {
		bottom: 11px;
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

	&__viewBtn {
		background: $purple;
		padding: 6px 25px 7px;
		border: 1px solid $purple;
		border-radius: 16px;
		transition: background 0.3s ease;

		&:hover {
			cursor: pointer;
			background: $white;
			
			.baseCard__btnLabel {
				color: $purple;
			}
		}

		&__btnLabel {
			line-height: 27px;
			transition: color 0.3s ease;

		}
	}
}

//----------------------------------------//
// 960
@include breakpoint(l) {
  .baseCard {
		width: calc(50% - 15px);
	  margin: 0 15px 15px 0;

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
		width: 100%;
	  margin: 0 0 15px 0;

		&:nth-child(2n + 2) {
			width: 100%;
		}
	}
}
</style>
