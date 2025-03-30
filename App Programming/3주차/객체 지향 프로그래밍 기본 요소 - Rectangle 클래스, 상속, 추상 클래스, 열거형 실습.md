## 객체 지향 프로그래밍 - Rectangle 클래스, 상속, 추상 클래스, 열거형 실습

### Rectangle 클래스 - 게터와 세터 활용

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
  print(r1.right);
  r1.right = 30;
  print(r1.left);
}
```

---

### Hero와 SuperHero 클래스 - 상속과 메서드 오버라이드

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
  
  if (authStatus == Status.logout) {
    print('로그인이 필요합니다.');
  }
}
```

---
