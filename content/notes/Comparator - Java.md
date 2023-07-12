---
title: "Comparator - Java"
enableToc: true
tags:
- Java
- LeetCode
---

## Comparator
A comparator interface is used to order objects of user-defined classes. If we needed to sort a class which contains fields such as name and ID number we may want to sort by either of these fields. 

Writing a sorting function can be difficult or requires rewriting if different criteria wants to be used. We can minimise this problem by using a Comparator interface. 

```java {title="Comparator"}
class NewComparator implements Comparator<T> {
	public int compare(T var1, T var2) {
		return var1.field - var2.field;
	}
}
```

The compare method compares its two arguments for order.
- Return a negative integer if the first argument is less than the second.
- Return zero if the arguments are equal.
- Return positive if the first argument is greater than the second.

Often if the comparison is zero, then we may want to compare another field to sort against it.


## Example
[LeetCode 347 - Top K frequent elements](https://leetcode.com/problems/top-k-frequent-elements/description/) 
```java {title="Leetcode 347"}
class Solution {
    public int[] topKFrequent(int[] nums, int k) {
        // Top K elements usually implies using a maxHeap
        // Put all entries into a HashMap

        HashMap<Integer, Integer> map = new HashMap<>();
        for (int num : nums) {
            map.put(num, map.getOrDefault(num, 0) + 1);
        }

		// Create heap
		/**
		 * Need to use a comparator to compare Map Entry object
		 * Otherwise the heap would not know how to sort this data type
		 */
        PriorityQueue<Map.Entry<Integer,Integer>> pq = new PriorityQueue<>(new Cmp());

        // Add all entries to pq
        for (Map.Entry<Integer, Integer> entry : map.entrySet()) {
            pq.add(entry);
        }

        // Get top K elements
        int[] result = new int[k];
        for (int i = 0; i < k; i++) {
            result[i] = pq.poll().getKey();
        }
        return result;
    }
}

  

class Cmp implements Comparator<Map.Entry<Integer, Integer>> {
    public int compare(Map.Entry<Integer, Integer> m1, Map.Entry<Integer, Integer> m2) {
        // If the frequency is the same then sort by which integer is smaller
        if (m1.getValue() == m2.getValue()) {
            return m1.getKey() - m2.getKey();
        }
        // Otherwise return the value where the frequency is highest
        return m2.getValue() - m1.getValue();
    }
}
```


## Other Usage
The Collections class also has a sorting method where you can use a comparator class in order to sort.
``` java {title="Sorting with Comparator"}
// Collections method
public void sort(List list, ComparatorClass c);

// Usage
Collections.sort(array, new sortCmp);
```

