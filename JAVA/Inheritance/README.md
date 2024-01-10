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
        this.division = "훈련소";
        System.out.println("육군 인스턴스의 부대 : " + division);
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

## 02. Method Overriding

<br>   

```java
class Soldier {
    public void drive() {
        System.out.println("군인이 차량을 조종합니다.");
    }

    public void shoot() {
        System.out.println("군인이 총을 쏩니다.");
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

    public void march() {
        System.out.println("육군이 행군을 합니다.");
    }

    public void superDrive() {
        super.drive(); // 슈퍼클래스의 drive() 메서드 호출
    }
}
```

<br>   

```java
ArmySoldier armySoldier = new ArmySoldier();

armySoldier.drive();        // 육군이 탱크를 조종합니다. (오버라이딩한 메서드)
armySoldier.shoot();        // 군인이 총을 쏩니다. (오버라이딩하지 않은 메서드)
armySoldier.march();        // 육군이 행군을 합니다. (서브클래스 고유 메서드)
armySoldier.superDrive();   // 군인이 차량을 조종합니다. (슈퍼클래스 메서드 호출)
```

<br>   

#### 오버라이딩(Overriding)은 슈퍼클래스 메서드를 서브클래스에서 재정의하는 과정이다. 
#### 서브클래스 객체에서 호출할 경우 슈퍼클래스의 메서드가 아니라 서브클래스의 메서드가 실행된다.

<br>   

#### 오버라이딩된 메서드는 시그니처(메서드 이름, 파라미터 리스트, 리턴 타입)가 동일해야 한다. 
#### final 메서드는 상속되지 않기 때문에, 서브클래스에서 오버라이딩할 수 없다.

<br>   

#### 접근 권한을 확장하여 오버라이딩할 수 있지만, 접근 권한을 축소하여 오버라이딩할 수 없다.
#### 예를 들어 public으로 선언된 메서드를 서브클래스에서 private로 오버라이딩해서는 안 된다.
#### private로 선언된 메서드는 서브클래스에서도 직접 접근될 수 없으므로, 오버라이딩될 수 없다.
