<template>
  <div class="vue-dropdown relative inline-block text-left">
    <div v-on-clickaway="hide">
      <slot name="button">
        <button @click="toggle" @keydown.esc="hide" type="button" :class="textClasses">
          <slot name="button-content">
            <span v-html="text" />
            <svg class="-mr-1 ml-2 h-5 w-5" fill="currentColor" viewBox="0 0 20 20">
              <path fill-rule="evenodd" d="M5.293 7.293a1 1 0 011.414 0L10 10.586l3.293-3.293a1 1 0 111.414 1.414l-4 4a1 1 0 01-1.414 0l-4-4a1 1 0 010-1.414z" clip-rule="evenodd"/>
            </svg>
          </slot>
        </button>
      </slot>
    </div>

    <div v-show="show" :class="menuClasses">
      <div class="rounded-md bg-white shadow-xs">
        <div class="py-1">
          <slot />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  import { directive as onClickaway } from 'vue-clickaway2'

  export default {
    directives: {
      onClickaway
    },

    props: {
      text: {
        type: String,
        default: 'Options'
      },
      textClasses: {
        type: String,
        default: 'inline-flex justify-between w-full rounded-md border border-gray-300 px-4 py-2 bg-white text-sm leading-5 font-medium text-gray-700 hover:text-gray-500 focus:outline-none focus:border-blue-300 focus:shadow-outline-blue active:bg-gray-50 active:text-gray-800 flex items-center'
      },
      menuClasses: {
        type: String,
        default: 'origin-top-right absolute right-0 mt-2 w-56 rounded-md shadow-lg z-50'
      }
    },

    data() {
      return {
        show: false
      }
    },

    methods: {
      toggle() {
        this.show = !this.show
      },

      hide() {
        this.show = false
      }
    }
  }
</script>
