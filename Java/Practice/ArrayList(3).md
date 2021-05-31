### 거스름돈
거스름돈에 돈의 단위마다 각각 얼마나 필요한지 출력

```java
public class Change {
	public static void main(String[] args)	{
		int[] money = {1000, 500, 100, 50, 10};
		int total = 4950;		
		for(int i = 0; i < money.length; i++)	{
			System.out.println(money[i] + "원 : " + total/money[i] + "개");
			total = total % money[i];

//			1회전 : 4950 / 1000 = 4(950)
//			2회전 : 950 / 500 = 1(450)
//			3회전 : 450 / 100 = 4(50)
//			4회전 : 50 / 50 = 1
		}
	}
}
```

> 1000원 4개 <br>
> 500원 1개 <br>
> 100원 4개 <br>
> 50원 1개 <br>
> 10원 0개 <br>

<br>
<br>

### 3의배수 출력
배열의 정수 중에서 3의 배수만 출력

```java
public class Multiple3 {
	public static void main(String[] args)	{
		int[] num = {10, 12, 15, 16, 20, 30, 40};
		
		for(int i = 0; i < num.length; i++)	{
			if(num[i] % 3 == 0) // 3으로 나눠서 0인값 출력
				System.out.println(num[i]);
		}
	}
}
```

>12
>15
>30

<br>
<br>

### 배열 합산 출력
배열의 모든 값을 더하여 출력

```java
public class SumArray {
	public static void main(String[] args)	{
		int[] num = {10, 20, 30, 40, 50};
		int total = 0;
		
		for(int i = 0; i < num.length; i++)	{
			total += num[i];
		}
		System.out.println(total); //5회전 후 출력
	}
}
```

>150

<br>
<br>

### 2차원 배열
배열에 담긴 모든 값들의 합과 평균(소수 첫째 반올림)

```java
public class MultipleDimensionArray {
	public static void main(String[] args)	{
		int[][] arr = {{10, 20, 30, 40}, {15, 25, 35, 45}, {4, 8, 16, 32}};
		int total = 0;
		double avg = 0;
		
		for(int i = 0; i < arr.length; i++)	{
			for(int j = 0; j < arr.length+1; j++)	{
				total += arr[i][j]; //배열 값 합산
			}
		}
		avg = (double)total / (arr.length * arr[0].length); //total / 3 * 4
		System.out.println(total);
		System.out.println(Math.round(avg)); //반올림
	}
}
```

>280
>23


