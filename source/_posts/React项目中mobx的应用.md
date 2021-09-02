---
title: React项目中mobx的应用
date: 2021-09-01
updated: 2021-09-01
description: " "
tags: 'react'
---

# mobx

>可以将React与Mobx结合起来的一个React组件包,支持React和React-Native

- `observable`用来声明可观察的数据。
- `computed`是声明可观察数据的演变数据，和 `observable` 具有同等地位。
- `action` 用来改变`observable`数据。(`action `不是必须的可以认为其是较好的约定最好遵循)

# mobx-react
>Provider、observer、inject均为是mobx-react提供。
- `Provider`以组件的形式存在，用来包裹最外层组件节点，并且传入 `store`通过`context `传递给后代组件。
- `observer`装饰的`react`组件将转换成一个监听者，当`observable`修饰的数据变化，react组件就会重新渲染。
- `inject`为了使被装饰的组件以`props`的形式获取到`Provider`传递过来的数据。

# 安装
```
npm install -S mobx mobx-react 
```

  在`package.json`中配置支持装饰器语法的开发依赖。

```
"dependencies": {
    "@babel/plugin-proposal-decorators": "^7.4.4",
  }
```

# 使用

1.在`react`项目`src`文件夹下新建一个用于存放`stores`的文件夹=>创建一个`appStore.js`作为项目的`store`。
```
import { observable, action } from 'mobx'; // 引入mobx 提供的方法
class HomeStore {
  @observable userName = "杨嘉浩";  // 定义一个作为观察的参数,修改会刷新jsx的view
  ......
  @observable xxx = "";
  
  //  用与改变observable数据
  @action changeName = (name)=>{
      // 在jsx中调用 changeName 传入需要更改的 userName
      this.userName = name;
  }
  ......
//  可以定义多个 action 搭配 ant Toast 做一些人性化的提示
}
const homeStore = new HomeStore ();

export default homeStore;
```
这样就是一个通过`mobx`对一个简单的`store`的创建,就可以在项目中引入使用。

2.在`src`文件夹下创建`Home.jsx`,引入定义的`store`。
```
import { observer, inject } from 'mobx-react';
// 通过 context 将 store 注入并使得任何层级的子组件可以访问到 store
// 将store中的数据注入当前组件，下面会在根组件通过 Provider 组件注入它
@inject('homeStore')
// 使用@observer装饰的react组件将转换成一个监听者，当`inject`的数据发生变化时，react组件就会重新渲染。
@observer  
export default class Home extends Component {
    constructor(props) {
        super(props);
        this.state = { };
    }
    componentDidMount() {
      console.log(this.props.homeStore)
      // 可以通过props拿到定义的 state 与 action
    }
    change(){
      this.props.homeStore.changeName("浩嘉杨");
    }
    render(){
      var { userName } = this.props.homeStore;
      return (
        <div>
          <div>用户名:{userName}</div>
          <button onClick={()=>{this.change()}}>更改</button>
        </div>
      )
    }
}
```
3.将创建的`Home.jsx`引入到`index.js`
```
import ReactDOM from 'react-dom';
import {Provider} from 'mobx-react';
import baseStore from './stores/baseStore';

const stores = {
    baseStore,
    // 便于引入多个 store
};
ReactDOM.render(
    <Provider {...stores}>
        <Page />  // 路由组件内容
    </Provider>
 ,document.getElementById('root')
);
```
# 小结
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;至此就是`react`项目中`mobx`的简单应用了，与`action`结合异步请求可以实现更多的玩法。提高工作效率的最好办法就是提升自己的能力，还可以给自己增加附加价值。💗
