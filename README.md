# 30 함수에서 위치 인수와 키워드 인수 사용하기 

## 인수의 종류 알기

### 1. 위치 인수란 
- 함수에 인수를 순서대로 넣는 방식을 위치 함수 
- 예시 코드
```
def print_mi,ners(a, b, c):
    print(a)
    print(b)
    print(c)

print_numbers(10, 20 ,30)
```
이렇게 출력함수를 만들고 함수에 숫자를 작성하면 숫자가 출력되는 것
### 2. 가변 인수란
- 인수의 개수가 정해지지 않은 것이 가변 인수이다
즉 함수에 개수가 1개 10개 또는 없을 수도 있다
- 예시 코드
```
def print_numbers(*args):
    for arg in args:
         print(arg)

print_numbers(10) or print_numbers(10, 20, 30, 40)
```
- 예시 코드에서 이 *args의 별( *)사용 방식에 따라 또 코드가 바뀝니다
이 별( *)이 두번 사용될때도 있는데 왜 두번 사용하냐면 이 딕셔너리는 키-값 쌍 형대로 저장되기에 두번( **) 사용하면 언페킹하여 값을 사용한다는 뜻으로도 사용 됩니다 이것을 키워드 인수로 예시를 들자면
- **의 예시 코드
```
앞에 함수를 먼저 만든 후

*를 한개만 사용했을때
x = {'name': '홍길동', 'age': 30, 'address': '서울시 용산구'}
personal_info(*x)
결과
이름:  name
나이:  age
주소:  address

**를 두개를 사용했을때
x = {'name': '홍길동', 'age': 30, 'address': '서울시 용산구'}
personal_info(**x)
결과
이름:  홍길동
나이:  30
주소:  서울시 용산구
```
 ### 3. 키워드 인수란 
 - 다른 인수들의 단점이 값을 그대로 넣어서 각각들의 인수들이 무슨 용도인지 알지 못했지만 키워드 인수는 예를 들어서 이름 , 나이 주소 등 세부사항을 작성하여 인수의 순서와 용도가 매번 기억하지 않도록 명확하게 보여줍니다
 - 예시 코드
```
def personal_info(name, age, address):
    print('이름: ', name)
    print('나이: ', age)
    print('주소: ', address)

personal_info('홍길동', 30, '서울시 용산구 000')
```

## 심화문제: 가장 낮은 점수, 높은 점수와 평균점수를 구하는 함수 만들기

### 1. 위치인수 코드 작성 규칙
- 점수 4개를 입력받음
- 점수가 입력되면 낮은 점수, 높은 점수, 평균점수 순으로 계산하여 출력함
- 4개의 편균을 구했다면 예를 들어서 영어, 과학 2개의 낮은 점수, 높은 점수, 평균점수를 구함
- 이렇게 결과에 4개의 낮음, 높음, 평균의 결과와 2개의 낮음, 높음, 평균 결과가 나옴

### 2. 작성시 시행착오
- 낮음, 높음, 평균의 결과값의 코드는 쉽게 작성할수 있었지만 **함수의 사용 미숙함**에 있어 *args에서 별표**를 더 써야 하는 것을 알지 못했다
- **반문환을 잘못 사용**하여 **산술식에 오류**가 생김

### 3. 실제 구현 내용
- 국어 영어 수학 과학 숫자를 4개 뛰여쓰기로 구분하여 작성
- 4개의 숫자를 낮음 높음 평균 순으로 계산하여 출력
- 2개의 숫자 영어 과학의 숫자의 똑같이 낮음 높음 평균 순으로 계산하여 출력

### 전체 코드 정리
```
korean, english, mathematics, science = map(int, input('국어 영어 수학 과학:').split())

def get_min_max_score(*args):
    return min(args), max(args)
def get_average(**args):
    return sum(args.values())/len(args)
    
    
min_score, max_score = get_min_max_score(korean, english, mathematics, science)
average_score = get_average(korean=korean, english=english, mathematics=mathematics, science=science) 
print('낮은 점수: {0:.2f}, 높은 점수: {1:.2f}, 평균 점수: {2:.2f}'.format(min_score, max_score, average_score))

min_score, max_score = get_min_max_score(english, science)
average_score = get_average(english=english, science=science)
print('낮은 점수: {0:.2f}, 높은 점수: {1:.2f}, 평균 점수: {2:.2f}'.format(min_score, max_score, average_score))
```
