# Drag and drop

## 如何拖拽

- 拖拽元素
  - 确定拖拽的元素: 添加`draggable="true"`属性
    ```html
    <p id="p1" draggable="true">..</p>
    ```
  - 处理拖拽事件: 添加`ondragstart`事件
    ```html
    <p id="p1" draggable="true" ondragstart="">..</p>
    ```
  - 定义拖拽数据: 使用`dataTransfer.setData()`设置数据
    ```JavaScript
    function dragstart_handler(e) {
        e.dataTransfer.setData("text/plain", e.target.id);
    }
    ```
- 释放区域
  - 可以释放的区域: 需响应`dragenter`或`dragover`事件, 在事件中取消默认事件否则不能 drop
  - 定义拖拽效果: `dropEffect`属性控制在可释放区域拖拽过程中鼠标的样式
    ```JavaScript
    function dragover_handler(e) {
        e.preventDefault(); // 必须
        e.dataTransfer.dropEffect = "move";
    }
    ```
- 拖拽结束: 拖拽元素会响应`dragend`事件

## 拖拽事件

### 按事件分类

- 拖拽开始: dragstart
- 进入可释放区域: dragenter
- 进入可释放区域中: dragover
- 在可释放区域释放: drop
- 离开可释放区域: dragleave
- 拖拽中: drag
- 拖拽结束: dragend

### 按拖拽对象分类

- 可拖拽元素
  - drag
  - dragstart
  - dragend
- 可释放区域(元素)
  - dragenter
  - dragover
  - drop
  - dragleave
