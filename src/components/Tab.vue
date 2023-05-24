<template>
  <div class="tab-content" v-show="title === selectedTab">
    <slot />
  </div>
</template>

<script>
import { inject } from 'vue'

export default {
  props: {
    title: {
      type: String
    }
  },

  setup() {
    const selectedTab = inject('selectedTab')

    return {
      selectedTab
    }
  }
}
</script>

<style>
.tab-content {
  min-height: 400px;
  padding: 20px;

  border-radius: 5px;
  box-shadow: 0 3px 5px 5px rgba(0,0,0,0.05);
}
</style>