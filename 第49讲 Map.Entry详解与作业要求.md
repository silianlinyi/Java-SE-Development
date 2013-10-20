# 第49讲 Map.Entry详解与作业要求

随机生成50个数字（整数），每个数字的范围是[10,50]，统计每个数字出现的次数以及出现次数最多的数字与它的个数，最后将每个
数字及其出现次数打印出来。 

    import java.util.HashMap;
    import java.util.Iterator;
    import java.util.Map;
    import java.util.Set;
    
    public class Test01 {
    
    	public static void main(String[] args) {
    		HashMap map = new HashMap();
    		int counter = 1;
    		while (counter <= 50) {
    			double ran = Math.random();
    			int ret = (int) Math.round(ran * 100);
    			if (ret >= 10 && ret <= 50) {
    				counter++;
    				if (map.containsKey(new Integer(ret))) { // 已包含该键
    					Integer val = (Integer) map.get(new Integer(ret));
    					int value = val.intValue() + 1;
    					map.put(new Integer(ret), new Integer(value));
    				} else {
    					map.put(new Integer(ret), new Integer(1));
    				}
    
    			}
    		}
    
    		Set set = map.entrySet();
    		Iterator iter = set.iterator();
    
    		int maxKey = 0;
    		int maxValue = 0;
    
    		while (iter.hasNext()) {
    			Map.Entry entry = (Map.Entry) iter.next();
    			int key = ((Integer) entry.getKey()).intValue();
    			int value = ((Integer) entry.getValue()).intValue();
    			if (value > maxValue) {
    				maxValue = value;
    				maxKey = key;
    			}
    			System.out.println(key + " = " + value);
    		}
    
    		System.out.println("maxKey = " + maxKey);
    		System.out.println("maxValue = " + maxValue);
    
    	}
    
    }
