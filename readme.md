获取表单元素值的几种方式
在白板上任意写出10个事件修饰符
为什么要在v-for的时候加key属性
在白板上手写出标签切换的核心代码
==============================================

#补充修饰符

.lazy(失去焦点之后才让a发生改变)
<input v-model.lazy="a"/>

.trim(去掉收尾空格)
<input v-model.trim="a"/>

.number(转换为数字类型,方便做数学运算)
<input v-model.number="a"/>

================================================
#组件(Vue框架核心)
概念：包含了View,Model,Methods等完整的、具有独立功能的自定义元素。
#创建方式:
1.全局(定义在new Vue前面,在所有的Vue实例挂载元素内使用)
    Vue.component('组件名',{
        template:'<div></div>'
    })
2.局部(只能在当前Vue实例的挂载元素内使用)
    new Vue({
        components:{
            '组件名1':{template:'<div></div>'},
            '组件名2':{template:'<div></div>'}
        }
    })
#组件属性
在组件中methods,computed都和之前写法一样，唯独data不同.
data变成了函数,要在里面return{},因为每个组件返回的数据都应该是独立的,隔离的
components:{
    parent:{
        template:'',
        data(){
            return {}
        }
    }
}

#组件嵌套
<div id="app">
    <parent></parent>
</div>
var child1={template:'<div></div>'}
components:{
    parent:{
        template:'<div><child1></child1><child2></child2></div>',
        components:{
            child1,child2:{
                template:'<div></div>'
            }
        }
    }
}

#组件通讯
1.父 -> 子(Props)
    父:
        <div>
            <child :tfboys="变量"></child>
        </div>
    子:
        child:{
            props:['tfboys'],
            template:`{{tfboys}}`
        }
    验证Props:
        props:{
            tfboys:{
                type:数据类型,
                required:true
            }
        }