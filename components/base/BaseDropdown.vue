<template>
  <div class="baseDropdown flex pos--abs z--3">
    <button
      v-for="(item, index) of dropdownItems"
      :key="item + index"
      class="baseDropdown__input pos--rel"
      @click.prevent="selectItem(item[0])">
      <p
        class="baseDropdown__selectionItemName fs--16 fc--grey fw--400 pos--rel ff--sfPro">{{ item.label }}</p>
    </button>
  </div>
</template>

<script>
export default {
  name: 'BaseDropdown',
  props: {
    dropdownItems: {
      type: Array,
      default: null
    }
  },
  data() {
    return {
      currentInput: '',
      filteredItems: this.dropdownItems,
      selectedItem: ''
    }
  },
  methods: {
    selectItem(item) {
      this.$emit('onSelect', item)
    },
  }
}
</script>

<style lang="scss">
.baseDropdown {
  top: 105%;
  box-shadow: 0px 3px 6px -3px rgba(116, 161, 228, 0.06);
  border: 1px solid hsla(212, 100%, 39%, 0.2);
  max-height: 215px;
  overflow-y: scroll;
	display: none;
	border-radius: 16px;

	&--open {
		display: block;
	}


  &::-webkit-scrollbar-thumb {
    background: #035191;
    border-radius: 8px;
  }

  &::-webkit-scrollbar-track {
    background: #a2c0d9;
    border-radius: 8px;
    width: 7px;
  }

  &__input {
    background: #F6F7FB;;
    width: 100%;
    border: none;
    border-bottom: 1px solid hsla(212, 100%, 39%, 0.2);
		padding: 13px;
		transition: background 0.3s;

    &:hover {
      background: #ecf2fc;
      cursor: pointer;
    }

    &:nth-last-child(1) {
      border-bottom: none;
    }
  }

  &__selectionItemName {
    text-align: left;
  }
}

//----------------------------------------//
// 600
@include breakpoint(s) {
  .baseDropdown {


    &__selectionItemName {
      font-size: 14px;
    }
  }
}
</style>
