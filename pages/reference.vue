<template>
  <div class="MainPage">
    <site-top-upper />
    <cards-tabs />
    <card-row class="DataBlock" />
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import CardsTabs from '@/components/CardsTabs.vue'
import CardRow from '@/components/cards/CardRow.vue'

export default Vue.extend({
  components: {
    CardsTabs,
    CardRow
  }
})
</script>

<style lang="scss" scoped>
.MainPage {
  .DataBlock {
    margin: 20px -8px;

    .DataCard {
      @include largerThan($medium) {
        padding: 10px;
      }

      @include lessThan($small) {
        padding: 4px 8px;
      }
    }
  }
}
</style>
