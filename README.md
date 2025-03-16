## 진행 결과
- Flutter SDK 설치
- 환경 변수 설정
- Android Studio에 Flutter, Dart 플러그인 설치 완료
- 새 프로젝트 생성 (hello_flutter)
- 기본 카운터 앱 Chrome에서 정상 실행됨
- 버튼 클릭 시 숫자 증가 확인
- "Hello World"를 출력하기
- import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        body: Center(
          child: Text(
            'Hello World',
            style: TextStyle(fontSize: 30),
          ),
        ),
      ),
    );
  }
}


## 실행 화면 캡처
![실행 화면](실행결과.JPG)

## 실행 화면 캡처
![실행 화면](실행결과2.JPG)
