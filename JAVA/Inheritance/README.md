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

#### 서브 클래스 생성자의 첫줄에 super(...) 메서드를 명시적으로 선언하면 매개값에 따라 슈퍼 클래스의 생성자를 지정하여 호출할 수 있다.
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

    private void rest() {
        System.out.println("군인이 휴식을 취합니다.");
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
armySoldier.rest();         // private 메서드에 접근할 수 없어 컴파일 오류 발생.
```

<br>   

#### 오버라이딩(Overriding)은 슈퍼클래스 메서드를 서브클래스에서 재정의하는 과정이다. 
#### 서브클래스 객체에서 호출할 경우 슈퍼클래스의 메서드가 아니라 서브클래스의 메서드가 실행된다.

<br>   

#### 오버라이딩된 메서드는 시그니처(메서드 이름, 파라미터 리스트, 리턴 타입)가 동일해야 한다. 
#### 서브클래스에서는 슈퍼클래스의 final 메소드를 그대로 사용할 수 있지만, 오버라이딩할 수 없다.

<br>   

#### 접근 권한을 확장하여 오버라이딩할 수 있지만, 접근 권한을 축소하여 오버라이딩할 수 없다.
#### 예를 들어 public으로 선언된 메서드를 서브클래스에서 private로 오버라이딩해서는 안 된다.
#### 한편 private 메서드는 서브클래스에서도 직접 접근할 수 없으므로, 오버라이딩될 수 없다.

<br>   
<br>   
<br>   
<br>   

## 03. Upcasting

<br>   

```java
class Soldier {
    String hat = "군모";

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
    String hat = "베레모";
    int serviceMonth = 18;

    @Override
    public void drive() {
        System.out.println("육군이 탱크를 조종합니다.");
    }

    public void march() {
        System.out.println("육군이 행군을 합니다.");
    }
}
```

<br>   

```java
Soldier soldier = new ArmySoldier();
// ArmySoldier 객체를 Soldier 타입의 변수에 업캐스팅


System.out.println("모자: " + soldier.hat);
// 슈퍼클래스의 필드 출력 -> 모자 : 군모 

soldier.drive();
// 서브클래스의 오버라이딩된 메소드 호출 -> 육군이 탱크를 조종합니다.

soldier.shoot();
// 슈퍼클래스의 메소드 호출 -> 군인이 총을 쏩니다.


System.out.println("복무 개월 : " + soldier.serviceMonth);
// 서브클래스의 필드 접근 불가 -> 컴파일 에러

soldier.march();
// 서브클래스의 메소드 호출 불가 -> 컴파일 에러
```

<br>   

#### 서브클래스 객체를 슈퍼클래스 타입으로 형변환(업캐스팅)하면 슈퍼클래스 타입으로 서브클래스 객체를 다룰 수 있게 된다.
#### 업캐스팅된 변수로는 슈퍼클래스에 정의된 멤버들에만 접근할 수 있지만, 서브클래스에 추가된 멤버들에는 접근할 수 없다. 
#### 그러나 서브클래스에서 오버라이딩된 메서드가 존재할 경우 
#### 슈퍼클래스 타입의 변수를 통해 해당 메서드를 호출하면 서브클래스의 메서드가 실행된다.
