<template>
  <svg
    :class="`animate-spin h-${size} w-${size} text-${loaderColor}-600`"
    fill="none"
    viewBox="0 0 24 24"
  >
    <circle
      class="opacity-25"
      cx="12"
      cy="12"
      r="10"
      stroke="currentColor"
      stroke-width="4"
    ></circle>
    <path
      class=""
      fill="currentColor"
      d="M4 12a8 8 0 018-8V0C5.373 0 0 5.373 0 12h4zm2 5.291A7.962 7.962 0 014 12H0c0 3.042 1.135 5.824 3 7.938l3-2.647z"
    ></path>
  </svg>
</template>

<script>
import { mapGetters } from "vuex";
export default {
  name: "Progress Spinner",
  props: {
    size: {
      type: Number,
      required: false,
      default: 6
    },
    color: {
      type: String,
      required: false
    }
  },
  computed: {
    loaderColor() {
      if (this.color) {
        return this.color;
      } else {
        //Override the color to the theme color if one is not provided as a prop
        return this.themeColor;
      }
    },
    ...mapGetters("theme", {
      themeColor: "color"
    })
  }
};
</script>
