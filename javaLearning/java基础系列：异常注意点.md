# 异常注意点 #
## 异常捕获顺序 ##
捕获异常时，我们通常先catch 子类异常，然后才能捕获父类异常，因为子类异常更详细。如果把父类异常放在子类异常前面，不能通过编译，因为后面的子类异常无用。

捕获到子类异常后，不会继续捕获其后的父类异常。
## 异常丢失 ##
1 在finally中抛出异常，可能会覆盖掉前面抛出的异常。


    public class FinalException {
        public static void main(String[] args){
        try{
            try{
                throw new FirstException();
            }finally{
                //override RedException
                throw new SecondException();
            }
        }catch(Exception e){
            System.out.println(e);
        }
        }
    }
    
    class FirstException extends Exception{}
    class SecondException extends Exception{}
>打印结果：com.timedimension.lib.BlueException

2 在finally中return,无法抛出异常。

    public static void main(String[] args){
        try{
            throw new Exception();
        }finally{
            return;
        }
    }
>打印结果：

无法打印出异常信息

注意，下面代码无法通过编译，会提示要catch异常信息

    public static void main(String[] args){
        try{
            throw new Exception();
        } finally{
          //  return;
        }
    }

