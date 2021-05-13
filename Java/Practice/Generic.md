```java
public class GenericPrinter<T> {
	private T material;
	
	public void setMaterial(T material) {
		this.material = material;
	}
	
	public T getMaterial() {
		return material;
	}
	
	public String toString() {
		return material.toString();
	}
}
```
<br></br>
```java
public class Powder {
	public void doPrinting() {
		System.out.println("Powder 재료로 출력합니다.");
	}
	public String toString() {
		return "재료는 Powder 입니다.";
	} //객체가 가진 정보나 값들을 문자열로 만들어 리턴
}
```
<br></br>
```java
public class Plastic {
	public void doPrinting() {
		System.out.println("Plastic 재료로 출력합니다.");
	}
	public String toString() {
		return "재료는 Plastic 입니다.";
	}
}
```
<br></br>
```java
public class GenericPrinterTest {
	public static void main(String[] args)	{
		GenericPrinter<Powder> powderPrinter = new GenericPrinter<Powder>();
							//powder형으로 GenericPrinter클래스 생성
		
		powderPrinter.setMaterial(new Powder());
		Powder powder = powderPrinter.getMaterial();
		System.out.println(powderPrinter);
		System.out.println(powder);
		
		GenericPrinter<Plastic> plasticPrinter = new GenericPrinter<Plastic>();
		
		plasticPrinter.setMaterial(new Plastic());
		Plastic plastic = plasticPrinter.getMaterial();
		System.out.println(plastic.toString());
		System.out.println(plastic);
	}
}
```
>재료는 Powder 입니다.<br></br>
>재료는 Powder 입니다.<br></br>
>재료는 Plastic 입니다.<br></br>
>재료는 Plastic 입니다.
