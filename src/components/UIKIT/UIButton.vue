<template>
  <div>
    <div>
      <button
        class="default"
        @click="tap"
        :class="{
            'large':large,
            'small':small,
            'xsmall':xsmall,         
            'xlarge':xlarge,
            'tile':tile,
            'round':round,
            'circle':circle,
            'disabled':disabled
        }"
        :style="`--color-tint:${tintColor}`"
      >
        <slot>button</slot>
      </button>
    </div>
  </div>
</template>


<script lang="ts">
import { Component, Vue, Emit, Prop } from "vue-property-decorator";

@Component
export default class UIButton extends Vue {
  @Prop(Boolean) private xsmall: boolean | undefined;
  @Prop(Boolean) private small: boolean | undefined;
  @Prop(Boolean) private normal: boolean | undefined;
  @Prop(Boolean) private large: boolean | undefined;
  @Prop(Boolean) private xlarge: boolean | undefined;
  @Prop(Boolean) private tile: boolean | undefined;
  @Prop(Boolean) private round: boolean | undefined;
  @Prop(Boolean) private circle: boolean | undefined;
  @Prop(Boolean) private disabled: boolean | undefined;
  @Prop(String) private color: string | undefined;

  @Emit("btnTap")
  private tapEmit(e: MouseEvent): void { }
  
  private tap(e:MouseEvent){
    if(!this.disabled){
      this.tapEmit(e)
    }
  }
  private get tintColor() {
    if (this.color) {
      return this.color;
    } else {
      return "blue";
    }
  }
}
</script>


<style lang="scss" scope>
@mixin resize($width, $height, $fontSize) {
  width: $width;
  height: $height;
  font-size: $fontSize;
  &.round,
  &.circle {
    border-radius: ($height/ 2);
  }
  &.circle {
    width: $height;
  }
}
.default {
  @include resize(80px, 40px, 1rem);

  background-color: var(--color-tint);
  color: #fff;
  margin: 10px;
  cursor: pointer;
  &.xlarge {
    @include resize(100px, 80px, 1.5rem);
  }
  &.large {
    @include resize(90px, 50px, 1.25rem);
  }
  &.small {
    @include resize(70px, 30px, 0.75rem);
  }
  &.xsmall {
    @include resize(60px, 20px, 0.5rem);
  }
  // 改变圆角
  &.tile {
    border-radius: 0;
  }

  &.circle {
    border-radius: 100%;
  }

  // 改变颜色
  &:hover {
    filter: brightness(120%);
  }
   &:active {
    filter: brightness(80%);
  }
  &.disabled {
    background-color: #f5f5f5;
    color: #c5c8ce;
    cursor: not-allowed;
  }
}
</style>