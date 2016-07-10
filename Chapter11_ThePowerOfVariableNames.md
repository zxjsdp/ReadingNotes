`Chapter 11` 变量名的力量（The Power Of Variable Names）
=====================================================


`11.1` 选择好变量名的注意事项（Considerations in Choosing Good Names）
------------------------------------------------------------------

类似 `x`，`xx`，`x1` 之类的变量名是糟糕的变量名，而类似 `balance`，`lastPayment`，`newPurchases` 之类的变量名是好的变量名。好的变量名是可读的，易记的和恰如其分的。


- #### 最重要的命名注意事项（The Most Important Naming Considerations）

    变量名要完全、准确地描述出该变量所代表的事物，对变量的描述就是最佳的变量名。好的变量名示例：`checkTotal`，`velocity`，`trainVelocity`，`currentDate`，`linesPerPage`。

- #### 以问题为导向（Problem Orientation）

    好记的名字反映的通常是问题，而不是解决方案。如果一个名字反映了计算的某些方面而不是问题本身，那么它反映的就是`how`而非`what`了。应该在名字中反映出问题本身。例如在财务软件中，`sum` 比 `calcVal` 更好。

- #### 最适当的名字长度（Optimum Name Length）

    变量平均名字在 `8` 到 `20` 个字符的时候调试比较容易。长度较合适的名字示例：`numTeamMembers`，`teamMemberCount`，`seatCount`，`pointsRecord`。

- #### 作用域对变量名的影响（The Effect of Scope on Variable Names）

    短的变量名（例如：`i`）代表一个临时的数据（循环计数器或者下标），其作用域非常有限。细心的程序员避免使用短的变量名。应对位于全局命名空间中的名字加以限定词，在 C++ 和 C# 里，可以使用 `namespace` 关键字来划分全局命名空间，在 Java 中，可以通过使用 package 达到同样的目的。对不支持命名空间或者包的语言，可以使用命名规则来划分全局命名空间，例如增加前缀（`uiEmployee`，`dbEmployee` 等）。

- #### 变量名中的计算值限定词（Computed-Value Qualifiers in Variable Names）

    对于表示计算结果的变量，将总额，平均值，最大值（`Total`，`Sum`，`Average`，`Max`，`Min`，`Record`，`String`，`Pointer`）这样的限定词加到名字的最后。这样可以突出为变量赋予主要含义的部份（位于变量前部），也可以使变量名的规则统一，提高可读性。一个例外是：将 `num` 放置在变量的开始位置代表总数，而放置在变量结束位置代表下标。这样的情况应使用 `Count`（或者 `Total`）以及 `Index` 来避开这个问题（例如：`customerCount` 及 `customerIndex`）。

- #### 变量名中的常用对仗词（Common Opposites in Variable Names）

    在命名规则中应用准确的对仗词，将有助于变量的理解和记忆。常用的对仗词：

    - `begin` / `end`
    - `first` / `last`
    - `min` / `max`
    - `next` / `previous`
    - `old` / `new`
    - `source` / `target`
    - `up` / `down`


`11.2` 为特定类型的数据命名（Naming Specific Types of Data）
---------------------------------------------------------

为特定类型的数据命名时，需要作出特殊的考虑。本节讲述与循环变量、状态变量、临时变量、布尔变量、枚举类型和具名常量有关的考虑事项。

- #### 为循环下标命名（Naming Loop Indexes）

    - 约定俗成的简单循环变量名：`i`，`j`，`k`
    - 若变量要在循环之外使用，应使用描述性较好的循环变量名（例如：`recordCount`）
    - 若使用嵌套循环，应给循环变量赋予更长的名字以提高可读性（例如：`score[teamIndex][eventIndex]` 比 `score[i][j]` 更清晰）。这有助于避免下标串话（index cross-talk）问题。

- #### 为状态变量命名（Naming Status Variables）

    状态变量用于描述程序的状态。应该为状态变量取一个比 `flag` 更好的名字，因为我们看不出 `flag` 是做什么的。标记应该用**枚举类型**，**具名常量**，或者用作具名常量的**全局变量**来对其赋值及比较。例如：`characterType = CONTROL_CHARACTER` 比 `statusFlag = 0x80` 更有意义。

- #### 为临时变量命名（Naming Temporary Variables）

    临时变量用于存储计算的中间结果，作为临时占位符，以及存储内务管理（housekeeping）值。但其实从某种角度来看，程序中的大多数变量都可以算是临时性的。我们不应该使用不提供任何信息的临时变量名（例如：`x`，`temp`），而应该使用具有描述性的真正的变量来替代“临时”变量。

- #### 为布尔变量命名（Naming Boolean Variables）

    应当给布尔变量赋予隐含**“真/假”**含义的名字。这些名字（例如：`done`）的状态要么是 `true`，要么是 `false`。而 `status` 等类型的名字没有明确的 `true` 或者 `false` 的概念。

    有些人喜欢在布尔变量名前加上 `is`，优点是避免了使用模糊不清的名字（例如：`isStatus`），缺点是降低了简单逻辑表达式的可读性（`is (isFound)` 的可读性要差于 `if (found)`）。

    应当使用肯定的布尔变量名，例如 `found`，否定的名字难以阅读（例如：`if not notFound`）。

    一些典型的布尔变量名：

    - `done`
    - `error`
    - `found`
    - `success` / `ok`

- #### 为枚举类型命名（Naming Enumerated Types）

    可以为枚举类型使用前缀命名约定（例如：`Color_Red`，`Color_Green`。或者：`Planet_Earth`，`Planet_Mars`）。对于枚举成员总是被冠以枚举字前缀的编程语言（例如 Java），可以将上述名字简化为：`Color.Red` 和 `Planet.Earth`。或者：

- #### 为常量命名（Naming Constants）

    常量命名应当根据该常量所表示的含义进行命名，而不是其数值。例如：`CYCLES_NEEDED` 比 `FIVE` 要好。


`11.3` 命名规则的力量（The Power of Naming Conventions）
-----------------------------------------------------

有效的命名规则是最强大的工具之一。

- #### 为什么要有规则（Why Have Conventions）

    命名规则的存在为代码增加了结构，减少了我们需要考虑的事情。命名规则的好处：

    - 要求我们按规矩行事，集中精力关注代码更重要的特征。
    - 有助于在项目之间传递知识，名字的相似性将能帮助我们更容易理解不熟悉的变量。
    - 一致风格的代码有助于在新项目中更快速地学习。
    - 有助于减少名字增生（name proliferation），即给同一个对象起两个不同的名字。
    - 弥补编程语言的不足之处，用规则来效仿具名常量和枚举类型。规则可以根据局部数据、类数据以及全局数据的不同而有所差别，并且可以包含编译器不直接提供的类型信息。
    - 强调相关变量之间的关系。

- #### 何时采用命名规则（When You Should Have a Naming Conventions）

    在下列情况下命名规则很有价值：

    - 多个程序员合作开发一个项目。
    - 把程序交给另一位程序员来修改和维护的时候。
    - 当其他程序员评估你所写的代码的时候。
    - 程序规模太大，以至于无法再脑海里同时了解事情的全貌，而必须分而治之的时候。
    - 当程序生命期足够长，长到可能会把它搁置几个星期或几个月之后又重新启动有关程序的工作时。
    - 当一个项目中存在一些不常见的术语，并且你希望在编写代码阶段使用标准的术语或者缩写的时候。

- #### 正式程度（Degrees of Formality）

    对于微小的，用完即弃的项目而言，严格的规则可能没有必要。对于多人协作的大型项目，在任何阶段，正式规则都是成为提高可读性的必不可少的辅助手段。
