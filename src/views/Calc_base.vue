<template>
  <div id="content" class="top">
    <h2>老後までの毎年貯蓄試算</h2>
    <div class="simulation">
      <p>老後までに毎年いくら貯めればいい？
        <br>老後までに2000万残すには毎年いくら貯金したらいいか試算してみましょう。</p>

      <h3>計算</h3>
      <p>
        <label>
          あなたの年齢
          <input type="number" pattern="[0-9]*" id="nenrei" v-model="nenrei" /> 歳
        </label>
      </p>
      <p>
        <label>
          現在の貯蓄額
          <input type="number" pattern="[0-9]*" id="genzai" v-model="genzai" /> 円
        </label>
      </p>
      <h3>結果</h3>
      <p v-if="maitoshiCalc > 0">
        毎年{{maitoshiCalc | number_format}}円、毎月{{maitukiCalc | number_format}}円、貯めれば2000万円に到達します。
      </p>
      <p v-else>
        もう到達しています。
      </p>
      <h3>条件</h3>
      <ul class="list-01">
        <li>報告書によると、"夫が65歳以上、妻が60歳以上の世帯の場合、退職後に公的年金などだけでは毎月約5万円の赤字となり、これが30年続くと2000万円不足すると指摘している。"ということなので、妻の年齢に合わせて60歳までに2000万円貯める（60歳は数えない）</li>
        <li>百の位を四捨五入して金額を出します。</li>
      </ul>


    </div>
  </div>
</template>

<script lang="ts">
  import { Component, Vue } from 'vue-property-decorator';
  @Component({
    /** filters */
    filters: {
      number_format(val) {
        return val.toLocaleString();
      }
    }
  })


  export default class Home extends Vue {
    mokuhyou: number = 20000000;
    nenrei: number = 30;
    genzai: number = 0;
    maitoshi: number = 660000;


    get maitoshiCalc(): number {
      let result = Math.round((this.mokuhyou - this.genzai) / (60 - this.nenrei) / 1000) * 1000;
      return result
    }

    get maitukiCalc(): number {
          let resultMaituki = Math.round((this.mokuhyou - this.genzai) / (60 - this.nenrei) / 12 / 1000) * 1000
          return resultMaituki
    }


  }
</script>
<style>
  p {
    margin-top: 30px;
  }

  h3 {
    margin-top: 30px;
    font-weight: bold;
  }
</style>