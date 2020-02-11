#### @Component
添加组件共有属性，包括 props,components 等

#### Error:Argument of type 'string | null' is not assignable to parameter of type 'string'.
```
JSON.parse(localStorage.getItem('list'))
```
解决方法：增加断言
```
JSON.parse(<string>localStorage.getItem('list'))
```

#### Object is possibly 'null'.Property 'checked' does not exist on type 'EventTarget'
```
changeStatus(e:Event){
    let checked=e.target.checked
    this.$emit
    console.log(checked)
}
```
解决方法：将 e.target 断言为 HTMLInputElement 类型
```
changeStatus(e:Event){
    let checked=(<HTMLInputElement>e.target).checked
    this.$emit
    console.log(checked)
}
```