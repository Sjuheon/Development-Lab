```java
public class Address {
	protected String name;
	private String address;
	
	public String showAddress()	{
		return "Name : " +  name + "\n" + "Address : " + address;
	}
	
	public String getName() {
		return name;
	}


	public String getAddress() {
		return address;
	}


	public Address() {
		super();
	}
	
	public Address(String name, String address) {
		this.name = name;
		this.address = address;
	}

	public void setName(String name) {
		this.name = name;
	}

	public void setAddress(String address) {
		this.address = address;
	}

}
```

<br>

```java
import java.util.ArrayList;

public class AddrBook {
	public static void main(String[] args)	{
		ArrayList<Address> list = new ArrayList<Address>(3);
		Address sam = new Address("Sam", "Daegu");
		Address dan = new Address();
		
		list.add(sam);
		list.add(new Address("Dan", "Daegu"));
		
		for(int i = 0; i < list.size(); i++)	{
			System.out.println(list.get(i).showAddress());
			System.out.println();
		}
	}

}
```

> Name : Sam <br>
Address : Daegu <br><br>
 Name : Dan <br>
Address : Daegu
