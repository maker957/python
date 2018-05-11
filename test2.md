int mutexSN=1,mutexNS=1;
int countSN=0,countNS=0;
sempahore bridge=1;

//南通向北函数
SN(){        
    do{
        wait(mutexSN);   
        if(countSN==0)    //如果南向北没有车通过
          wait(bridge);    //分配桥资源
        countSN++;         
        signal(mutexSN);     
        过桥中
        wait(mutexSN);
        countSN--;
        if(countSN==0)    //如果南向北没有车通过
          signal(bridge);  //释放桥面资源
        signal(mutexSN);    //释放互斥信号量，复原
    }while(TRUE)
} 


// 北通南函数   同理
NS(){
    do{
        wait(mutexSN);   
        if(countSN==0)    
          wait(bridge);   
        countSN++;         
        signal(mutexSN);     
        过桥中
        wait(mutexSN);
        countSN--;
        if(countSN==0)   
          signal(bridge);  
        signal(mutexSN); 
    }while(TRUE)
}