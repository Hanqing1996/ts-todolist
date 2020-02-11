<template>
  <div class="list-wrapper">
    <div>
      <ol class="list" v-for="item in list" :key="item.name">
        <li> <input type="checkbox" :checked="item.status==='done'" @change=changeStatus($event,item)> {{item.name}}</li>
      </ol>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue, Watch } from "vue-property-decorator";
import Todo from "../src/models/Todo";

@Component({
  props: {
    list: Array
  },
  components: {
  },
  updated(){
    localStorage.setItem('list', JSON.stringify(this.$props.list))
  }
})
export default class todoList extends Vue {
  changeStatus(e:Event,item:Todo){
    let checked=(<HTMLInputElement>e.target).checked
    this.$emit('updateTodoList',{name:item.name,status:checked?'done':'todo'})
  }
}
</script>

<style scoped lang="scss">
 .list {
    list-style: none;
    > li{
      border: 1px solid red
    }
  }
</style>
