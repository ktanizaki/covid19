<template>
  <component :is="cardComponent" />
</template>

<script>
import SevereCaseCard from '@/components/cards/SevereCaseCard.vue'
import SevereCaseCard2 from '@/components/cards/SevereCaseCard2.vue'
import SevereCaseCard3 from '@/components/cards/SevereCaseCard3.vue'
import SevereCaseCard4 from '@/components/cards/SevereCaseCard4.vue'
import SevereCaseCard5 from '@/components/cards/SevereCaseCard5.vue'
import SevereCaseCard6 from '@/components/cards/SevereCaseCard6.vue'
import SevereCaseCard7 from '@/components/cards/SevereCaseCard7.vue'
import MonitoringStatusOverviewCard from '@/components/cards/MonitoringStatusOverviewCard.vue'

export default {
  components: {
    SevereCaseCard,
    SevereCaseCard2,
    SevereCaseCard3,
    SevereCaseCard4,
    SevereCaseCard5,
    SevereCaseCard6,
    SevereCaseCard7,
    MonitoringStatusOverviewCard
  },
  data() {
    let title, updatedAt, cardComponent
    switch (this.$route.params.card) {
      case 'positive-status-severe-case':
        cardComponent = 'severe-case-card'
        break
      case 'positive-status-severe-case2':
        cardComponent = 'severe-case-card2'
        break
      case 'positive-status-severe-case3':
        cardComponent = 'severe-case-card3'
        break
      case 'positive-status-severe-case4':
        cardComponent = 'severe-case-card4'
        break
      case 'positive-status-severe-case5':
        cardComponent = 'severe-case-card5'
        break
      case 'positive-status-severe-case6':
        cardComponent = 'severe-case-card6'
        break
      case 'positive-status-severe-case7':
        cardComponent = 'severe-case-card7'
        break
      case 'monitoring-status-overview':
        cardComponent = 'monitoring-status-overview-card'
        break
    }

    return {
      cardComponent,
      title,
      updatedAt
    }
  },
  head() {
    const url = 'https://stopcovid19.metro.tokyo.lg.jp'
    const timestamp = new Date().getTime()
    const ogpImage =
      this.$i18n.locale === 'ja'
        ? `${url}/ogp/${this.$route.params.card}.png?t=${timestamp}`
        : `${url}/ogp/${this.$i18n.locale}/${this.$route.params.card}.png?t=${timestamp}`
    const description = `${this.$t(
      '当サイトはマスク着用率等のデータを公開するために、東京工業大学 出口研究室が開設したものです。'
    )}`
    const defaultTitle = `${this.$t('データ公開サイト') + ' '}`

    return {
      titleTemplate: title => `${this.title || title} | ${defaultTitle}`,
      meta: [
        {
          hid: 'og:url',
          property: 'og:url',
          content: url + this.$route.path + '/'
        },
        {
          hid: 'og:title',
          property: 'og:title',
          template: title => `${this.title || title} | ${defaultTitle}`,
          content: ''
        },
        {
          hid: 'description',
          name: 'description',
          template: updatedAt =>
            `${this.updatedAt || updatedAt} | ${description}`,
          content: ''
        },
        {
          hid: 'og:description',
          property: 'og:description',
          template: updatedAt =>
            `${this.updatedAt || updatedAt} | ${description}`,
          content: ''
        },
        {
          hid: 'og:image',
          property: 'og:image',
          content: ogpImage
        },
        {
          hid: 'twitter:image',
          name: 'twitter:image',
          content: ogpImage
        }
      ]
    }
  }
}
</script>
