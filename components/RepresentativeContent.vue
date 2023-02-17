<template>
  <section class="representativeContent pos--rel">
		<div class="representativeContent__container">
			<div class="representativeContent__body flex">
				<p class="representativeContent__copy fc--black fs--16 ff--sfPro fw--700"><span>Representative example:</span> <span>Borrowing £11,790.00 over 4 years with a representative APR of 7.9 %, an annual interest rate of 4.08 % (Fixed) and a deposit of £500.00, the amount payable would be £273.59 per month, with a total cost of credit of £1,843.32 and a total amount payable of £13,633.32.</span></p>
				<div class="representativeContent__btn flex alignI--center">
					<p class="representativeContent__btnLabel fc--grey fs--16 fw--400 ff--sfPro" ref="buttonLabel">Hide breakdown</p>
					<button class="representativeContent__dropdownBtn flex justifyC--center alignI--center">
						<CaretIconUp class="representativeContent__caret"/>
					</button>
				</div>
			</div>
			<div class="representativeContent__tabs">
				<ul class="representativeContent__tabList flex justifyC--between">
          <BaseTabs v-for="(tab, i) in tabs" :key="tab + i" class="representativeContent__tab flex pos--rel"> {{ tab.name }} </BaseTabs>
        </ul>
				<div class="representativeContent__tabContent flex">
					<ul class="representativeContent__tabList flex justifyC--between">
						<div
							v-for="(el, i) in personal_contract" :key="el + i"
								class="representativeContent__item flex pos--rel flex--dir-c justifyC--center alignI--center"> 
								<p class="representativeContent__heading fs--16 fw--400 fc--grey ff--sfPro"> {{ el.heading }}</p>
								<p class="representativeContent_value fs--18 fw--700 fc--black ff--overpass"> {{ el.value }}</p>
						</div>
          </ul>
				</div>
			</div>
		</div>
	</section>
</template>
  
<script>
	import CaretIconUp from '~/assets/svgs/interface/caret-up.svg?inline'
  export default {
    name: 'RepresentativeContent',
		components: {
			CaretIconUp
		},
		data() {
			return {
				tabs: [
					{
						name: 'Personal Contract Purchase'
					},
					{
						name: 'Hire Purchase'
					}
				],
				personal_contract: [
					{
						heading: '48 monthly payments',
						value: '£157.25'
					},
					{
						heading: 'Cash price',
						value: '£9,998.00'
					},
					{
						heading: 'Customer deposit',
						value: '£250.00'
					},
					{
						heading: 'Amount of credit',
						value: '£11,980.75'
					},
					{
						heading: 'APR',
						value: '7.9%'
					},
					{
						heading: 'Term',
						value: '48 months'
					},
					{
						heading: 'Total amount payable',
						value: '£12,163.72'
					},
					{
						heading: 'Rate of interest (fixed)',
						value: '4.08% PA'
					},
					{
						heading: 'Annual mileage',
						value: '8,000'
					},
					{
						heading: 'Optional final payment',
						value: '£3,888.04'
					}
				]
			}
		},
		mounted() {
			window.addEventListener('resize', () => {
				if (window.innerWidth <= 960) {
					this.$refs.buttonLabel.innerHTML = 'Show breakdown'
				} else {
					this.$refs.buttonLabel.innerHTML = 'Hide breakdown'
				}
			})
		}
  }
</script>
  
<style lang="scss">
  .representativeContent {

		&__container {
			border: 1px solid #D1D6E0;
			border-radius: 16px;
			padding: 15px;
			background: #F6F7FB;
		}

		&__copy {
			line-height: 24px;
			max-width: 781px;
			width: calc(100% - 234px);
			margin-right: 15px;
			font-family: "SF Pro Text, sans-serif";
			span {
				font-weight: 700;
				font-family: $sfPro;

				&:nth-last-child(1) {
					font-weight: 400;
					font-family: $sfPro;
				}
			}
		}

		&__btn {
			background: $white;
			border-radius: 16px;
			border: none;
			padding: 24px 24px 24px 13px;
			max-height: 72px;
		}

		&__btnLabel {
			line-height: 24px;
		}

		&__dropdownBtn {
			background: #D1D6E0;
			border-radius: 8px;
			width: 24px;
			height: 24px;
			border: none;
			margin-left: 31px;
		}

		&__tabList {
			padding: 0;
		}

		&__tabs {
			width: 100%;
			margin-top: 13px;
		}

		&__tab {
			width: 50%;
		}

		&__item {
			width: calc(20% - 15px);
			margin-bottom: 15px;
			background: white;
			border-radius: 16px;
			padding: 13.5px 11.9px;

			&:nth-child(n + 6) {
				margin-bottom: 0;
			}
		}

		&__heading {
			text-align: center;
			margin-bottom: 5px;
		}

		&__tabContent {
			margin: 15px 0 0;
		}


  }
	//----------------------------------------//
  // 1080
	@include breakpoint(xl) {
  .representativeContent {

		&__tabs {
			display: none;
		}

		&__body {
			flex-direction: column;
		}

		&__copy {
			width: 100%;
			margin-right: 0;
			margin-bottom: 15px;
			font-size: 14px;
			line-height: 21px;
		}

		&__btn {
			justify-content: space-between;
			padding: 12px 13px;
		}

		&__btnLabel {
			font-weight: 600;
		}

		&__caret {
			transform: rotate(180deg);
		}
		
	}
}
</style>
  