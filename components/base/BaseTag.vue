<template>
    <button class="baseTag pos--rel ta--center buttonReset">
      <p class="baseTag__label fs--16 fw--400 fc--white"><slot /></p>
    </button>
  </template>
  
  <script>
  export default {
    name: 'BaseTag',
    props: {
      type: {
        type: String,
        default: 'btn',
        validator(value) {
          return ['btn', 'link'].includes(value) // The value must match one of these strings
        }
      },
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
  .baseTag {
    background: $purple;
    border-radius: 12px;
    padding: 3px 25px;

		&__label {
			line-height: 24px;
		}

    &--disabled {
      border: 1px solid #D1D6E0;

      .baseTag__label {
        color: $grey;
      }
    }
  }
  </style>
  