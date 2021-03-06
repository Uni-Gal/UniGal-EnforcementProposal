# UniGal-EnforcementProposal

UniGal-EnforcementProposal，简称UEP，是UniGal的警告和错误汇总形成文档的提案。

由于不同的引擎之间或多或少存在一定的不能完美导出的问题，作为一个标准，应当给出成熟的异常反馈系统。UEP就是为此设计的。

UniGal标准（Script与Diagram）可能会有多套分别由官方或第三方维护的编译器、渲染器。但均应遵循本错误提案，即本提案中的错误并非您的工具链实现一定会遇到。

UEP将错误分为两个等级，Warning（警告）和Error（错误）。编号系统中对应的格式分别为```UEWXXXX```和```UEEXXXX```，其中```XXXX```为数字。

由于大部分UniGal工具链均采用C++/C#系技术栈的原因，UEP的命名风格将参考MSVS生态主导的[MSDN风格](https://docs.microsoft.com/zh-cn/cpp/build/reference/c-cpp-building-reference?view=msvc-140)而不是以Pypi生态主导的[PEP风格](https://www.python.org/dev/peps/)作为命名原则。

但是为方便Python使用者，如果您在您的引擎中使用Python实现相关操作，您可以使用```UEP-W-XXXX```和```UEP-E-XXXX```命名，但序号应与本处保持一致。

## 处理方式

### Warning

Warning是因为不同引擎之间存在差异，从部分引擎向另一部分引擎转换的时候会因为引擎存在特性而无法无损和完美的转换。能够被UniGal理解意图且有可行的处理方式的，我们将尽可能保证转写出来，但需要对此提出警告。

### Error

Error将终止编译器的运行，并不再编译Error行及Error行之后的代码。出现错误一般是遇到了逻辑不允许的场景，源语言的部分特性在目标引擎中不能实现且没有方法正确理解。也可能是出现了类型错误或者调用了未定义的函数，unigal脚本中出现了源引擎和目标引擎都不存在的函数（无论是否在unigal标准中定义过）

## 索引列表

您可以根据下列的索引号找到对应警告/错误的释义。部分警告和释义将有单独的说明库。

### [UEW](./UEW/README.md)

| 编号 Number | 说明 Description | 文档链接 Docs |
| ----------- | ---------------- | ------------- |
| UEW0001  |                  |               |
| UEW0002  |                  |               |
| UEW0003  |                  |               |
| ……          | ……               | ……            |

更多警告请您查阅UEW目录


### [UEE](./UEE/README.md)

| 编号 Number | 说明 Description                  | 文档链接 Docs |
| ----------- | --------------------------------- | ------------- |
| UEE0001  | 不完整的XML结构或不合法的XML语法  | [UEE0001](./UEE/UEE0001.md)    |
| UEE0002  | 非定义的unigal根节点的合法XML文档 | [UEE0002](./UEE/UEE0002.md)    |
| UEE0003  | 不合法的unigal文件                | [UEE0003](./UEE/UEE0003.md)    |
| …… | …… | …… |

更多错误请您查阅UEE目录

## 注意事项

1. 在编写过程中，如果有暂时的UEP提案但不知道应该如何编号，可以先以`UEW-Proposal`或者`UEE-Proposal`开头，后面不要使用数字，而使用一个有规律有意义的英文单词来命名，待相似问题整理较多后一并编号。
2. 不强制写解决方法
3. 未来在提案逐步增加的时候，希望作为提案目录的两个README文件可以自动生成，便于在修改了说明的时候能够快速准确的同步。类似name-suggestion-index通过npm进行自动生成一样，或者通过GitHub-Action来完成。
4. 若部分UEP提案的编号不够合理需要交换，应提前向整个社区说明，之后在通过后交换或重新指定涉及到的UEP提案的编号，并有次序的对所有存量代码进行更新
