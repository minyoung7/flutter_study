## 2. 데이터 구조와 컬렉션

Dart는 리스트, 맵, 셋 등 다양한 컬렉션 타입을 제공하며, 이를 통해 데이터를 효율적으로 관리하고 조작할 수 있다.

### 리스트 생성 및 메서드 활용

리스트는 순서가 있는 요소의 컬렉션이다. Dart에서는 대괄호 []를 사용해 리스트를 생성하고, 다양한 메서드로 요소를 추가, 제거, 검색할 수 있다.

```dart
void main() {
  var l1 = [1, 2, 3, 4, 5, 6];
  var l2 = ['가', '나', '다', '라', '마', '바'];
  print(l1);
  print(l2);

  l1.add(7);
  print(l1);

  l1.remove(2);
  print(l1);

  print(l1[0]);
  print(l1.length);
  print(l1.contains(4));
}
```

---

### 맵(Map)과 셋(Set) 사용법

맵은 키-값 쌍의 컬렉션이고, 셋은 중복이 없는 요소의 컬렉션이다. 둘 다 중괄호 {}로 리터럴을 생성한다.

```dart
void main() {
  var m1 = {'한국': '서울', '일본': '도쿄'};
  print(m1);
  print(m1['한국']);

  m1['중국'] = '북경';
  print(m1);

  print(m1.containsKey('미국'));
  m1.forEach((key, value) => print('$key의 수도는 $value'));

  var s1 = {1, 2, 3, 3, 3, 3, 4, 5};
  print(s1);

  s1.add(6);
  print(s1);

  s1.add(6);
  print(s1);

  var s2 = {4, 5, 6, 7, 8};
  print(s1.union(s2));
  print(s1.intersection(s2));
}
```

---

## 3. 함수형 프로그래밍

Dart에서는 함수가 일급 객체이며, 이를 활용한 함수형 프로그래밍이 가능하다. 함수를 변수에 할당하거나 다른 함수의 인자로 전달할 수 있다.

### 함수를 변수에 할당하고 인자로 전달

```dart
void func_a() {
  print('왼쪽!');
}

void func_b() {
  print('오른쪽!');
}

void main() {
  var fun = func_a;
  fun();

  fun = func_b;
  fun();

  var list = [1, 2, 3, 4, 5];
  list.forEach(print);
}
```

---

### 고차 함수와 익명 함수

고차 함수는 다른 함수를 인자로 받거나 함수를 반환하는 함수이다. 익명 함수(람다)는 이름 없이 즉석에서 정의되는 함수이다.

```dart
void main() {
  var numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];

  var evenNumbers = numbers.where((n) => n % 2 == 0);
  print(evenNumbers);

  var squaredNumbers = numbers.map((n) => n * n);
  print(squaredNumbers);

  var sum = numbers.reduce((value, element) => value + element);
  print(sum);

  var sumOfSquaredOdds = numbers
    .where((n) => n % 2 != 0)
    .map((n) => n * n)
    .reduce((sum, n) => sum + n);

  print(sumOfSquaredOdds);
}
```

---

### 클로저(Closure)

클로저는 자신을 둘러싼 환경의 변수를 캡처하는 함수이다. Dart에서 모든 함수는 클로저이다.

```dart
Function makeAdder(int addBy) {
  return (int i) => addBy + i;
}

void main() {
  var add2 = makeAdder(2);
  var add4 = makeAdder(4);

  print(add2(3));
  print(add4(3));
}
```

---
