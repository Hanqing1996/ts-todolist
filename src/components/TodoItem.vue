<template>
  <div class="item-wrapper">
    <slot></slot>
    <button>delete</button>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";

@Component
export default class todoItem extends Vue {
  @Prop() private msg!: string;
}
</script>

<style scoped lang="scss">
.item-warpper{
    border: 1px solid red
}
</style>
