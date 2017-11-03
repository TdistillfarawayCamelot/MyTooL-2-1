# MyTooL-2-1
封装成对象，然后写入window的属性里，大概是这样吧，我也不是很懂
```js
(function(G) {
        function MyTool() {

            //查找第一个子节点或子元素的方法
            this.Firstchild = function (parent) {
                var result;
                var Fchild = parent.firstChild;
                var FEchild = parent.firstElementChild;
                // 通过正则表达式判断文本节点是不是由空格等其他符号组成的空白节点
                Fchild.nodeType === 3 && /^\s+$/.test(Fchild.nodeValue) ?
                    result = FEchild : result = Fchild;
                return result;
            };

            //查找最后一个子节点或子元素的方法
            this.Lastchild = function (parent) {
                var result;
                var Lchild = parent.lastChild;
                var LEchild = parent.lastElementChild;
                Lchild.nodeType === 3 && /^\s+$/.test(Lchild.nodeValue) ?
                    result = LEchild : result = Lchild;
                return result;
            };

            //查找相邻兄弟中后一个兄弟的元素或节点
            this.Nbrother = function (name) {
                var result;
                var someone = name.nextSibling;
                var otherone = name.nextElementSibling;
                someone.nodeType === 3 && /^\s+$/.test(someone.nodeValue) ?
                    result = otherone : result = someone;
                return result;
            };

            //查找相邻兄弟中前一个兄弟的元素或节点
            this.Pbrother = function (name) {
                var result;
                var someone = name.previousSibling;
                var otherone = name.previousElementSibling;
                someone.nodeType === 3 && /^\s+$/.test(someone.nodeValue) ?
                    result = otherone : result = someone;
                return result;
            };

            //获取指定标签的所有子元素的个数
            this.Childrenum = function (parent) {
                var result;
                var childsnum = parent.childElementCount;
                var childrens = parent.children.length;
                //条件运算符判断是不是undefined,其实判断的是true or false
                childsnum ? result = childrens : result = childsnum;
                return result;
            };

            //获取指定标签的所有子节点
            this.Cnodes = function (parent) {
                var children = parent.childNodes;
                for (i = 0; i < children.length; i++) {
                    var child = children[i];
                    if (child.nodeType === 3 && /^\s+$/.test(child.nodeValue)) {
                        parent.removeChild(child);
                    }
                    return children;
                }
            };
        }

        var mytool = new MyTool();
        var fn = MyTool.prototype;

        // 将当前的函数作用域中的对象，提升为全局作用域的
        G.MyTool = mytool;
        G.Fn = fn;

    }(window));
    ```
