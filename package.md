otl 存放HDA的地方
scripts 存放python脚本的地方
help 存放帮助相关的地方
OPmenu.xml 设置节点右键菜单

现在我要添加一个打开设置help的操作，这个action需要出现右键菜单中。那么我得修改OPmenu.xml.
添加action中...

当添加完action后，看下help的格式。

Documenting your assets
https://www.sidefx.com/docs/houdini/help/nodes.html

文件命名规则
[namespace--]name[-version].txt



创建自定义节点example
https://www.sidefx.com/docs/houdini/help/createexamples.html
HOUDINIPATH/Help/examples/nodes/nodetype/nodename/
HOUDINIPATH/
    Help/
        examples/
            nodes/
                sop/
                    mysop/
                        MyNodeExample.hda
                        MyNodeExample.txt