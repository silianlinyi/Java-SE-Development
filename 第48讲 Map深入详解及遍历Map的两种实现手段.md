# 第48讲 Map深入详解及遍历Map的两种实现手段

> java HashMapTest4 hello world welcome hello welcome helo

    import java.util.HashMap;
    import java.util.Iterator;
    import java.util.Set;
    
    public class HashMapTest4 {
    
    	public static void main(String[] args) {
    		HashMap map = new HashMap();
    
    		for (int i = 0; i < args.length; i++) {
    			if (map.containsKey(args[i])) {
    				Integer num = (Integer) map.get(args[i]);
    				int n = num.intValue() + 1;
    				map.put(args[i], new Integer(n));
    			} else {
    				map.put(args[i], new Integer(1));
    			}
    		}
    
    		Set set = map.keySet();
    		Iterator iter = set.iterator();
    		while (iter.hasNext()) {
    			Object key = iter.next();
    			Integer value = (Integer) map.get(key);
    			System.out.println(key + " = " + value);
    		}
    	}
    }
