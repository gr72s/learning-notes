# redux
## api
### redux
* createStore(): 创建全局state
* combineReducers(): 将多个reducer函数合并成一个reducer函数
* bindActionCreators(): 将多个action creator对象, 转成拥有同名key的对象. 使用dispatch包装后可以直接调用
* compose(): 从右到左把接收到的函数合成后的最终函数
### react-redux
* <Provider>: 使嵌套在内的组件可以通过connect()获得redux store
* connect(): 返回一个新的与redux store连接的组件类
  * mapStateToProps(state, [ownProps]): stateProps 
    * state: 监听redux store
    * ownProps: 监听来自父组件的props
    * stateProps: 合并成一个新的state传入组件  
  * mapDispatchToProps(dispatch, [ownProps]): dispatchProps
    * dispatch: redux的dispatch函数, 可以使用bindActionCreators()包装action creator
  * mergeProps(stateProps, dispatchProps, ownProps)
    * stateProps: mapStateToProps()的执行结果
    * dispatchProps: mapDispatchToProps()的执行结果
    * ownProps: 父组件传递的props
### redux toolkit
* 