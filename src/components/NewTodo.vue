<template>
  <div class="new-todo-wrapper">
      <input type="text" v-model="content"/>
      <button @click="addTodo">add</button>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";

@Component
export default class todoItem extends Vue {
  @Prop() private msg!: string;
  content=''
  addTodo(){
      this.$emit('addTodo',this.content)
      this.content=''
  }
}
</script>

<style scoped lang="scss">
</style>
