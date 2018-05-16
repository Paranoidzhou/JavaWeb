### 回顾

- 对样式的操作：
- - obj .addClass("");    //增加节点
  - obj.removeclass("") //删除某一个class
  - obj.removeclass();   //删除所有的样式
  - obj.hasClass("");      //是否应用了某一个样式
  - obj.toggleClass("");   //切换某一个样式

### jQuery在 DOM 树中水平遍历：

- 通过节点关系，查找节点.

   obj.children(); / obj.children(selector);     //获取直接子节点

   obj.next(); / obj.next(selector);    //下一个弟弟

   obj.prev(); / obj,prev(selector);    //上一个哥哥

   obj.siblings(); / obj.siblings(selector);     //查询所有的兄弟、结果不含自己

   obj.find(selector);   //查询满足条件所有后代

   obj.parent();   //查询其父亲

