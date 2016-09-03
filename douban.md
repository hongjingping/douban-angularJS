# 豆瓣api电影列表项目
    # 分析需求
        # 列表功能
            # 正在热映
            # 即将上线
            # top250
        # 分析分页
        # loading效果
        # search查询
        # 详情页

    # 1.下载模板
        # 在根文件件下载angular和angular ui-router文件和bootstrap（下载后可以在package.json文件中查看）
    # 2.在index.html中对模板进行改造
        # 将引入文件的路径进行修改
          ```
          <script src="../node_modules/angular/angular.js"></script>
          <script src="../node_modules/angular-ui-router/release/angular-ui-router.js"></script>
          ```
        # 将样式去bootstrap中引入(bootstrap中的body部分拷贝过来，然后引入CSS文件)，然后进行修改
        # 在浏览器中查看，控制台的network中dashboard.css,我们将样式全部拷贝到我们的app.css文件中，直接将之前的css全部替换掉(app.css文件放在css文件的最下面)
===================以上页面模板已经完成==========================


        # 3.改造页面左边的代码结构，将index.html中找到overview的代码段，进行改造，写上正在热映、即将上映、top250，将多余的ul删除
        # 4.将HTML中的table删除，还有view1，view2进行删除
        # 5.将div class="row placeholders"部分删除
        # 6.div.main部分写ui-view，将其中的代码段抽取出来，放到新建的1.html文件中
        ```
        <h1 class="page-header">Dashboard</h1>
        萍宝贝。。。。
        <h2 class="sub-header">Section title</h2>
        <div class="table-responsive">
        	萍宝贝...
        </div>
        ```
        # 7.写路由的东西，让中间的部分可以在点击左边的时候来回切换
        在app.js写模块,先定义一个模块，然后在HTML中引入模块
        ```
        angular.module('appModule', []).
        ```
        # 8.引入`angular.module('appModule', []).
               config(['$stateProvider','$urlRouterProvider', function($stateProvider,$urlRouterProvider) `
        # 9.配置路由
        ***** 创建模块的时候要按照mvc思想划分，不能将list页面也在模块中，要分开来写，建立一个areas文件夹，然后建立一个list文件夹，将list.html放到该文件夹里面
        # 10.创建一个控制器，控制器定义在模块中，我们要先定义一个模块出来
        `list_controller.js`文件，内部写入
        ```
        /*10.1list页面的控制器*/
        angular.module("listController",[])
        	.controller("listController",["$scope",function($scope){

        	}]);
        ```
        10.2然后将`listController`写到app.js的路由设置中
        ```
        $stateProvider
        		.state('list', {
        			url: '/areas/list/list.html',
        			controller:"listController"
        		});
        ```
        10.3然后在页面中引入模块`  <script src="./areas/list/list_controller.js"></script> `
        10.4然后在app.js中主模块注入
        ```
         angular.module('appModule', [
         	'ui.router',
         	'listModule',
         ]).
        ```
### 以上步骤总结:
1. index页面，一上来就启动，但是文件未执行，
2. 然后引入一些angular.js等文件，然后开始执行，
3. 执行的时候从ng-app开始执行，找到appModule,
4. 然后去appModule,appModule里面我们引了ui-router,在模块中注入uirouterlistModule,(这两个东西我们可以使用)，然后
5. 我们配置路由的东西，配置了list路由，给了list页面，然后给了模板页面，list控制器
6. 然后找不到路径的时候跳转到list页面

# 我们点击左边的list，右边就进行跳转，我们去查看doubanAPIv2








