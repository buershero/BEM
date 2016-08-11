# BEM

CSS BEM

---

#题外话
再烂的东西,如果真的毫无价值,是会马上被历史所淹没的

每个领域都有沉淀下来对特定开发者在特定场景有用的东西
很赞同克军那句取其精华去其糟粕,何为精华,自己根据使用场景取舍

可能大多数同学看到那么多下划线中划线以及那么长我靠还有驼峰的名字,就会觉得混乱和不爽
不爽是一个很主观的词儿,他除了解决心理问题,没法解决生理问题

CSS这么多年并没有一个相对比较严谨的套路出来,宽松的写法导致团队成员写法各异,丢在页面都能跑起来,但混着做项目就不敢动或理不清别人写的代码
"这个CSS重写一遍比修改老文件快",这样的念头几乎所有人都曾有过.


作者：大猫
链接：https://www.zhihu.com/question/21935157/answer/20116700
来源：知乎

#what's BEM
> BEM的意思就是块（block）、元素（element）、修饰符（modifier），是由Yandex团队（Yandex是俄罗斯重要网络服务门户之一）提出的一种CSS Class 命名方法。



# 认识 BEM
####B
> Block !误区:这个block并非inline-block里的block,
而是将所有东西都划分为一个独立的模块,一个header是block,header里嵌套的搜索框是block,甚至一个icon一个logo也是block,block可以相互嵌套.

####E
> Element !误区:如果一个Element-son是另一个Element-father的子元素,
那么写法是 Block__Element-father__Element-son_Modifer,嵌套多了会很长么?
不是的!!!
一个Block下的所有Element无论相互层级如何,都要摊开扁平的属于Block
所以 BEM 最多只有 B+E+M 三级,不可能出现 B+E+E+..+E+M 超长class名,也要求E不能同名

####M
> Modifier 之前我们经常写的 .current .active 等表达状态

# 从Class中解读B.E.M

> 我们常说CSS的注释要写WHY,而不是写WHAT,看Class命名最好就知道是WHAT
BEM提出的一个概念是用连接符号来表达,它并不规定必须用什么连接符,但规定用不同连接符做团队内约定区分BEM 3类元素

例如我们可以这样约定
> __双下划线代表B和E连接例如 menu__item
_单下划线代表B和M或E和M的连接 例如 menu_active 或 menu__item_active
-中划线同英语里做连字符例如 mod-menu 或 mod-menu__item 这里 B或E或M需要多个单词来描述,就使用中划线

![img](https://pic2.zhimg.com/2f34e41f10a05b3675a8153110aa19bd_r.jpg)

可以采用的是类似 bootstrap 的方案
用程度来划分,而非具体数值,所以根本就不会存在.text-size30这么个类,那个写style上去有毛线区别.
![img](https://pic1.zhimg.com/e952dd436525ba2079e729742c2f91bc_b.jpg)

在var.less里定义具体的数值
![img](https://pic1.zhimg.com/adde16397f58140be3f84a3dc8f8a734_b.jpg)
在 ui.less 里调用

> BEM的任何一个block都可以到处用,这对模块并不多的手机项目非常有利.

#注
> BEM是不允许用标签选择器的,一开始难以接受...
.menu li 能搞定的事情需要每个 li 都写.menu-item

