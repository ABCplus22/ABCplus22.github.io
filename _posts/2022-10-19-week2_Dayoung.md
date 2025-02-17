---
layout: post
title: 2주차 활동일지_정다영
subtitle:
categories: Week_02
tags: #Dayoung
---
## 두 번째 활동 일지
**일시 :** 2022.10.19 16:00~18:30  
**작성자 :** 콘텐츠IT전공 20215238 정다영   
**학습 목표 :** 함수와참조  

**주요학습내용**
- 함수 인자 전달 방식
- 참조 rvalue % lvalue
- 복사 생성자
- Move Semantics  

**오늘의 학습 계획**
1. Ch05_함수와참조 수업자료 ppt 공부
2. 7주차 실습 문제 코딩  
3. 학습 평가
### 요약 정리   

#### 함수 인자 전달 방식   

##### 값에 의한 호출(call by value)  
함수를 호출하는 쪽에서 객체 전달한다.

-호출하는 쪽의 객체가 매개 변수 객체에 그대로 복사된다.   
-매개 변수 객체의 생성자는 호출되지 않는다(함수 종료시 객체의 소멸자는 호출됨)   
 (why?) -> 호출되는 순간의 실 인자 객체 상태를 매개 변수 객체에 그대로 전달하기 위해   
 
#####주소에 의한 호출(call by address)  
함수 호출 시 객체의 주소 전달한다.

-함수의 매개 변수는 객체에 대한 포인터 변수로 선언된다.
-함수 호출 시 생성자/소멸자가 실행되지 않는다.

#### 참조 rvalue % lvalue

1. 참조 매개변수로 이루어진 연산은 원본 객체에 대한 연산된다.   
2. 참조 매개변수는 이름만 생성되고, 생성자와 소멸자는 실행되지 않는다.   

##### Lvalue  
 변수처럼 이름과 주소를 가진 대상(지속되는 객체)   
##### Rvalue   
 리터럴, 임시객체처럼 더 이상 존재하지 않는 임시적인 객체   


#### 복사 생성자(copy constructor)
객체의 복사 생성시 호출되는 특별한 생성자   

-한 클래스에 오직 한 개만 선언 가능하다   
-복사 생성자는 보통 생성자와 클래스 내에 중복 선언 가능하다    
-클래스에 대한 참조 매개 변수를 가지는 생성자 모양이다   
cf.복사 생성자가 선언되어 있지 않는 클래스 : 컴파일러가 자동으로 디폴트 복사 생성자를 삽입시켜준다

#### Move Semantics  
임시 객체(Rvalue)는 복사가 아닌 이동 되는 것이 상식적 이나 C++11에 객체의 이동이라는 개념이 도입되었다.   

##### Move Semantics 구현   
-이동 생성자와 이동 대입 연산자 구현한다.
-Rvalue Reference를 파라미터로 받는 함수 작성한다.
-컨테이너에 객체를 삽입할 때 더 이상 포인터를 넣지 않아도 된다.
-vector 컨테이너와 같은 대규모 리소스를 반환하는 함수 작성 가능하다.

### 학습 평가   

함수의 인자 전달방식을 값으로 받는 방법, 주소로 받는 방법, 참조로 받는 방법에 대해 알게 되었다.   
그렇기 때문에 함수에 객체전달을 했을 때의 객체의 치환과 객체 리턴 상태일 때 데이터가 어떤식으로 저장이 되는지에 대해 자세히 배우게 되었ㅎ다.
특히 C++에서는 객체의 멤버 변수에 동적 메모리가 할당된 경우에 얕은 복사와 깊은 복사를 하게 된다. 

##### *얕은 복사(shallow copy)   
• 객체 복사 시, 객체의 멤버를 1:1로 복사.   
• 사본은 원본 객체가 할당 받은 메모리를 공유하는 문제가 발생   
##### *깊은 복사(deep copy)   
• 객체 복사 시, 객체의 멤버를 1:1대로 복사   
• 사본은 원본이 가진 메모리 크기 만큼 별도로 동적 할당시킨다.   
• 원본의 동적 메모리에 있는 내용을 사본에 복사하기 때문에 완전한 형태의 복사가 가능하다.   
• 사본과 원본이 메모리를 공유하는 문제가 없다.   
