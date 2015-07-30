# 三秦企业云API

三秦企业云API是针对MCS开发的三秦企业云商城和自服务门户两个移动端框架的基本前端架构说明和API接口说明，阅读此说明书能够帮助开发者使用JS命名空间和AmazeUI的特性创建丰富的移动端框架。

####Why not MVVM?
第一点是我不喜欢使用MVVM,我不喜欢双向数据流,无论wpf还是angular,这是最主要原因,第二点是在现阶段,操作DOM势必要引入JQuery,单纯的使用Angular或者其他MVVM框架在移动端的效果不是很理想。

###Why not React?
我非常喜欢React的virtual DOM,但是这势必给后面的开发者带来很多的障碍,从学习到使用有很长的路要走。

###AmazeUI？
我也是斟酌了良久引入了AmazeUI,国内最受欢迎的开源项目,github上的fork让我汗颜,有良好的文档和社区支持,最最主要是AmazeUI不同于
Bootstrap的地方,AmazeUI主要针对的是移动端开发,Bootstrap更倾向于从大向小兼容,下位开发童鞋可以试试AmazeUI React.

###RequireJS?
引入RequireJS是为了模块化项目,Angular已经将项目模块化做的很好,所以不用AMD规则的模块化了,编译需要安装nodejs和r.js
另外使用RequireJS主要是因为CMD的seajs在引入某些package很容易出现问题,12年在华山医院的时候使用seajs我就吃了很多苦,而且我个人也不觉得spm会在
不久的将来取代npm。


