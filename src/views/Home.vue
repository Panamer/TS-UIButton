<template>
  <div class="root-home">
    <div class="btn-container">
      <UIButton @click="onClick"
        :xsmall="xsmall"
        :small="small"
        :large="large"
        :xlarge="xlarge"
        >点我呀</UIButton>
    </div>
    <div class="btn-group">
      <UIButton class="btn" @click="resize('xsmall')">超小</UIButton>
      <UIButton class="btn" @click="resize('small')">小</UIButton>
      <UIButton class="btn" @click="resize('normal')">正常</UIButton>
      <UIButton class="btn" @click="resize('large')">大</UIButton>
      <UIButton class="btn" @click="resize('xlarge')">超大</UIButton>
    </div>
    <div>{{ tint }}</div>
  </div>
</template>

<script lang="ts">
// Home
import { Component, Vue } from 'vue-property-decorator';
import UIButton from '@/components/UIK/UIButtoon.vue';

@Component({
  components: {
    UIButton
  }
})
export default class Home extends Vue{

  // 计算属性
    private get tint() {
        return `计算属性： ${this.xsmall}-${this.small}-${this.large}-${this.xlarge}`
    }

  private xsmall = false;
  private small = false;
  private normal = false;
  private large = false;
  private xlarge = false;

  private resize(type: string) {
     switch(type) {
       case 'xsmall':
         this.xsmall = true;
         this.small = false;
         this.large = false;
         this.xlarge = false;
         break;
       case 'small':
         this.xsmall = false;
         this.small = true;
         this.large = false;
         this.xlarge = false;
         break;
       case 'normal':
         this.xsmall = false;
         this.small = false;
         this.large = false;
         this.xlarge = false;
         break;
       case 'large':
         this.xsmall = false;
         this.small = false;
         this.large = true;
         this.xlarge = false;
         break;
       case 'xlarge':
         this.xlarge = true;
         this.xsmall = false;
         this.small = false;
         this.large = false;
         break;
     }
  }

  private onClick(event: MouseEvent) {
    console.log(event);
  }
}
 
</script>
<style lang="stylus">
.btn-container
  width 480px
  height 160px
  display flex
  justify-content center
  align-items center
.btn
  margin 6px
</style>