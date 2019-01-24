#### ﻿angular自定义服务

> - 创建自定义服务的方式
>
>   1. factory方式创建服务
>
>      `factory方式创建的服务，作用就是返回一个有属性有方法的对象。相当于：var f = myFactory();`
>
>      ```javascript
>          //创建模型
>          var app = angular.module('myApp', []);
>          //通过工厂模式创建自定义服务
>          app.factory('myFactory', function() {
>              var service = {};//定义一个Object对象'
>              service.name = "张三";
>              var age;//定义一个私有化的变量
>              //对私有属性写getter和setter方法
>              service.setAge = function(newAge){
>                  age = newAge;
>              }
>              service.getAge = function(){
>                  return age; 
>              }
>              return service;//返回这个Object对象
>          });
>          //创建控制器
>          app.controller('myCtrl', function($scope, myFactory) {
>              myFactory.setAge(20);
>              $scope.r =myFactory.getAge();
>              alert(myFactory.name);
>          });  
>      ```
>
>   2. service方式
>
>      `service方式创建自定义服务，相当于new的一个对象：var s = new myService();，只要把属性和方法添加到this上才可以在controller里调用。`
>
>      ```javascript
>          <div ng-app="myApp" ng-controller="myCtrl">
>              <h1>{{r}}</h1>
>          </div>
>          <script>
>              var app = angular.module('myApp', []);
>
>              app.service('myService', function($http,$q) {
>                  this.name = "service";
>                  this.myFunc = function (x) {
>                      return x.toString(16);//转16进制
>                  }
>                  this.getData = function(){
>                      var d = $q.defer();
>                      $http.get("ursl")//读取数据的函数。
>                          .success(function(response) {
>                          d.resolve(response);
>                      })
>                          .error(function(){
>                          alert(0)
>                          d.reject("error");
>                      });
>                      return d.promise;
>                  }
>              });
>              app.controller('myCtrl', function($scope, myService) {
>                  $scope.r = myService.myFunc(255);
>                  myService.getData().then(function(data){
>                      console.log(data);//正确时走这儿
>                  },function(data){
>                      alert(data)//错误时走这儿
>                  });
>              });
>          </script>
>      ```
>
>   3. Provider方式（了解）
>
>      ​
>
> 

相关文章：http://www.oschina.net/translate/angularjs-factory-vs-service-vs-provider