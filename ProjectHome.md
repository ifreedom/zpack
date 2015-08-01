请前往downloads页面下载最新的代码包，不要使用svn来checkout代码！拜GFW所赐，google code的svn已经很久无法访问，无法提交最新的修改。

zpack is a small, fast, easy to expand archiving file format

zpack是一个小巧，易用，高效并且便于移植的文件打包格式

![http://multi-crash.com/download/zpEditor.png](http://multi-crash.com/download/zpEditor.png)

速度

> 以文件名hash方式检索，读取效率至上

> 删除包内文件时，只删除文件索引，不需要移动包内数据

> 在两次flush之间用户可以添加任意多个文件（例如添加整个目录），这期间除了被添加文件数据的写入，没有任何其它多余的文件IO操作


大小

> 添加文件时，优先插入到之前删除文件留下的空闲位置，尽可能利用空间

> 用户可以调用countFragmentSize检查当前包内空闲空间字节数，必要的话可以调用defrag进行整理

> 支持zlib压缩


安全/健壮

> 严格保证在用户调用flush()之前，包文件的有效性。这样当用户一次添加/删除较多文件的过程中即使发生意外（例如停电，进程被强行终止等），包文件能保持最后一次flush后的逻辑结构，不会发生灾难性后果

> 包文件以只读方式打开时，原始的文件名信息不会被加载到内存。也就是说用户可以选择不将原始目录结构和文件名写入包内，包文件仍然能正常读取


工具

> 虽然包内文件是以扁平方式组织（以保证检索效率），但zpack另外提供工具类ZpExplorer，让用户可以以树状目录形式浏览和编辑包内文件

> 提供命令行工具，接近dos使用习惯

> 提供类似windows explorer的编辑器


其它

> 目标文件不受4g大小限制

> 核心读取模块仅依赖c++标准库，很容易移植到windows以外的平台，例如Linux，Mac，iPhone等

> 代码小巧精简，不提供任何多余接口。

> 支持同时写入和读取