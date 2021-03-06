---
title: AOP注解切面
date: 2019-05-15 11:04:52
collection: Spring
---

注解如下

```java
@Retention(RetentionPolicy.RUNTIME)
public @interface LogCollect {
}
```

切面编写

```java
/**
 * 日志收集切面
 *
 * @author Miguel.hou
 * @version v1.0
 * @date 2019-03-19
 */
@Component
@Aspect
@Slf4j
public class LogCollectAspectA {

    @Pointcut(value = "@annotation(logCollect)", argNames = "logCollect")
    public void logPointcut(LogCollect logCollect) {
        // 横切点
    }

    @Around(value = "logPointcut(logCollect)")
    public Object around(ProceedingJoinPoint joinPoint, LogCollect logCollect) throws Throwable {
        return joinPoint.proceed();
    }
}
```

```java
public class AspectUtils {

    /**
     * 获取切点的方法
     * @param joinPoint
     * @return
     * @throws NoSuchMethodException
     */
    public static Method getAspectMethod(ProceedingJoinPoint joinPoint) throws NoSuchMethodException {
        //方法签名
        Signature signature =  joinPoint.getSignature();
        Method method = ( (MethodSignature)signature ).getMethod();
        return joinPoint.getTarget().getClass().getDeclaredMethod(signature.getName(), method.getParameterTypes());
    }
}
```


