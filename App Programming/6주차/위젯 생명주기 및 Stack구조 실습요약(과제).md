# 위젯 생명주기 및 Stack 구조 실습 요약

---

Flutter의 상태 기반 위젯(`StatefulWidget`)에서 **생명주기(lifecycle)**의 흐름을 명확히 이해하는 것을 목표로 한다.  
또한 `Navigator.push()`와 `Navigator.pop()`을 통해 화면 전환이 발생할 때, **각 위젯의 생명주기 메서드가 어떤 순서로 호출되는지**를 출력 로그를 통해 직접 확인할 수 있도록 구성되어 있다.

즉, 화면이 생성될 때 호출되는 `initState()`, 다시 그려질 때 호출되는 `build()`, 그리고 화면이 종료될 때 호출되는 `dispose()`를 실제 실행 로그를 통해 확인하며  
Flutter가 **상태 변화에 따라 위젯을 어떻게 관리하는지 학습**하는 데 목적이 있다.

---

### 주요 생명주기 메서드 정리

- `initState()`  
  → 위젯이 처음 생성될 때 단 한 번 호출된다.  
  → 데이터를 초기화하거나 리소스를 연결할 때 주로 사용됨.

- `dispose()`  
  → 위젯이 화면에서 제거될 때 호출된다.  
  → 리소스 해제, 컨트롤러 정리 등에 사용됨.

- `build()`  
  → 위젯이 화면에 나타날 때마다 호출된다.  
  → 화면 UI를 구성하는 메서드로, `setState()` 호출 시에도 다시 실행됨.

---

### 화면 전환 흐름 및 생명주기 순서

#### 1. 앱 첫 실행 시

- `MyHomePage`의 `initState()` → `build()`가 순서대로 호출됨  
- 이는 첫 번째 화면이 생성되고 표시될 때 호출되는 메서드 흐름임

#### 2. 다음 페이지로 전환 (`push` 호출)

- `NextPage`의 `initState()` → `build()`가 호출됨  
- 이와 동시에 `MyHomePage`의 `build()`도 한 번 더 호출됨  
- 이유는 Navigator가 새로운 페이지를 push하면 기존 위젯도 rebuild되기 때문

#### 3. 뒤로 가기 (`pop` 호출)

- `NextPage`의 `dispose()`가 호출되어 해당 페이지가 메모리에서 제거됨  
- 다시 돌아온 `MyHomePage`의 `build()`가 호출됨

#### 4. 앱 종료 시

- `MyHomePage`의 `dispose()`가 마지막으로 호출됨

---

### 생명주기 관련 코드 요약

```dart
@override
void initState() {
  super.initState();
  print("페이지 - initState()");
}

@override
Widget build(BuildContext context) {
  print("페이지 - build()");
  return Scaffold(
    // ... UI 구성 ...
  );
}

@override
void dispose() {
  print("페이지 - dispose()");
  super.dispose();
}
```

---

### 실습 정리 요약

- 화면이 처음 로딩될 때 `initState()` → `build()`가 호출된다.  
- 다른 페이지로 전환 시, 새 페이지의 `initState()`와 `build()`가 호출되며 기존 페이지의 `build()`도 재실행된다.  
- 페이지가 제거될 땐 `dispose()`가 호출된다.  
- 이를 통해 **화면 전환과 상태 변화에 따른 위젯의 생명주기 흐름**을 정확히 확인할 수 있다.

---
