# 第45讲 hashCode与equals深度剖析与源码详解

**Object类**的equals方法的特定

* （1）自反性：x.equals(x)应该返回true
* （2）对称性：x.equals(y)为true，那么y.equals(x)也为true
* （3）传递性：x.equals(y)为true，并且y.equals(z)为true，那么x.equals(z)也应该为true
* （4）一致性：x.equals(y)的第一次调用为true，那么x.equals(y)的第二次、第三次、第n次调用也应该为true，前提条件是在
比较之间没有修改x也没有修改y。
* (5)对于非空应用x，x.equals(null)返回false。

在大多数情况下，我们比较的都是对象的内容，而不是对象的hashCode，通过重写hashCode和equals方法，可以实现往一个集合里面
添加对象时，如果该对象的内容已在集合中，那么该对象就不能添加到集合中。

    import java.util.HashSet;

    public class HashSetTest3 {
    	public static void main(String[] args) {
    		HashSet set = new HashSet();
    		Student s1 = new Student("zhangsan");
    		Student s2 = new Student("zhangsan");
    		set.add(s1);
    		set.add(s2);
    		System.out.println(set);
    	}
    }
    
    class Student {
    	String name;
    
    	public Student(String name) {
    		this.name = name;
    	}
    
    	public int hashCode() {
    		return this.name.hashCode();
    	}
    
    	public boolean equals(Object obj) {
    		if (this == obj) {
    			return true;
    		}
    		if (null != obj && obj instanceof Student) {
    			Student s = (Student) obj;
    			if (name.equals(s.name)) {
    				return true;
    			}
    		}
    		return false;
    	}
    }

