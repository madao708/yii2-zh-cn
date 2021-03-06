翻译必读 Translating Guide
============================

为了方便大家更好的了解并上手权威指南，新闻，源码注释等翻译项目，这里特地为大家提供翻译的相关流程的讲解。

简述
--------

- 翻译指粗翻和持续更新翻译工作，更新文档前的翻译状态。
- 校对指文档的校对和更新工作，更新文档前的校对状态。
- 同一文档的翻译人员和校对人员最好不同，以便核查勘误。
- 无论翻译还是校对，都请标明所参考的**英文原文的版本日期**，请注意放**原文日期**，目的是方便后续更新文档。
- 亲，动笔之前，除了本篇文章之外，也请先完整看一遍[校阅手册](translation-proofreading.md)，了解最终文档的成文要求，稍稍地注意一下，
就能有效减轻校阅人员的工作量，减少无意义的内耗。

概念及工具
------------

<a name="git-scm"></a>
### 版本控制与 Git
我们使用git作为版本控制，GitHub作为官方仓库。
推荐使用 [SourceTree](http://www.sourcetreeapp.com/) 或 GitHub 官方客户端作为 Git 前端。同时，如果用到控制台终端了，
常用的命令我们会告诉你的。
与Git相关的教程，可以看下[CSDN上某大神写的零基础学Git系列](http://blog.csdn.net/column/details/jacky-git.html?&page=2)

> 如果各位有条件，欢迎在国内帮我们建立文档的镜像站点或镜像代码仓库，并使用脚本与我们保持同步，以防 GFW 抽风，提高国内同胞的访问效率。

<a name="terminology"></a>
### 术语

关于某些特定概念，我们应该遵循相同的术语翻译，有些Yii的独有概念，其含义也很好理解的，我们可以不翻译。
翻译的难点很大一部分都在术语的翻译上，**当一条术语被最终确定下来的时候，记得把他添加到术语表中哦。**

<a name="intro-glossay"></a>
#### 术语表

相关术语的介绍和参考翻译，被称为**[术语表（Glossary）](translation-glossary.md)**。
如果在翻译的过程中，发现有新的术语，然而它还没有被加入术语表，请千万帮忙加入，防止同一个术语在不同字符串里的翻译不同，这很重要。
同时一个术语的翻译可能影响其他所有人的翻译，请添加术语之前一定要查阅下Yii1.0时代的翻译，确保传承性，拿不准请在群里讨论一下。
如果有术语翻译错误的地方，还请不吝赐教。

#### 微软术语搜索

计算机科学及软件工程领域的一些技术词汇，完全可以参考微软的术语设计。很多翻译都很有借鉴性，当然也有翻译地很烂的。
把它当计算机专业词典用吧！仅供参考——[微软术语搜索](http://www.microsoft.com/Language/zh-CN/Search.aspx?langID=zh-cn)

#### Google
为了找到一个好的术语翻译，通常需要查阅大量文档资料。请永远记住善用Google，有益身体健康……
繁体以及日语的翻译都是可以借鉴的哦。

#### 企鹅群
很多术语确定不了也可以在群里讨论一下，让我们一起来找出最好的术语翻译！官方一群：343188481

### 认领机制README.md
在yii2文档子站里，点击权威手册链接直接进入手册部分的同学应该会首先跳转到 `README.md` 的页面。
此时 `README.md` 就是一个目录.对于参与翻译的同学来说，README.md还提供记录文件版本和翻译状态的功能，接下来我会一一[解释](#README)。


具体过程
------------------

###Git 工作流程###

有关Git的使用，可以参考 Yii2 官方的内部文档[git-workflow.md](internals-zh-CN/git-workflow.md)

我们的工作流程与其类似。也有所不同。

先简单介绍两个库：

* **官方库**：yii-chinesization/yii2 官方授权我们维护的框架库，用于收集大家翻译的文档，并随时反馈给官方。地址：`https://github.com/yii2-chinesization/yii2.git`
* **文档库**：yii2-chinesization/yii2-zh-cn 只用于存放翻译指南资料及老翻译的备份，**新翻译请别放在这里**。地址：`https://github.com/yii2-chinesization/yii2-zh-cn.git`

<a name="git-workflow"></a>
#### 参考 Git 操作流程 --重要！

有些朋友可能不太清楚如何用 Git 参与翻译工作，我这里写一个简单的流程，大家可以参考一下：

1. 首先 fork 这个项目以及由我们负责维护的 [Yii2 分支](https://github.com/yii2-chinesization/yii2/)
2. 把 fork 过去的两个项目也就是你名下的那两个项目分别 clone 到你的本地
3. 在命令行运行 `git branch temp` 来创建一个新分支，这里用 `temp`，你也可以用 `translating` 或其他任何名字
4. 运行 `git checkout temp` 来切换到新分支
5. 添加官方的远端库，命名为 upstream（也可以是其他名字），用来获取更新
    * 在**文档库的目录**内，运行 `git remote add upstream https://github.com/yii2-chinesization/yii2-zh-cn.git` 把汉化组的文档库添加为远端库
    * 在 **yii2 目录**内，运行 `git remote add upstream https://github.com/yii2-chinesization/yii2.git` 把汉化组的官方库添加为远端库
    * 例外：如果你同时 fork 了yiisoft/yii2，你可以把 yii2-chiesization 远端，命名为 `chinesization`，或其他你能明白的名字。这样修改以后请对应修改掉下面的 `upstream` 改为你命名的远端名称，如 `chinesization`

步骤1~5是一个初始化流程，只需要做一遍就行，之后请一直在 temp （或其他名字）分支进行修改。

6. 分别在两个目录内，运行 `git remote update` 更新两库
7. 分别在两个目录内，运行 `git fetch upstream master` 拉取两库的更新到本地
8. 分别在两个目录内，使用 `git checkout temp` 切换回你的日常分支后，运行 `git rebase upstream/master` 将两库的更新合并到你的分支

如果修改过程中我们的仓库（不管是文档库还是官方库）有了更新，在对应的库目录下重复6、7、8步即可。
也可以简写为 `git pull --rebase upstream master` 一条命令。或者你用 SourceTree 等 GUI 的话，在 push 面板下勾选用变基替代合并。也可以起到相同的作用，巧用变基，可以避免不必要的合并。

修改之后，首先 Push 到你的库，然后登录 GitHub，在你的库的首页可以看到一个 `pull request` 按钮，点击它，填写一些说明信息，
然后提交即可。

> 特别注意：在官方进行重大调整的时候，我们有可能会临时更改默认分支，请注意把master对应更换成新的默认分支。

如果没有直接修改权限，你需要创建 Pull Request 简称 PR。最好可以把相关PR都挂在同一个 issue 之下，便于交流。
如果你翻译地较多，在群里吱一声，就可以提升为写权限，这样就可以直接 push 了，即使是有权限也建议使用 PR 处理
大规模多次零散的翻译提交，这样管理和沟通都会方便。

<a name="detailed-workflow"></a>
#### 具体翻译流程 --极其重要！！

* 翻译前，请先在 **文档库** 认领并登记[原文日期](#get-date)，认领信息登记在[文档库/guide-zh-CN/README](guide-zh-CN/README.md)，将待翻译改为翻译中，后加原文日期和你的 GitHub ID。例如：`【翻译中-20140505-你的 GitHub 名】`。 **[点此了解原文日期的获取](#get-date)**
* 在官方库内的英文原版目录内，把你要翻译的文件的最新版本复制到（官方库内的，不是文档库）`guide-zh-CN`
目录内，确保 GitHub
里官方文件的最后修改日期（不是本地文件日期哦）和你认领时填写的编辑时间吻合。
* 翻译地过程中请多多参考术语表，这能大幅减少你寻求准确翻译的时间。如果术语表中没有的翻译，可以参考
[有道词典](http://dict.youdao.com/) 和 [微软术语搜索](http://www.microsoft.com/Language/zh-cn/Search.aspx)等工具。
* 翻译完成后提交给 `yii-chinesization/yii2` 官方库，别忘了更改文档库里 [README里的翻译状态](guide-zh-CN/README.md)，参考
[汉化进度](#tags) 章节。

认领机制
--------
<a name="README"></a>
### README

在文档库的 `guide` 目录内的 `README.md` 是整个文档的目录索引。[打开看下](https://github.com/yii2-chinesization/yii2-zh-cn/blob/master/guide-zh-CN/README.md)，你会发现，在每个条目的的前方会有一个标签，而后方则有着一些日期。他们是做神马的呢？

针对每一个不同的文件我们分别挂上一些标签，以及翻译时所参考的英文原文的版本日期。标签用来标注翻译的状态，日期用来在后续文档更新及审阅时，方便找到对应的英文版本，并根据 GitHub 所提供的 History 功能对照着修改我们的译文，使得我们的译文和英文始终保持对应状态。防止文档老旧，更新不及时的情况。

<a name="tags"></a>
#### 文档汉化进度分为以下几种状态：

等待认领：

- 【待翻译】任何翻译人员都可认领
- 【需更新】指官方文档已更新，需要翻译人员或校对进行更新，及翻译。

无需认领：

- 【翻译中】表示该文档已被某位翻译人员认领，正在翻译中，请等他完成再刊错。
- 【已完成】官方文档无更新，已完成翻译和校对的中文文档，表示该文档翻译结束。

翻译状态：

- 【未校对】粗翻完成后更改
- 【已更新】标明新增了内容，后面往往跟其他标签如：
    * 【已更新|未校对】更新且汉化完成，但未经严格校对
    * 【已更新|翻译中】更新大量内容，尚未完全汉化
- 【已完成】校对完毕更新为该状态，文档需要更新时更改标签为【需更新】

临时状态：

- 待定中 - 文章整体都被官方标记为TBD，也就是待定的部分。
- 编撰中 - 官方正在编撰或完善中的文档，官方没定稿，我们搞不了。

<a name="get-date"></a>
#### 原文的版本日期

没有原文的版本日期，就难以判别该文章需不需要与官方文档进行更新，也难以给读者一个信息时效性上的提醒。
所以需要在Readme和正文中加入文档的原文日期，是**`原文日期`**不是**`翻译成稿日期`**。

原文日期的获取，可以在 GitHub 的页面上查看，也可以使用 `git log` 查看你所选版本所对应的 last committed date。
```
git log ./path/file.md
```

写日期不写 hash 主要基于两点考虑：

1. 日期更容易修改，更不容易出错。
2. 日期更直观，能明确知道该文档是否需要更新，而不需搜索寻找复杂的 commits 列表。

缺点是，如果一天之内官方有多次更新，校对者需要检查当天的后几次 commits 是否也需要更新。

翻译技巧与注意事项
-----------------

>小技巧: **最好不要直接在原文上修改**：如果zh-CN文件夹里没有相应的文件请先复制原文进来。翻译的时候，最好一句一句地翻译，先翻译好中文再删除英文；
也可以复制一下英文原句，然后在克隆的句子上修改；也可以充分发挥大显示器的特长，左手原文右手译文。
这样可以省的翻译到一半突然想不起来英文原文，节省掉再去查找原文的时间，减少打扰，提高翻译质量和效率。

- 翻译时不必中英文一一对应，先读懂英文的意思，然后用中文表达相同或相近的意思即可。想象着我们自己就是手册的原作者，写出我们所想要表达的意思即可。有的时候，一一对应反而不好翻译。

- 翻译时可以善用工具，除了有道和 Google，参考[Yii 1.1 的手册翻译](http://www.yiiframework.com/doc/guide/1.1/zh_cn/index)也是不错的办法。可能有些文字，涉及较深的专业知识，其含义本身就算是中文也不太好理解。你可以选择跳过，也可以选择查阅相关维基百科，来搞明白这些概念，方便的话请随后把这些概念加入[术语表](#intro-glossary)。

- 粗翻时也无需太过注重信达雅的要求。这些部分可以在后续校对工作时，慢慢达到。关于信达雅的确切含义，请见后面校对篇[信达雅](translation-proofreading.md#xin-da-ya)部分的说明。


### 需特殊注意的文字

#### 维持原样
有些字符串是不应该被翻译的，比如：

1. 源代码。注：源代码我们不翻译，但是注释还是要翻译的，别漏了。源代码里面的部分内容被卖萌地翻译了。但是切记注意保持功能的正确性。
2. 众所周知的概念，如Codeception，Alias，AssetManager，这类概念仅在标题处注释其中文名称即可，具体翻译中可以不使用其中文名称，原因有二，其一，这些是 Yii
的独有概念，其在语境中的含义和在其他编程语言中可能不尽相同。其二，为了国际化的需要，由于工作量的原因，我们不太可能翻译世界上出现的每一篇有关
 Yii 的教程和心得分享。所以看懂原文就显得比较重要，而这些概念在有道和
 Google 上翻译的都是英文领域的概念，而非Yii语境下的概念，帮助大家对其英文原词建立相应的概念就显得比较重要。
3. Markdown语法所需特殊符号。[请参考校阅手册的 Markdown 部分](translation-proofreading.md#markdown)，以及 [Markdown
语法推荐标准](markdown-code-style.md)

#### URL

如果是原文中的URL是维基百科或PHP手册，且提供了相应的中文翻译，我们最好把URL改为中文版本页面的URL。

如果没有，则最好注明**英文**字样。

比如：

    [pivot table]: http://en.wikipedia.org/wiki/Pivot_table "Pivot table（数据透视表（中间表），英文，维基百科）"

#### 斜体字

若原文中包含 ```*斜体*```，改为 ```**粗体**```，原因是中文是区块字，倾斜后会破坏区块感觉，影响阅读体验。

附录
------------------
### 参考阅读

- [校对手册](translation-proofreading.md)：如果说翻译是从无到有，校对就是从有到优。读校对手册，就像作者要摸透编辑的心。
才能写出编辑满意的高质量文章。
- [术语表](translation-glossary.md) 对术语的翻译有任何意见都请随时建立issue大家交流讨论，我们也会不定期向全社会征集对于术语翻译的意见与建议。
- [Yii 文档风格指南](documentation_style_guide.md)：主要记述了官方编写文档时的考虑与原则，理解他们有利于我们理解官方的
叙述风格，增加翻译的准确性。
- [Markdown 编写规范（试行）](markdown-code-style.md)

