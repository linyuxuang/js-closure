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




