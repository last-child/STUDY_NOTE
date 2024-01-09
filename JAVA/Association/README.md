## 01. Association

<br>   

```java
class Driver {
    private String driverName;

    Driver(String name) {
        this.driverName = name;
    }

    public String getDriverName() {
        return driverName;
    }
}
```

<br>   

```java
class Car {
    private String carName;
    private Driver driver; // Car has-a Driver

    Car(String name, Driver driver) {
        this.carName = name;
        this.driver = driver;
    }

    public void getCarDetails() {
        System.out.println("자동차 이름 : " + carName);
        System.out.println("운전자 이름 : " + driver.getDriverName());
    }
}
```

<br>   

```java

public class AssociationExample {
    public static void main(String[] args) {
        Driver driver = new Driver("Sejin");
        Car car = new Car("Toyota", driver);
        car.getCarDetails();
    }
}
```

<br>   
<Br>   

![image](https://github.com/last-child/STUDY_NOTE/assets/98595054/3af91ee4-9a3d-4397-a568-df5ff8fe69d0)
