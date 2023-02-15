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
			<p class="baseCard__pricePerMonth"> <span>{{ price_per_month }}</span> <span>/mo (PCP)</span></p>
			<div class="baseCard__priceCalculation flex">
			  <p class="baseCard__price fs--12 fw--400">{{ price }}</p>
				<button class="baseCard__calculator fs--12 fw--400 fc--purple">calculate</button>
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
		subheading: {
			type: String,
			default: ''
		},
		advert_classification: {
			type: String,
			default: ''
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
		height: 250px;
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

	&__price {
		line-height: 18px;
	}

	&__calculator {
		margin-left: 8px;
		line-height: 18px;
		background: none;
		border: none;
	}

	&__tagHolder {
		width: 100%;
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
