<template>
  <div class="whole">
    <UIButton @btnTap="btnTap" :large="large" :xsmall="xsmall" :xlarge="xlarge" :normal="normal" :small="small"
                :round="round" :circle="circle" :tile="tile" :disabled="disabled"
                color="green"></UIButton>
    <div class="sizeGroup">
      <UIButton @btnTap="resize('xsmall')">xsmall</UIButton>
      <UIButton @btnTap="resize('small')">small</UIButton>
      <UIButton @btnTap="resize('normal')">normal</UIButton>
      <UIButton @btnTap="resize('large')">large</UIButton>
      <UIButton @btnTap="resize('xlarge')">xlarge</UIButton>
    </div>

    <div class="sizeGroup">
      <UIButton @btnTap="changeShape('tile')">tile</UIButton>
      <UIButton @btnTap="changeShape('normal')">normal</UIButton>
      <UIButton @btnTap="changeShape('round')">round</UIButton>
      <UIButton @btnTap="changeShape('circle')">circle</UIButton>
    </div>
    <UIButton @btnTap="jinyong">禁用</UIButton>
  </div>
</template>


<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import UIButton from "@/components/UIKIT/UIButton.vue";

@Component({
  components: {
    UIButton
  }
})
export default class Home extends Vue {
  private xsmall: boolean = false;
  private small: boolean = false;
  private normal: boolean = false;
  private large: boolean = false;
  private xlarge: boolean = false;
  private circle: boolean = false;
  private round: boolean = false;
  private tile: boolean = false;
  private disabled: boolean = false;

  private resize(val: string) {
    switch (val) {
      case "xsmall":
        this.small = false;
        this.large = false;
        this.xlarge = false;
        this.xsmall = !this.xsmall;
        break;
      case "small":
        this.xsmall = false;
        this.large = false;
        this.xlarge = false;
        this.small = !this.small;
        break;
      case "normal":
        this.small = false;
        this.xsmall = false;
        this.large = false;
        this.xlarge = false;
        break;
      case "large":
        this.xlarge = false;
        this.small = false;
        this.xsmall = false;
        this.xlarge = false;
        this.large = !this.large;
        break;
      case "xlarge":
        this.small = false;
        this.xsmall = false;
        this.large = false;
        this.xlarge = !this.xlarge;
        break;
      default:
        break;
    }
  }
  private changeShape(val: string) {
    switch (val) {
      case "tile":
        this.tile = !this.tile;
        this.round = false;
        this.circle = false;
        break;
      case "round":
        this.round = !this.round;
        this.tile = false;
        this.circle = false;
        break;
      case "normal":
        this.circle = false;
        this.tile = false;
        this.round = false;
        break;
      case "circle":
        this.tile = false;
        this.round = false;
        this.circle = !this.circle;
        break;
      default:
        break;
    }
  }

  private btnTap(e:MouseEvent) {
      console.log(e)
  }
  private jinyong(){
      this.disabled = !this.disabled;
  }
}
</script>


<style lang="scss" scope>
.whole {
  display: flex;
  flex-direction: column;
  align-items: center;
}
.sizeGroup {
  display: flex;
  margin: 30px;
}
</style>