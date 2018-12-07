```
let ajax = function (){
        return new Promise(function(resolve, reject){
            // 模拟网络请求
            setTimeout(function(){
                if(true){
                    resolve("{data:null}");
                }else{
                    reject("{error:null}");
                }
            },1000)
        })
    }
    ajax().then(function(data){
        console.log("收到了"+data);
    }).catch(function(error){
        console.log("错了"+error);
    })


    function fn(id,time){
        return new Promise(function(resolve,reject){
            setTimeout(function(){
                if(true){
                    resolve(`${id}`+"成功")
                }else{
                    reject(`${id}`+"不行")
                }
            },time)
        })
    }
    // 一起加载完
    Promise.all([
        fn(1,2000)
        ,fn(2,4000)
        ,fn(3,1000)        
    ]).then(list=>{
        console.log(list);
    })
    // 优先执行
    Promise.race([
        fn(1,2000)
        ,fn(2,4000)
        ,fn(3,1000)  
    ]).then(data=>{
        console.log(data);
    })
```
