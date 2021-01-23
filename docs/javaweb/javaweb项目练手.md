# JavaWeb 练手项目

## 开发以及运行环境
>jdk 1.8    
maven 3.6.3    
tomcat 8.5.45     
junit 4.11      
servlet  4.0.1     
jsp 2.3.3    
mysql  5.7   



## 实体类

### Bus

```java
public class Bus {

	public int Bus_id;
	public String Bus_type;
	public String Route;
	public Double money;
	
	public Bus() {
		super();
	}

	public Bus(int bus_id, String bus_type, String route, Double money) {
		super();
		Bus_id = bus_id;
		Bus_type = bus_type;
		Route = route;
		this.money = money;
	}

	public int getBus_id() {
		return Bus_id;
	}

	public void setBus_id(int bus_id) {
		Bus_id = bus_id;
	}

	public String getBus_type() {
		return Bus_type;
	}

	public void setBus_type(String bus_type) {
		Bus_type = bus_type;
	}

	public String getRoute() {
		return Route;
	}

	public void setRoute(String route) {
		Route = route;
	}

	public Double getMoney() {
		return money;
	}

	public void setMoney(Double money) {
		this.money = money;
	}

	@Override
	public String toString() {
		return "Bus [Bus_id=" + Bus_id + ", Bus_type=" + Bus_type + ", Route=" + Route + ", money=" + money + "]";
	}
	
}
```