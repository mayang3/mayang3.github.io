---
title: "[codeforce][round 555] Minimum Array"
tag:
- codeforce
- algorithm
- problemSolving
categories:
- problemSolving
---

## Algorithm

* [http://codeforces.com/contest/1157/problem/E](http://codeforces.com/contest/1157/problem/E)

두개의 array a,b 가 주어집니다.

이때 array b 는 순서를 변경할 수 있고,
순서를 변경한 b 와 a 에 대해서 특정한 연산을 한다면 array c 를 얻을 수 있습니다.

이때, *사전순* 으로 최소가 되는 array c 를 구하는 문제입니다.

몇 가지 생각해보면..

* 사전순으로 최소가 되려면 앞에서부터 작은 숫자가 와야 합니다.
* 각 array 의 최대 범위는 < n 까지입니다.
* c 를 구하는 연산이 % n 이므로, Ai + Bi 가 n 과 같다면 제일 작은 숫자가 됩니다.

위의 내용을 바탕으로 저는 아래와 같은 알고리즘을 생각했습니다.

1. Ai + Bi 가 n 보다 같거나 큰 경우에는 최대한 n 하고 가까울수록 가장 작은 수이다 ( %n 으로 나누어 지므로 그렇다.)
2. Ai + Bi 가 n 보다 적은 경우에는 0과 가까운 수가 가장 작은 수이다.


## Source Code

``` java

import java.util.Map;
import java.util.Scanner;
import java.util.TreeMap;

/**
 * @author neo82
 */
public class MinimumArray {

	/**
	 * @param args
	 */
	public static void main(String[] args) {
		Scanner scanner = new Scanner(System.in);

		int n = scanner.nextInt();

		int [] A = new int[n];

		for (int i = 0; i < n; i++) {
			A[i] = scanner.nextInt();
		}

		TreeMap<Integer, Integer> map = new TreeMap<>();

		for (int i = 0; i < n; i++) {
			map.merge(scanner.nextInt(), 1, Integer::sum);
		}

		StringBuilder sb = new StringBuilder();

		for (int i = 0; i < n; i++) {

			Integer min = map.firstKey();
			Integer max = map.ceilingKey(n - A[i]);

			if (max == null) {
				sb.append((A[i] + min) % n).append(" ");
				decreaseAndRemove(map, min);
			} else if (min == null) {
				sb.append((A[i] + max) % n).append(" ");
				decreaseAndRemove(map, max);
			} else if ((A[i] + min) % n <= (A[i] + max) % n) {
				sb.append((A[i] + min) % n).append(" ");
				decreaseAndRemove(map, min);
			} else {
				sb.append((A[i] + max) % n).append(" ");
				decreaseAndRemove(map, max);
			}
		}

		System.out.println(sb.toString());
	}

	static void decreaseAndRemove(Map<Integer, Integer> map, int key) {
		map.merge(key, -1, Integer::sum);

		if (map.get(key) <= 0) {
			map.remove(key);
		}
	}
}

```




