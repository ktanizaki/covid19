<template>
  <table :class="$style.table">
    <thead>
      <tr>
        <th scope="col" rowspan="2" colspan="2">
          ウイルスに感染しない・<br />させないためにできること
        </th>
        <th :class="$style.headerDivided" scope="colgroup" colspan="4">
          なぜ必要か
        </th>
        <th scope="col" rowspan="2">
          指標
        </th>
      </tr>
      <tr>
        <th :class="$style.headerDivided" scope="col">
          健康状態を<br />把握する
        </th>
        <th :class="$style.headerDivided" scope="col">
          ウイルスを<br />体から出さない
        </th>
        <th :class="$style.headerDivided" scope="col">
          ウイルスを<br />広げない
        </th>
        <th :class="$style.headerDivided" scope="col">
          ウイルスを<br />体に入れない
        </th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td rowspan="3">一般的な対策</td>
        <td>定期的に体温を測定する</td>
        <td>&#10004;</td>
        <td />
        <td />
        <td />
        <td>体温</td>
      </tr>
      <tr>
        <td>マスクを着用する</td>
        <td />
        <td>&#10004;</td>
        <td />
        <td />
        <td>着用率</td>
      </tr>
      <tr>
        <td>手洗い・消毒する</td>
        <td />
        <td />
        <td>&#10004;</td>
        <td>&#10004;</td>
        <td>頻度</td>
      </tr>
      <tr>
        <td rowspan="4">人との接触機会を減らす</td>
        <td>在宅勤務・時差出勤の活用</td>
        <td />
        <td />
        <td>&#10004;</td>
        <td>&#10004;</td>
        <td>活用率</td>
      </tr>
      <tr>
        <td>会議・懇親会等にオンラインを活用する</td>
        <td />
        <td />
        <td>&#10004;</td>
        <td>&#10004;</td>
        <td>オンライン率</td>
      </tr>
      <tr>
        <td>外食を減らす</td>
        <td />
        <td />
        <td>&#10004;</td>
        <td>&#10004;</td>
        <td>外食率</td>
      </tr>
      <tr>
        <td>買い物をオンラインにする</td>
        <td />
        <td />
        <td>&#10004;</td>
        <td>&#10004;</td>
        <td>オンライン率</td>
      </tr>
      <tr>
        <td rowspan="1">密集を避ける</td>
        <td>人が密集する場所を避ける</td>
        <td />
        <td />
        <td />
        <td>&#10004;</td>
        <td>滞在時間</td>
      </tr>
    </tbody>
  </table>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  props: {
    status: {
      type: Array,
      required: true
    }
  },
  methods: {
    replaceFullWidthByHalfWidth(str: string) {
      return str.replace(
        /[０-９]/g,
        s => String.fromCharCode(s.charCodeAt(0) - 0xfee0) // eslint-disable-line unicorn/number-literal-case
      )
    }
  }
})
</script>

<style lang="scss" module>
$default-bdw: 2px;
$default-pad: 0.5rem;

.table {
  height: 0;
  width: 100%;
  color: $green-1;
  border-collapse: collapse;
  @include font-size(10);

  th,
  td {
    padding: $default-pad;
    border: $default-bdw solid $green-1;
    height: 100%;
  }

  td {
    text-align: center;
  }

  thead {
    white-space: nowrap;
  }

  .headerDivided {
    padding: {
      top: calc(#{$default-pad} * 0.6);
      bottom: calc(#{$default-pad} * 0.6);
    }
  }

  th[scope='row'] {
    justify-content: flex-start;
    text-align: left;
  }
}

@function px2vw($px, $vw: 0) {
  @if $vw > 0 {
    @return ceil($px / $vw * 100000vw) / 1000;
  } @else {
    @return $px * 1px;
  }
}

@mixin override($vw, $bdw, $fz, $pad) {
  .table {
    border-width: $bdw;
    @include font-size($fz);

    th,
    td {
      padding: $pad;
      border-width: $bdw;
    }

    .headerDivided {
      padding: {
        top: calc($pad * 0.6);
        bottom: calc($pad * 0.6);
      }
    }
  }
}

/*
// variables.scss Breakpoints: huge (1440)
@include lessThan(1440) {
  @include override(1440, 3, 15, 150);
}

// Vuetify Breakpoints: Large (1264)
@include lessThan(1263) {
  @include override(1263, 2, 13, 107);
}

// variables.scss Breakpoints: large (1170)
@include lessThan(1170) {
  @include override(1170, 2, 13, 107);
}

// Vuetify Breakpoints: Small (960)
@include lessThan(959) {
  @include override(960, 4, 14, 180);
}

@include lessThan(767) {
  @include override(960, 3, 14, 180);
}

// Vuetify Breakpoints: Extra Small (600)
@include lessThan(600) {
  @include override(600, 3, 14, 150);
}

@include lessThan(420) {
  @include override(600, 2, 12, 150);
}
*/
</style>
