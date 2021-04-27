## HTML诞生于李爵士的文章《HTML Tags》。

起手时应该写!DOCTYPE html,所谓的网页骨架，在vscode用打英文!后自动生成。

### 常用的章节标签：
* h1——h6：表示标题，从1-6字体大小依次变小。
* section：HTML5后添加的语义化标签，表示一个章节。
* article：表示页面中文章的独立结构。
* main：表示内容的主体部分，但不会影响DOM。
* aside：HTML中常用作侧边栏或者标注框

### 常用的全局属性有:
class 类名、contenteditable 内容可编辑、style 行内样式（优先级高于css，低于JS）、hidden 隐藏元素（比display:none优先级更高）、id 不常用（因为id不报错）、tabindex 控制元素是否可以通过键盘tab键聚焦（tabindex = 0表示可以交互、越大优先级越高、相同时按在dom的顺序判定、负值时不可交互）、title 通常在单行文字溢出时用来显示完整的内容。

strong、em、code、pre 等等）

### 常用的内容标签:
* a 超链接文本，一般用来跳转页面，文本或者图片都可以包含其中。
* strong 加粗标签内的文本。
* em 标签内文本以斜体显示。
* code 标签内的字体换成等宽字体。
* pre 保留标签内的空格、换行等特殊字符和格式。
