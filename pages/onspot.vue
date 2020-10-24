<template>
  <div class="MainPage">
    <site-top-upper />
    <cards-tabs />
    <card-row class="DataBlock">
      <!-- モニタリング指標 マスク着用率 多摩市 -->
      <severe-case-card />
    </card-row>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import CardsTabs from '@/components/CardsTabs.vue'
import CardRow from '@/components/cards/CardRow.vue'
import SevereCaseCard from '@/components/cards/SevereCaseCard.vue'

export default Vue.extend({
  components: {
    CardsTabs,
    CardRow,
    SevereCaseCard
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
