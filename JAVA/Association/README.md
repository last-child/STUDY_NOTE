## 01. Association

<br>   

```java
class Driver {
    private String driverName;

    Driver(String name) {
        this.driverName = name;
    }

    public void replaceDriver(Driver newDriver) {
        this.driver = newDriver;
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
    private Driver driver;

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

#### Association은 두 클래스 간의 연결을 나타낸다. 
#### 한 클래스의 객체는 다른 클래스의 객체를 참조할 수도 있고, 다른 클래스의 객체로부터 참조될 수도 있다.
#### 하지만 객체 간의 연결이 느슨하기 때문에 한 객체의 상태 변화가 반드시 다른 객체에 영향을 미치는 것은 아니다.

<br>   

#### 예를 들어 Car 객체가 Driver 객체를 참조하지만, Car 객체가 소멸되어도 Driver 객체는 그대로 남아있을 수 있다.
#### 또한 Driver 클래스의 코드를 수정해도 Car 객체의 기능에 영향을 미치지 않는다.
#### Association에서 참조가 동적으로 변경될 수 있다. 즉 Car 객체는 Driver 객체를 유연하게 교체할 수 있다. 

<br>   
<br>   
<br>   
<br>   

## 02. Aggregation

<br>   

```java
class Engine {
    private String engineType;

    Engine(String type) {
        this.engineType = type;
    }

    public String getEngineType() {
        return engineType;
    }
}
```

<br>   

```java
class Car {
    private String model;
    private Engine engine;

    Car(String model, Engine engine) {
        this.model = model;
        this.engine = engine;
    }

    public void replaceEngine(Engine newEngine) {
        this.engine = newEngine;
    }

    public void getCarDetails() {
        System.out.println("자동차 모델 : " + model);
        System.out.println("자동차 엔진 : " + engine.getEngineType());
    }
}
```

<br>   

```java
public class AggregationExample {
    public static void main(String[] args) {
        Engine engine = new Engine("V8");
        Car car = new Car("Ford Mustang", engine);
        car.getCarDetails();
    }
}
```
<br>   

#### Aggregation은 전체와 부분의 관계를 나타내지만, 전체 객체와 부분 객체는 독립적으로 존재할 수 있다. 
#### 전체 객체와 부분 객체는 느슨하게 결합되어 있어 부분 객체를 유연하게 교체하거나, 부분 객체의 코드를 자유롭게 수정할 수 있다. 

<br>   

#### 예를 들어 Car 클래스는 Engine 클래스의 인스턴스를 가지고 있다. 
#### 하지만 Car는 Engine의 생명주기에 의존적이지 않으므로 Engine 객체가 Car 객체 없이도 존재할 수 있다. 
#### 또한 두 객체는 느슨하게 결합되기 때문에 Car 객체는 Engine 객체를 유연하게 교체할 수 있다. 
