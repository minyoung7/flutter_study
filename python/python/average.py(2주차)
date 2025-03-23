#리스트를 이용한 최고점,최서점,평균 구하는 프로그램 

# 평균 점수를 구하는 함수
def avgfunc(scores):
    return sum(scores) / len(scores)  # 점수 총합을 개수로 나눠서 평균 계산

# 최고 점수를 구하는 함수
def maxfunc(scores):
    return max(scores)  # 리스트에서 가장 높은 점수 반환

# 최저 점수를 구하는 함수
def minfunc(scores):
    return min(scores)  # 리스트에서 가장 낮은 점수 반환

# 점수를 저장할 리스트 만들기
scores = []

# 5명의 점수 입력받기
for i in range(5):
    score = float(input(f"{i+1}번째 점수를 입력하세요: "))  # 실수형 점수 입력받음
    scores.append(score)  # 리스트에 추가

# 입력한 점수 전체 출력
print("\n입력된 5명의 점수:", scores)

# 메뉴 선택 반복 실행
while True:
    # 사용자에게 메뉴 보여주기
    print("\n메뉴를 선택하세요 ▶ 종료(0), 최고점(1), 최소점(2), 평균값(3)")
    select = input("선택: ")

    if select == "0":
        # 0을 입력하면 프로그램 종료
        print("프로그램을 종료합니다.")
        break

    elif select == "1":
        # 최고점 출력
        print(f"5명 중 최고 점수는 {maxfunc(scores)}점 입니다.")

    elif select == "2":
        # 최저점 출력
        print(f"5명 중 최저 점수는 {minfunc(scores)}점 입니다.")

    elif select == "3":
        # 평균값 출력 (소수점 둘째 자리까지 표시)
        print(f"5명의 평균 점수는 {avgfunc(scores):.2f}점 입니다.")

    else:
        # 잘못된 번호를 입력한 경우
        print("잘못 입력하셨습니다. 0~3 중에서 선택해주세요.")
