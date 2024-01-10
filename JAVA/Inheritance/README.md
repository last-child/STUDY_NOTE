## 01. Inheritance and Constructor

<br>   

```java
class Soldier {
    private String serviceNumber;

    // 슈퍼 클래스의 생성자
    public Soldier(String serviceNumber) {
        this.serviceNumber = serviceNumber;
        System.out.println("군인 인스턴스의 군번 : " + serviceNumber);
    }
}
```

<br>   

```java
class ArmySoldier extends Soldier {
    private String division;

    // 서브 클래스의 생성자
    public ArmySoldier(String serviceNumber, String division) {
        super(serviceNumber); // 슈퍼 클래스의 생성자 호출
        this.division = division;
        System.out.println("육군 인스턴스의 부대 : " + division);
    }

    public ArmySoldier(String serviceNumber) {
        // super( );
        System.out.println("육군 인스턴스의 부대 : " + 훈련소);
    }
}
```

<br>   

```java
ArmySoldier armySoldier = new ArmySoldier("24-12345678", "1사단");

// 군인 인스턴스의 군번 : 24-12345678
// 육군 인스턴스의 부대 : 1사단

ArmySoldier armySoldier = new ArmySoldier("24-12345678");

// 해당 생성자의 바이트코드에 super( )가 자동으로 추가됨.
// 하지만 슈퍼 클래스에 기본 생성자가 없어서 컴파일 오류가 발생함.
```

<br>   

#### 서브 클래스 생성자를 호출하면 서브 클래스 생성자의 바이트코드 첫줄에 슈퍼 클래스의 기본 생성자가 자동으로 추가된다. 
#### 따라서 서브 클래스 생성자를 호출하면 슈퍼 클래스 생성자가 먼저 실행되기 때문에  
#### 슈퍼 클래스의 인스턴스가 먼저 생성되고, 그 다음에 서브 클래스의 인스턴스가 생성된다.

<br>   

#### 서브 클래스 생성자의 첫줄에 super(...) 메서드를 명시적으로 선언하면 매개값에 따라 슈퍼 클래스의 특정 생성자를 호출할 수 있다.
#### 하지만 매개값 타입과 일치하는 슈퍼 클래스 생성자가 없을 경우 컴파일 오류가 발생한다.

<br>   
<br>   
<br>   
<br>   

## 02. Overriding

<br>   

```java
class Soldier {
    public void drive() {
        System.out.println("군인이 차량을 조종합니다.");
    }
}
```

<br>

```java
class ArmySoldier extends Soldier {
    @Override
    public void drive() {
        System.out.println("육군이 탱크를 조종합니다.");
    }
}

class NavySoldier extends Soldier {
    @Override
    public void drive() {
        System.out.println("해군이 함정을 조종합니다.");
    }
}

class AirForceSoldier extends Soldier {
    @Override
    public void drive() {
        System.out.println("공군이 전투기를 조종합니다.");
    }
}
```
