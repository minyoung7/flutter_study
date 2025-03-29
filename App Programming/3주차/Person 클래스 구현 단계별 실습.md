# Person 클래스 단계별 실습

---

### 실습 1: 기본 Person 클래스 - 공개 필드

가장 기본적인 형태의 클래스로, 공개 필드와 간단한 메서드를 가집니다. 객체를 생성하고 속성에 직접 접근합니다.

```dart
class Person {
  String name = "";
  int age = 0;

  void addOneYear() {
    age++;
  }
}

void main() {
  var na = Person();
  na.name = '이민영';
  na.age = 24;
  print([na.name, na.age]);
}
```

---

### 실습 2: 직접 나이 증가

공개 필드의 값을 직접 수정하는 방식으로 나이를 증가시킵니다. 나이가 24에서 25로 변경됩니다.

```dart
class Person {
  String name = "";
  int age = 0;

  void addOneYear() {
    age++;
  }
}

void main() {
  var na = Person();
  na.name = '이민영';
  na.age = 24;
  print([na.name, na.age]);

  na.age++;
  print([na.name, na.age]);
}
```

---



### 실습 4: 비공개 필드와 게터 도입

비공개 필드(_name, _age)와 게터를 도입했지만 세터가 없어서 속성 할당 시 오류가 발생합니다.

```dart
class Person {
  String _name;
  int _age;

  String get name => _name;
  int get age => _age;
}

void main() {
  var na = Person();
  na.name = '이민영'; // 오류
  na.age = 24;       // 오류
  print([na.name, na.age]);
}
```

---

### 실습 5: 잘못된 생성자 사용

비공개 필드, 게터만 있는 클래스에 생성자를 통한 초기화를 시도하지만, 해당 생성자가 정의되지 않아 오류가 발생합니다.

```dart
class Person {
  String _name;
  int _age;

  String get name => _name;
  int get age => _age;
}

void main() {
  var na = Person('이민영', 24); // 오류
  na.name = '이민영'; // 오류
  na.age = 24;       // 오류
  print([na.name, na.age]);
}
```

---

### 실습 6: 초기화되지 않는 생성자

생성자를 선언했지만 매개변수를 필드에 할당하지 않아 객체의 필드는 초기값을 유지합니다. 출력 결과는 빈 문자열과 0입니다.

```dart
class Person {
  String _name = "";
  int _age = 0;

  Person(String _name, int _age);

  void addOneYear() {
    _age++;
  }

  String get name => _name;
  int get age => _age;
}

void main() {
  var na = Person('이민영', 24);
  print([na.name, na.age]); // [, 0]

  print([na.name, na.age]); // [, 0]
}
```

---

### 실습 7: this를 사용한 올바른 생성자

this 키워드를 사용하여 생성자 매개변수를 비공개 필드에 올바르게 할당합니다. 출력 결과는 [이민영, 24]입니다.

```dart
class Person {
  String _name;
  int _age;

  Person(this._name, this._age);

  void addOneYear() {
    _age++;
  }

  String get name => _name;
  int get age => _age;
}

void main() {
  var na = Person('이민영', 24);
  print([na.name, na.age]); // [이민영, 24]
}
```

---

### 실습 8: 메서드 호출로 나이 증가

addoneYear() 메서드를 호출하여 나이를 증가시킵니다. 출력 결과는 [이민영, 24]와 [이민영, 25]입니다.

```dart
class Person {
  String _name;
  int _age;

  Person(this._name, this._age);

  void addoneYear() {
    _age++;
  }

  String get name => _name;
  int get age => _age;
}

void main() {
  var na = Person('이민영', 24);
  print([na.name, na.age]); // [이민영, 24]

  na.addoneYear();
  print([na.name, na.age]); // [이민영, 25]
}
```

---

### 실습 9: 설명 필드 추가

_desc 필드와 해당 게터/세터를 추가했습니다. 생성자에서 세 번째 인수로 설명을 받습니다.

```dart
class Person {
  String _name;
  int _age;
  String _desc;

  Person(this._name, this._age, this._desc);

  void addOneYear() {
    _age++;
  }

  String get name => _name;
  int get age => _age;
  String get desc => _desc;
  set desc(String v) => _desc = v;
}

void main() {
  var na = Person('이민영', 24, '이민영은 이민영이다.');
  print([na.name, na.age, na.desc]); // [이민영, 24, 이민영은 이민영이다.]
}
```

---


```

---

