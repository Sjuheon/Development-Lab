```java
import 성주헌.subject.Subject;

public class Student {
	public int studentNum;
	public Subject subject;
	public int rank = 1;

	public int getRank() {
		return rank;
	}

	public void setRank(int rank) {
		this.rank = rank;
	}

	public Student(int studentNum, int kor, int eng, int math) {
		this.subject = new Subject(kor, eng, math);
		this.studentNum = studentNum;
	}

	public Student(int studentNum, Subject subject) {
		this.studentNum = studentNum;
		this.subject = subject;
	}

	public Student() {};

}
```

<br>

```java
import java.util.ArrayList;

public class CalcRank {

	public ArrayList<Student> calcRanK(ArrayList<Student> list) {
		int[] sum = new int[3]; //석차 구하기
		int[] rank = new int[3];

		for (int i = 0; i < list.size(); i++) {
			sum[i] = (int) list.get(i).subject.getSum();
		}

		for (int i = 0; i < list.size(); i++) {
			rank[i] = 1; //기본 석차 1 지정
			for (int j = 0; j < sum.length; j++) {
				if (sum[i] < sum[j])
					++rank[i];
			}
		}
		for (int i = 0; i < list.size(); i++) {
			list.get(i).rank = rank[i]; //석차 대입
		}
		return list;
	}
}
```

<br>

```java
import java.util.ArrayList;

import 성주헌.subject.Subject;

public class Main {
	public static void main(String[] args) {
		ArrayList<Student> list = new ArrayList<Student>();

		list.add(new Student(1, 90, 90, 90));
		list.add(new Student(2, new Subject(88, 97, 90)));
		list.add(new Student(3, 70, 70, 70));

		for (int i = 0; i < list.size(); i++) {
			System.out.println(list.get(i).studentNum + "번 학생 : ");
			list.get(i).subject.showSubjectInfo();
			CalcRank cr = new CalcRank(); //calcRank 호출용 생성자
			System.out.println("석차 : " + cr.calcRanK(list).get(i).getRank());
			System.out.println();
		}

	}

}
```
