
[slide]
<div style="text-align: center">
    <img src="/img/logo.png" style="width:300px"/>
</div>
# Vue实例
每一个Vue.js应用都是通过构造函数Vue创建的一个Vue的根实例启动的。
[slide]
## Vue实例
----
* <a href="/md/vue.md?theme=light#2">实例属性</a>
* <a>实例方法</a>
    * <a href="/md/vue.md?theme=light#3">实例方法/数据</a>
    * <a href="/md/vue.md?theme=light#4">实例方法/事件</a>
    * <a href="/md/vue.md?theme=light#5">实例方法/生命周期</a>

[slide]
## 实例属性
----
* <a href="/md/vue.md?theme=light#3">vm.$data</a>
* <a href="/md/vue.md?theme=light#4">vm.$props</a>
* <a href="/md/vue.md?theme=light#6">vm.$el</a>
* <a href="/md/vue.md?theme=light#6">vm.$options</a>
* <a href="/md/vue.md?theme=light#6">vm.$parent</a>
* <a href="/md/vue.md?theme=light#6">vm.$root</a>
* <a href="/md/vue.md?theme=light#6">vm.$children</a>
* <a href="/md/vue.md?theme=light#6">vm.$slot</a>
* <a href="/md/vue.md?theme=light#6">vm.$scopedSlot</a>
* <a href="/md/vue.md?theme=light#6">vm.$refs</a>
* <a href="/md/vue.md?theme=light#6">vm.$isServer</a>
[slide]
## $data
----
 * 类型[Object]
 * Vue 实例观察的数据对象。Vue 实例代理了对其 data 对象属性的访问。
 * <a href="http://localhost:8080/#/props">🌰</a>
[slide]
## $props
----
 * 类型[Object]
 * 当前组件接收到的 props 对象。Vue 实例代理了对其 props 对象属性的访问。
 * <a href="http://localhost:8080/#/props">🌰</a>
[slide]
## $el
----
 * 类型[HTMLElement]
 * Vue 实例使用的根 DOM 元素。
 * <a href="http://localhost:8080/#/props">🌰</a>
[slide]
## $options
----
 * 类型[Object]
 * 只读
 * 用于当前 Vue 实例的初始化选项。需要在选项中包含自定义属性时会有用处：
 * <a href="http://localhost:8080/#/options">🌰</a>
[slide]
## $parent $root $children
----
 * 类型
    * parent root [Vue instance]
    * children [Array [Vue instance]]
 * 只读
 * 详细
    * parent：父实例，如果当前实例有的话。
    * root： 当前组件树的根 Vue 实例。如果当前实例没有父实例，此实例将会是其自己。
    * children：当前实例的直接子组件。需要注意 $children 并不保证顺序，也不是响应式的。如果你发现自己正在尝试使用 $children 来进行数据绑定，考虑使用一个数组配合 v-for 来生成子组件，并且使用 Array 作为真正的来源。
 * <a href="http://localhost:8080/#/props">🌰</a>
[slide]
## $slots
----
 * 类型 { [name: string]: ?Array<VNode> }
 * 只读
 * 详细
    * 用来访问被插槽分发的内容。每个具名插槽 有其相应的属性 (例如：slot="foo" 中的内容将会在 vm.$slots.foo 中被找到)。default 属性包括了所有没有被包含在具名插槽中的节点。在使用渲染函数书写一个组件时，访问 vm.$slots 最有帮助。
 * <a href="http://localhost:8080/#/solt">🌰</a>
[slide]
## $scopedSlots
----
* 类型：{ [name: string]: props => VNode | Array<VNode> }
* 只读
* 详细：
    * 用来访问作用域插槽。对于包括 默认 slot 在内的每一个插槽，该对象都包含一个返回相应 VNode 的函数。
    vm.$scopedSlots 在使用渲染函数开发一个组件时特别有用。
 * <a href="http://localhost:8080/#/scopedslot">🌰</a>
[slide]
## $refs
----
* 类型：Object
* 只读
* 详细：
    * 一个对象，持有已注册过 ref 的所有子组件。
 * <a href="http://localhost:8080/#/ref">🌰</a>
[slide]
## $isServer
----
* 类型：boolean
* 只读
* 详细：
    * 当前 Vue 实例是否运行于服务器。
[slide]
## $attrs $listeners
----
* 类型：
    * $attrs：{ [key: string]: string }
    * $listeners { [key: string]: Function |Array<Function>}
* 只读
* 详细：
    * $attrs: 包含了父作用域中不作为 prop 被识别 (且获取) 的特性绑定 (class 和 style 除外)。当一个组件没有声明任何 prop 时，这里会包含所有父作用域的绑定 (class 和 style 除外)，并且可以通过 v-bind="$attrs" 传入内部组件——在创建更高层次的组件时非常有用。
    * $listeners: 包含了父作用域中的 (不含 .native 修饰器的) v-on 事件监听器。它可以通过 v-on="$listeners" 传入内部组件——在创建更高层次的组件时非常有用。
* <a href="http://localhost:8080/#/attr">🌰</a>
[slide]
## Vue实例/数据
----
* <a href="/md/vue.md?theme=light#6">vm.$watch</a>
[slide]
## vm.$watch
----
* 参数：
    * {string | Function} expOrFn
    * {Function | Object} callback
    * {Object} [options]
    * {boolean} deep
    * {boolean} immediate
* 用法：
观察 Vue 实例变化的一个表达式或计算属性函数。回调函数得到的参数为新值和旧值。表达式只接受监督的键路径。对于更复杂的表达式，用一个函数取代。
* 注意： 在变异 (不是替换) 对象或数组时，旧值将与新值相同，因为它们的引用指向同一个对象/数组。Vue 不会保留变异之前值的副本。
* <a href="http://localhost:8080/#/methoddata">🌰</a>
[slide]
## 事件
----
* <a href="/md/vue.md?theme=light#6">vm.$on</a>
* <a href="/md/vue.md?theme=light#6">vm.$once</a>
* <a href="/md/vue.md?theme=light#6">vm.$off</a>
* <a href="/md/vue.md?theme=light#6">vm.$emit</a>
[slide]
## $on $emit
----
* 参数：
    * $on
        * {string | Array<string>} event (数组只在 2.2.0+ 中支持)
        * {Function} callback
    * $emit 
        * {string} event
        * [...args]
* 用法：
    * $on: 监听当前实例上的自定义事件。事件可以由vm.$emit触发。回调函数会接收所有传入事件触发函数的额外参数。
    * $emit: 触发当前实例上的事件。附加参数都会传给监听器回调。
[slide]
## $once $off
----
* 参数：
    * $once
        * {string} event
        * {Function} callback
    * $off 
        * {string | Array<string>} event (只在 2.2.2+ 支持数组)
        * {Function} [callback]
* 用法：
    * $on: 监听一个自定义事件，但是只触发一次，在第一次触发之后移除监听器。
    * $emit: 移除自定义事件监听器。如果没有提供参数，则移除所有的事件监听器; 如果只提供了事件，则移除该事件所有的监听器；如果同时提供了事件与回调，则只移除这个回调的监听器。
* <a href="http://localhost:8080/#/methodevent">🌰</a>
[slide]

### 生命周期
---
* <a href="/md/vue.md?theme=light#6">vm.$mount</a>
* <a href="/md/vue.md?theme=light#6">vm.$forceUpdate</a>
* <a href="/md/vue.md?theme=light#6">vm.$nextTick</a>
* <a href="/md/vue.md?theme=light#6">vm.$destory</a>
[slide]
## $mount( [elementOrSelector] )
----
* 参数：
    * {Element | string} [elementOrSelector]
    * {boolean} [hydrating]
* 返回值 vm - 实例自身
* 用法：
    如果 Vue 实例在实例化时没有收到 el 选项，则它处于“未挂载”状态，没有关联的 DOM 元素。可以使用 vm.$mount() 手动地挂载一个未挂载的实例。

    如果没有提供 elementOrSelector 参数，模板将被渲染为文档之外的的元素，并且你必须使用原生 DOM API 把它插入文档中。

    这个方法返回实例自身，因而可以链式调用其它实例方法。
[slide]
## $forceUpdate()
----
* 参数：
    * {Function} [callback]
* 用法：
    将回调延迟到下次 DOM 更新循环之后执行。在修改数据之后立即使用它，然后等待 DOM 更新。它跟全局方法 Vue.nextTick 一样，不同的是回调的 this 自动绑定到调用它的实例上。
* 注意：
    2.1.0 起新增：如果没有提供回调且在支持 Promise 的环境中，则返回一个 Promise。请注意 Vue 不自带 Promise 的 polyfill，所以如果你的目标浏览器不是原生支持 Promise (IE：你们都看我干嘛)，你得自行 polyfill。
[slide]
## $nextTick([callback])
----
* 用法：
    迫使 Vue 实例重新渲染。注意它仅仅影响实例本身和插入插槽内容的子组件，而不是所有子组件。
[slide]
## $nextTick([callback])
----
* 用法：
    完全销毁一个实例。清理它与其它实例的连接，解绑它的全部指令及事件监听器。
    触发 beforeDestroy 和 destroyed 的钩子。
* <a href="http://localhost:8080/#/methodlife">🌰</a>
[slide]
## Q & A
[slide]
