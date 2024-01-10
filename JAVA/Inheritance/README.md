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
