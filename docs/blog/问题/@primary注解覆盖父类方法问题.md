### 问题场景

现在有两个类userInfo 和 user ，其中userInfo  使用了@Primary 注解，并且是user的子类

```java
@Service
@Primary
@Slf4j
public class UserInfo extends User{
    
    public Boolean updateStatus(Long userId) {
        ```业务逻辑```

}
```

```java
@Service
@Slf4j
public class User {
    
    public Boolean updateStatus(Long userId) {
        ```业务逻辑```
    }
    
    public Boolean updateName(Long userId) {
        ```业务逻辑```
    }
        
}
```

假如我在其他地方使用时

```java
@Service
public class Login{
    @Autowired
    private User user;
    
     public Boolean insertLoginUser(Long userId){
         user.updateStatus(userId);
     }
}

```

那么在Login这个类中执行的是user.updateStatus方法呢？ 还是userInfo.updateStatus方法呢

在Idea中，点击这个updateStatus方法跳转到的是User类，但是实际执行的却是UserInfo类中的方法

这个问题的关键就在于**`@Primary`**注解



### 那么@Primary 在 Spring 中起什么作用呢？

当存在多个相同类型的 bean 时，它赋予某个 bean 更高的优先级。

当容器中存在父类和子类两个 Bean，且你按父类类型注入时，@Primary 让子类 Bean 成为首选，因此实际注入的是子类的实例。

Java 遵循动态绑定（运行时绑定），实际对象是子类实例，因此调用的必然是子类重写后的方法，与引用变量的类型（父类）无关。

如果子类没有重写父类方法，那么调用时执行的才是父类的方法。

