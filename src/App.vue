<template>
  <div id="app">
    <NewTodo @addTodo="show($event)"></NewTodo>
    <TodoList :list.sync="list" @updateTodoList=updateTodoList($event)></TodoList>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import NewTodo from "../src/components/NewTodo.vue";
import TodoList from "../src/components/TodoList.vue";
import Todo from "../src/models/Todo";


@Component({
  components: {
    TodoList,
    NewTodo
  }
})
export default class App extends Vue {
  list: Array<Todo> = localStorage.getItem('list')?JSON.parse(<string>localStorage.getItem('list')):[];
  show(name:string) {

    let task:Todo={
      name,
      status:'todo'
    }
    this.list.push(task)
  }
  updateTodoList(item:Todo){
    let targetName=item.name
    this.list.forEach((task,index)=>{
      if(task.name===targetName){
         this.list[index].status=item.status
      }
    })
  }
}
</script>

<style lang="scss">
#app {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
</style>
