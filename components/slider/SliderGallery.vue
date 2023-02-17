<template>
    <div class="sliderGallery pos--rel">
      <div ref="slider" class="sliderGallery__slider keen-slider flex pos--rel">
        <div v-for="(el, i) in image_carousel" :key="el + i" class="sliderGallery__slide keen-slider__slide pos--rel grid placeI--center">
          <img class="sliderGallery__img pos--abs" :src="el.image">
        </div>
      </div>
    </div>
  </template>
  
  <script>
  // https://keen-slider.io/docs
  import KeenSlider from 'keen-slider'
  import 'keen-slider/keen-slider.min.css'
  
  export default {
    name: 'SliderGallery',
    props: {
      image_carousel: {
        type: Array,
        default: () => []
		  },
    },
    data() {
      return {
        current: 0,
        slider: null
      }
    },
    mounted() {
      this.slider = new KeenSlider(this.$refs.slider, {
        selector: '.sliderGallery__slide',
        initial: this.current,
        slideChanged: (s) => {
          this.current = s.track.details.rel
        },
        slides: {
          spacing: 5,
					perView: 3,
        },
        loop: true,
        breakpoints: {
					'(max-width: 400px)': {
          	slides: {
							spacing: 5,
							perView: 3
          	}
					},
        }
      })
    },
    destroy() {
      if (this.slider) this.slider.destroy()
    }
  }
  </script>
  
<style lang="scss">
  .sliderGallery {
    width: 100%;
    overflow: visible;
    height: 84px;
    
    &__slider {
      flex-wrap: nowrap;
      align-content: flex-start;
      overflow: hidden;
      -webkit-user-select: none;
      -moz-user-select: none;
      -ms-user-select: none;
      user-select: none;
      -webkit-touch-callout: none;
      -khtml-user-select: none;
      touch-action: pan-y;
      -webkit-tap-highlight-color: transparent;
      width: 100%;
      height: 100%;
    }
  
    &__slide {
      overflow: hidden;
      width: 100%;
      height: 84px;
      border-radius: 16px;
    }

    &__img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      border-radius: 16px;
    }
  
  }
</style>
  