# 객체 지향 프로그래밍 기본 요소

---

## 1. 객체 지향 프로그래밍(OOP)

객체 지향 프로그래밍은 현실 세계의 개념을 코드로 모델링하는 패러다임이다. Dart에서는 클래스, 상속, 추상화, 다형성, 캡슐화 등의 OOP 개념을 지원한다.

### Rectangle 클래스 - 게터와 세터 활용

게터와 세터를 사용하면 클래스의 속성에 대한 접근과 수정을 제어할 수 있다. 이를 통해 데이터 유효성 검사, 계산된 값 반환 등이 가능하다.

```dart
class Rectangle {
  num left, top, width, height;
  
  Rectangle(this.left, this.top, this.width, this.height);
  
  num get right => left + width;
  set right(num value) => left = value - width;
  
  num get bottom => top + height;
  set bottom(num value) => top = value - height;
}

void main() {
  var r1 = Rectangle(5, 10, 20, 25);
  print([r1.left, r1.top, r1.width, r1.height]);
  print([r1.width, r1.height]);
}
```

---

### Hero와 SuperHero 클래스 - 상속과 메서드 오버라이드

상속을 통해 기존 클래스의 기능을 확장하고 메서드를 재정의할 수 있다. extends 키워드를 사용하여 클래스를 상속하고, @override 어노테이션으로 메서드 재정의를 명시한다.

```dart
class Hero {
  String name = '영웅';
  
  void run() {
    print('달다');
  }
}

class SuperHero extends Hero {
  @override
  void run() {
    super.run();
    this.fly();
  }
  
  void fly() {
    print('난다!');
  }
}

void main() {
  var hero = SuperHero();
  hero.run();
  print(hero.name);
}
```

---

### Monster 추상 클래스와 다형성

추상 클래스는 구현되지 않은 메서드를 선언할 수 있으며, 이를 상속받는 클래스에서 해당 메서드를 구현해야 한다. 다형성은 상위 타입 변수가 하위 타입 객체를 참조할 수 있게 해준다.

```dart
abstract class Monster {
  void attack();
}

class Goblin implements Monster {
  @override
  void attack() {
    print('고블린 어택!');
  }
}

class Bat implements Monster {
  @override
  void attack() {
    print('할퀴기!');
  }
}

void main() {
  var g1 = Goblin();
  var b1 = Bat();
  g1.attack();
  b1.attack();
  
  List<Monster> monsters = [g1, b1];
  monsters.forEach((m) => m.attack());
}
```

---

### Status 열거형과 switch문 활용

열거형은 제한된 상수 값의 집합을 정의할 때 유용하다. switch 문과 함께 사용하면 타입 안전성과 가독성이 향상된다.

```dart
enum Status { login, logout }

void main() {
  var authStatus = Status.logout;
  print(authStatus);
  
  switch (authStatus) {
    case Status.login:
      print('로그인');
      break;
    case Status.logout:
      print('로그아웃');
      break;
  }
}
```

---
