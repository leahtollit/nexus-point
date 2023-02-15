<template>
    <div class="baseTag pos--rel">
      <p class="baseTag__label fs--16 fw--600 fc--white"><slot /></p>
    </div>
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
    background: #3F3A50;
    border: 1px solid rgba(255, 255, 255, 0.2);
    backdrop-filter: blur(5px);
    border-radius: 8px; 
    padding: 1px 10px;


    &__label {
      line-height: 27px;
    }

  }
  </style>
  