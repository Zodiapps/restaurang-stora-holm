<template lang="pug">
article
  h2 {{ week.title }}
  table
    tbody
      tr(v-for='day in week.menu', v-if='day')
        td {{ day.weekday | weekday }}
        td
          ul
            li(v-for='option in day.options') {{ option }}
  nuxt-content(:document='week')
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  props: {
    week: {
      type: Object,
      required: true,
    },
  },
})
</script>

<style lang="scss" scoped>
article {
  @apply flex flex-col;
}

table {
  @apply border-separate;

  $border-spacing: 1rem;

  margin-left: -$border-spacing;
  margin-right: -$border-spacing;
  border-spacing: $border-spacing;
}

td {
  @apply align-baseline;

  ul {
    @apply list-none;

    li {
      @apply mb-3;
    }
  }
}
</style>
