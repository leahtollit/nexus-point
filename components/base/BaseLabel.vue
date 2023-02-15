<template>
	<div class="baseLabel pos--rel">
		<p class="baseLabel__label fs--12 fw--400 fc--white"><slot /></p>
	</div>
</template>

<script>
export default {
	name: 'BaseLabel',
	props: {
		link: {
			type: String,
			default: ''
		},
		external: {
			type: Boolean,
			default: false
		},
		parentLink: {
			type: Boolean,
			default: false
		},
		loading: {
			type: Boolean,
			default: false
		}
	}
}
</script>

<style lang="scss">
.baseLabel {
	background: #3F3A50;
  border: 1px solid rgba(255, 255, 255, 0.2);
  backdrop-filter: blur(5px);
	border-radius: 8px;
	padding: 1px 10px;
	margin-right: 5px;
	pointer-events: none;

	&:nth-last-child(1) {
		margin-right: 0;
	}


	&__label {
		line-height: 18px;
	}

}
</style>
