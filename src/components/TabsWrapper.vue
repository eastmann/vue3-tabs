<template>
  <div class="tabs">
    <ul class="tabs__header">
      <li
        v-for="title in tabTitles"
        :key="title"
        :class="{ 'selected' : selectedTab === title }"
        @click="selectedTab = title"
      >
        {{ title }}
      </li>
    </ul>
    <slot />
  </div>
</template>

<script>
import { ref, provide } from 'vue'

export default {
  setup(props, { slots }) {

    const tabTitles = ref(slots.default().map((tab) => {
      return tab.props.title
    }))

    const selectedTab = ref(tabTitles.value[0])

    provide('selectedTab', selectedTab)

    return {
      tabTitles,
      selectedTab,
    }
  }
}
</script>

<style lang="less">
.tabs {
  max-width: 400px;
  margin: 0 auto;

  &__header {
    display: flex;

    list-style: none;
    margin-bottom: 10px;
    padding: 0;

    li {
      margin-right: 10px;
      padding: 10px 20px;

      width: 80px;

      text-align: center;

      background-color: #ddd;
      border-radius: 5px;
      cursor: pointer;

      transition: 0.4s all ease-out;

      &.selected {
        color: white;

        background-color: #0984e3;
      }
    }
  }
}
</style>