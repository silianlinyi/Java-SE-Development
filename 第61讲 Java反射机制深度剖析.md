# 第61讲 Java反射机制深度剖析

**Java反射机制主要提供了以下功能**

* 在运行时判断任意一个对象所属的类；
* 在运行时构造任意一个类的对象；
* 在运行时判断任意一个类所具有的成员变量和方法；
* 在运行时调用任意一个对象的方法；

**在JDK中，主要由以下类来实现Java反射机制，这些类都位于java.lang.reflect包中**

* Class类：代表一个类
* Field类：代表类的成员变量（成员变量也称为类的属性）
* Method类：代表类的方法
* Constructor类：代表类的构造方法
* Array类：提供了动态创建数组，以及访问数组的元素的静态方法

**通过Java的反射机制访问一个类中的私有方法**

> Private.java

    public class Private {
        private String sayHello(String name) {
      	    return "hello: " + name;
        }
    }

> TestPrivate.java

    import java.lang.reflect.InvocationTargetException;
    import java.lang.reflect.Method;
    
    public class TestPrivate {
    	public static void main(String[] args) throws NoSuchMethodException, SecurityException, IllegalAccessException,
    			IllegalArgumentException, InvocationTargetException {
    		Private p = new Private();
    		Class<?> classType = p.getClass();
    		Method method = classType.getDeclaredMethod("sayHello", new Class[] { String.class });
    		method.setAccessible(true); // 压制Java的访问控制检查
    		String str = (String) method.invoke(p, new Object[] { "Jack" });
    		System.out.println(str);
    	}
    }

如果不加<code>method.setAccessible(true);</code>这行代码，便不能访问一个类中的私有方法。

**通过Java的反射机制访问一个类中的私有变量**

> Private2.java

    public class Private2 {
    	private String name = "zhangsan";
    
    	public String getName() {
    		return name;
    	}
    }









