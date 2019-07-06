<template>
  <div id="content">
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
  </div>
</template>

<script lang="ts">
  import { Component, Prop , Vue } from 'vue-property-decorator';
  @Component
  export default class CalcParts extends Vue {
    nenrei: number = 30;
    genzai: number = 0;

    @Prop()
    public nenrei?: number;
    public genzai?: number;




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