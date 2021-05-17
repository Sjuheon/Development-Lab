```java
interface PrintString	{
	void showString(String str);
}

public class LambdaTest {
	public static void main(String[] args)	{
		PrintString lambdaStr = s -> System.out.println(s);
		lambdaStr.showString("Hello World");
		showMyString(lambdaStr);
	}
	public static void showMyString(PrintString p)	{
		p.showString("Hello Universe");
	}
}
```
> Hello World <br>
> Hello Universe
