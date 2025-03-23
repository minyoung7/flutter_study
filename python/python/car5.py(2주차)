#자동차 경주 프로그램 

from turtle import *        # turtle 모듈 불러오기 
import random               # random 모듈 불러오기 

# 자동차 클래스 만들기 
class Car:
    def __init__(self, speed, color, fname, locate, goal):  # 자동차가 생성될 때 필요한 정보들
        self.speed = speed              # 자동차 기본 속도 저장
        self.color = color              # 자동차 색상 저장 (지금은 따로 쓰지 않음)
        self.turtle = Turtle()          # 자동차 모양을 그릴 turtle 객체 만들기
        self.turtle.shape(fname)        # 자동차 모양 설정 (이미지 파일로 설정)
        self.turtle.speed(self.speed)   # 자동차의 움직이는 속도 설정
        self.locate = locate            # 현재 x 위치를 저장 (경주 중 계속 업데이트됨)
        self.goal = goal                # 결승선 도착 여부 저장 (1이면 도착)

    def drive(self, distance):          # 자동차 앞으로 이동시키는 함수
        self.turtle.forward(distance)   # 지정된 거리만큼 전진

    def goto(self, x, y):               # 자동차 위치를 특정 좌표로 이동시키는 함수
        self.turtle.goto(x, y)

    def turnleft(self, degree):        # 자동차를 왼쪽으로 회전시키는 함수 (지금은 사용 안 함)
        self.turtle.left(degree)

    def write(self, write):            # 글씨를 출력하는 함수 (몇 등인지 화면에 표시)
        self.turtle.write(write)

    def hide(self):                    # 자동차를 숨기는 함수 (도착하면 화면에서 사라지게 하기 위해 사용)
        self.turtle.hideturtle()


register_shape("car2.gif")  # 자동차 모양으로 이미지 등록

car_list = []    # 자동차 객체들을 저장할 리스트
y = -100         # 각 자동차의 시작 y좌표 설정 (자동차끼리 겹치지 않게)
n = 0            # 결승선 도착한 순서를 저장할 변수 (몇 번째 도착인지)

# 자동차 3대를 생성해서 리스트에 넣기
for i in range(3):
    car_list.append(Car(10, "red", "car2.gif", -400, 0))  # 속도 10, 빨간색, car2.gif 모양, 출발 위치 -400, 도착 여부 0

# 자동차들을 출발선 위치로 이동시키기
for car in car_list:
    car.turtle.penup()         # 이동할 때 선 그리지 않게 설정
    car.goto(-400, y)          # 자동차 위치 이동 (x: -400, y: 각각 다르게)
    car.turtle.pendown()       # 다시 선 그리기 상태로 (실제 경주에서는 영향 없음)
    y += 100                   # 다음 자동차는 더 아래에 위치하도록 y값 증가


for i in range(400):   # 자동차 경주 시작 (400번 반복해서 자동차들을 계속 움직임)
    for car in car_list:       # 모든 자동차에 대해 반복
        speed = random.randint(2, 20)    # 매번 랜덤한 속도로 이동 (2~20 사이)

        if car.locate < 400:            # 아직 결승선(x=400)에 도착 안 했으면
            if car.locate + speed >= 400:    # 다음 이동에서 결승선을 넘을 경우
                speed = 400 - car.locate     # 정확히 결승선까지 속도 조정
                n += 1                       # 순위 증가 (몇 번째 도착인지)
                car.goal = 1                 # 이 자동차는 도착했다는 표시
                car.hide()                   # 도착했으니 자동차 숨기기

            car.drive(speed)                 # 자동차 실제로 앞으로 이동

            if car.goal == 1:                # 도착한 자동차라면
                car.write(str(n) + "등")     # 몇 등인지 화면에 글씨로 보여주기

        car.locate += speed                  # 자동차의 위치 정보 업데이트
