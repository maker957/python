int dish=1,apple=0,banana=0;
semaphore Father,Monther,Son,Daughter;

Father(){
    wait(dish);
    放苹果；
    signal(apple);
}
Monther(){
    wait(dish);
    放香蕉；
    signal(banana);
}
Son(){
    wait(banana);
    取香蕉；
    signal(dish);
    吃香蕉；
}
Daughter(){
    wait(apple);
    取苹果;
    signal(dish);
    吃苹果；
}