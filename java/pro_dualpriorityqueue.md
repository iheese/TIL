```java
import java.util.*;

class Solution {
		public int[] solution(String[] operations) {
			List<Integer> list = new ArrayList<>();

			for(String operation : operations){
				String[] strings=operation.split(" ");
				if(strings[0].equals("I")){
					list.add(Integer.parseInt(strings[1]));
				}else{
					if(strings[1].equals("1") && !list.isEmpty()){
						list.remove(Collections.max(list));
					}else if(strings[1].equals("-1") && !list.isEmpty()){
						list.remove(Collections.min(list));
					}
				}
			}
			int[] arr = new int[2];
			if (!list.isEmpty()) {
				arr[0] = Collections.max(list);
				arr[1] = Collections.min(list);
			}
			return arr;
		}
	}
```
