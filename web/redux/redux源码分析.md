# redux

## api

### redux

- createStore(): 创建全局 state
- combineReducers(): 将多个 reducer 函数合并成一个 reducer 函数
- bindActionCreators(): 将多个 action creator 对象, 转成拥有同名 key 的对象. 使用 dispatch 包装后可以直接调用
- compose(): 从右到左把接收到的函数合成后的最终函数

### react-redux

- <Provider>: 使嵌套在内的组件可以通过 connect()获得 redux store
- connect(): 返回一个新的与 redux store 连接的组件类
  - mapStateToProps(state, [ownProps]): stateProps
    - state: 监听 redux store
    - ownProps: 监听来自父组件的 props
    - stateProps: 合并成一个新的 state 传入组件
  - mapDispatchToProps(dispatch, [ownProps]): dispatchProps
    - dispatch: redux 的 dispatch 函数, 可以使用 bindActionCreators()包装 action creator
  - mergeProps(stateProps, dispatchProps, ownProps)
    - stateProps: mapStateToProps()的执行结果
    - dispatchProps: mapDispatchToProps()的执行结果
    - ownProps: 父组件传递的 props

### redux toolkit

-
