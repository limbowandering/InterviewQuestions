### 题目列表

1. 请谈谈Vue中的MVVM模式
2.  `v-show`和`v-if`指令的共同点和不同点?
3. 如何让CSS只在当前组件中起作用?
4. `<keep-alive></keep-alive>`的作用是什么?
5. Vue中引入组件的步骤?
6. 指令v-el的作用是什么?

#### 1. 请谈谈Vue中的MVVM模式

MVVM全称是Model-View-ViewModel

Vue是以数据为驱动的，Vue自身将DOM和数据进行绑定，一旦创建绑定，DOM和数据将保持同步，每当数据发生变化，DOM会跟着变化。  ViewModel是Vue的核心，它是Vue的一个实例。Vue实例时作用域某个HTML元素上的这个HTML元素可以是body，也可以是某个id所指代的元素。

DOMListeners和DataBindings是实现双向绑定的关键。DOMListeners监听页面所有View层DOM元素的变化，当发生变化，Model层的数据随之变化；DataBindings监听Model层的数据，当数据发生变化，View层的DOM元素随之变化。

#### 2. `v-show`和`v-if`指令的共同点和不同点?

- `v-show`指令是通过修改元素的`display` CSS属性让其显示或者隐藏.
- `v-if`指令是直接销毁和重建DOM达到让元素显示和隐藏的效果

#### 3.如何让CSS只在当前组件中起作用?

将当前组件的`<style>`修改为`<style scoped>` 

#### 4.`<keep-alive></keep-alive>`的作用是什么?

`<keep-alive></keep-alive>`包裹动态组件时, 会缓存不活动的组件实例, 主要用于保留组件状态或避免重新渲染.

#### 5. Vue中引入组件的步骤?

1. 采用ES6的`import ... from ...`语法
2. 对组件进行注册
3. 使用组件`<my-component></my-component>`

#### 6. 指令v-el的作用是什么?

 