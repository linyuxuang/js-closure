# js-closure
js闭包 (私有化)
   
   
         var  init=(function(){
         	      var  a=100;
         	      function w(){
         	      	console.log(a+=1)
         	      }
                 function e(){
                 	console.log(a+=1)
                 }
           	return function(){
          		w();   //101
          		e();    //102
         	} 	
         }())
    
    init()


    模块化闭包
    
        
  
        var myObji=(function(){
            var models={};
            function define(name,deps,impl){
                 for(var i=0;i<deps.length;i++){
                 deps[i]=models[deps[i]]
                 }
                 console.log(impl())
                 var s=impl.apply(impl,deps)
                 console.log(s)
                 models[name]=impl.apply(impl,deps)
              }
              function get(name){
                 return models[name]
              } 
          return{
              define:define,
              get:get
          }
        })()

       myObji.define("bar",[],function(){
          function hello(who){
              return "我是"+who; 
          }
          return {
              hello:hello
          }
        })
        var bar=myObji.get("bar")
         bar.hello("haha")    //我是haha




   上面代码看不懂 看下面
   
   
               var modules=(function(){
                   var obj={};
                   function def(name,fun){
                        obj[name]=fun()
                   }
                  //查询{}里面的属性
                   function get(name){
                       return obj[name]
                   }
                       return{
                           def:def,
                           get:get 
                       }

               }())

                modules.def("z",function(){
                    function hello(){
                         return "哈哈我是闭包"
                    }
                    return {
                        hello:hello
                    }
                })


                 var f=modules.get("z");
                 f.hello()



