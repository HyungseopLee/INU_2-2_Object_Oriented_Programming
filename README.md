# 객체기반 SW 설계 — C++ & OOP 정리

인천대학교 2학년 2학기 전공 `객체기반SW설계` 수업을 들으며 정리한 **C++ 기본 문법**과 **객체지향 프로그래밍(OOP) 필수 개념** 노트입니다.
각 개념마다 실제 학습에 사용한 예제 코드 파일을 링크해두었으니, 개념 설명을 먼저 읽고 해당 `.cpp` 파일에서 직접 코드를 확인하는 방식으로 보면 됩니다.

> 파일명은 `번호_주제.cpp` 형식으로, 배운 순서대로 정렬되어 있습니다.

---

## 📚 목차

- [객체기반 SW 설계 — C++ \& OOP 정리](#객체기반-sw-설계--c--oop-정리)
  - [📚 목차](#-목차)
  - [1. C++ 기본 문법](#1-c-기본-문법)
  - [2. 함수](#2-함수)
  - [3. 클래스와 객체 (OOP 입문)](#3-클래스와-객체-oop-입문)
  - [4. 생성자 / 소멸자](#4-생성자--소멸자)
  - [5. 포인터 \& 동적 메모리](#5-포인터--동적-메모리)
  - [6. static 멤버](#6-static-멤버)
  - [7. 연산자 오버로딩](#7-연산자-오버로딩)
  - [8. 상속 (Inheritance)](#8-상속-inheritance)
  - [9. 다형성 (Polymorphism)](#9-다형성-polymorphism)
    - [업캐스팅 / 다운캐스팅](#업캐스팅--다운캐스팅)
    - [virtual \& 동적 바인딩](#virtual--동적-바인딩)
    - [순수 가상 함수 \& 추상 클래스 (인터페이스)](#순수-가상-함수--추상-클래스-인터페이스)
  - [10. 파일 입출력](#10-파일-입출력)
  - [11. 예외 처리 (Exception Handling)](#11-예외-처리-exception-handling)
  - [12. 템플릿 (Template)](#12-템플릿-template)
  - [13. STL (Standard Template Library)](#13-stl-standard-template-library)
    - [컨테이너](#컨테이너)
    - [반복자 \& 알고리즘](#반복자--알고리즘)
  - [14. OOP 4대 특징 요약](#14-oop-4대-특징-요약)
    - [참고: 디자인 패턴](#참고-디자인-패턴)

---

## 1. C++ 기본 문법

| 개념 | 설명 | 예제 |
| --- | --- | --- |
| 입출력 | `cout`, `cin`으로 콘솔 입출력 | [002_cout.cpp](002_cout.cpp) |
| 자료형 | 기본 데이터 타입 정리 | [003_datatype.cpp](003_datatype.cpp) |
| bool | 참/거짓 타입 | [006_bool.cpp](006_bool.cpp) |
| string | 문자열 클래스, 대소 비교, 멤버 함수 | [007_string.cpp](007_string.cpp), [019](019_string_대소비교.cpp), [020](020_h_string_memberFunc.cpp) |
| random | 난수 생성 | [008_random.cpp](008_random.cpp) |
| 배열 | 1차원/2차원 배열, range-based for, find | [009](009_array.cpp), [010](010_rangebased.cpp), [011](011_find.cpp), [012](012_이중배열출력.cpp) |

**C++이 C보다 좋은 점**: [001_cpp장점.txt](001_cpp장점.txt) — OOP 지원, STL, 참조자, 함수 오버로딩, 예외 처리 등.

---

## 2. 함수

| 개념 | 설명 | 예제 |
| --- | --- | --- |
| 함수 원형 (prototype) | 선언과 정의 분리 | [013](013_function_prototype.cpp) |
| Call by Value / Reference | 값 전달 vs 참조 전달 (주소를 넘겨 원본 수정 가능) | [014](014_callby.cpp), [015](015_callby.cpp) |
| 함수 오버로딩 | 같은 이름, 다른 매개변수 → 컴파일러가 시그니처로 구분 | [016_overloadedFunc.cpp](016_overloadedFunc.cpp) |
| 기본 매개변수 | 인자를 안 넘기면 기본값 사용 (오른쪽부터 채워야 함) | [017_defaultParameter.cpp](017_defaultParameter.cpp) |
| inline 함수 | 함수 호출 오버헤드를 줄이기 위해 호출부에 코드를 직접 삽입하도록 컴파일러에 요청 | [018_inlineFunc.cpp](018_inlineFunc.cpp) |

---

## 3. 클래스와 객체 (OOP 입문)

- **class**: 데이터(멤버 변수)와 기능(멤버 함수)을 하나로 묶은 사용자 정의 타입(설계도)
- **object**: class로부터 실제로 메모리에 찍어낸 실체(instance)

```cpp
class Circle {
private:
    int radius;          // information hiding
public:
    void setRadius(int r);
    double getArea();
};
```

- 선언(.h)과 구현(.cpp)을 분리하는 것이 일반적: [023_Circle.h](023_Circle.h), [023_Circle.cpp](023_Circle.cpp), [023_main.cpp](023_main.cpp) (실무에서는 헤더가 여러 번 include돼도 중복 선언 에러가 안 나도록 `#pragma once` 또는 `#ifndef` 헤더 가드를 넣는 것이 정석)
- getter/setter로 private 멤버에 안전하게 접근: [030_getter_setter.cpp](030_getter_setter.cpp)
- 객체를 함수 인자로 주고받기: [031_객체와함수.cpp](031_객체와함수.cpp), [041_class_ref.cpp](041_class_ref.cpp), [042_class_return_obj.cpp](042_class_return_obj.cpp)
- 클래스 안에 다른 클래스 객체를 멤버로 포함: [045_클래스안에객체.cpp](045_클래스안에객체.cpp)

관련 예제: [021_oop.cpp](021_oop.cpp), [022_1class.cpp~022_3class.cpp](022_1class.cpp), [024_oop특징.cpp](024_oop특징.cpp), [025_UML.txt](025_UML.txt)

---

## 4. 생성자 / 소멸자

- **생성자(Constructor)**: 객체가 생성될 때 자동으로 호출되어 멤버 변수를 초기화. 클래스 이름과 동일, 반환형 없음, 오버로딩 가능.
- **소멸자(Destructor)**: 객체가 소멸될 때(스코프 종료, `delete` 등) 자동 호출. `~클래스이름()` 형태, 오버로딩 불가.
- **복사 생성자(Copy Constructor)**: 기존 객체를 복사해서 새 객체를 만들 때 호출 (`Pizza p2 = p1;`, 함수에 값으로 객체 전달 시 등). 정의하지 않으면 컴파일러가 얕은 복사(shallow copy)로 자동 생성.

```cpp
Pizza(const Pizza& p) { ... }   // 복사 생성자
```

- 기본 생성자 / 초기화 리스트 문법: [026](026_constructor.cpp), [027](027_constructor.cpp), [028](028_constructor.cpp)
- 소멸자 호출 시점: [029_destructor.cpp](029_destructor.cpp), [064_생성자_소멸자.cpp](064_생성자_소멸자.cpp), [065_생성자.cpp](065_생성자.cpp)
- 대입 연산자와 복사 생성자의 차이: [043_why_copy_constructor.cpp](043_why_copy_constructor.cpp), [044](044_복사생성자_대입연산자.cpp), [056_복사생성자.cpp](056_복사생성자.cpp)
- **const 멤버 함수**: 함수 뒤에 `const`를 붙이면 그 함수 안에서 멤버 변수를 변경할 수 없음 (변경 시 컴파일 에러) → [040_const_mem_function.cpp](040_const_mem_function.cpp)

---

## 5. 포인터 & 동적 메모리

| 개념 | 설명 | 예제 |
| --- | --- | --- |
| 포인터 기초 | 주소를 저장하는 변수 | [036_pointer.cpp](036_pointer.cpp) |
| 동적 메모리 할당 | `new` / `delete` (힙 메모리) | [037_dynamic_mem_allocation.cpp](037_dynamic_mem_allocation.cpp) |
| 객체의 동적 할당 | `new`로 클래스의 객체 생성 | [038_class_allocation.cpp](038_class_allocation.cpp) |
| 스마트 포인터 | `unique_ptr` 등 — `delete`를 잊어도 스코프를 벗어나면 자동 해제되는 wrapper (진짜 포인터는 아님) | [039_smart_pointer.cpp](039_smart_pointer.cpp) |

```cpp
unique_ptr<Person> pp1(new Person(21));  // delete 불필요
```

---

## 6. static 멤버

- **static 변수**: 모든 객체가 **공유**하는 단 하나의 복사본. 클래스 이름으로 초기화(`int Lemon::count = 30;`) 필요.
- **static 함수**: 객체 생성 없이 `클래스::함수()`로 호출 가능. 오직 static 변수/static 함수만 사용 가능(일반 멤버 변수 접근 불가).

```cpp
int MyObj::k = 10;
MyObj::showStatics();  // 객체 없이 호출
```

- [046](046_정적변수.cpp), [047](047_정적변수.cpp) static 변수 / [048_정적함수.cpp](048_정적함수.cpp) static 함수
- **싱글톤 패턴(Singleton)**: 생성자를 `private`으로 막고, static 메서드(`getInstance()`)로만 유일한 객체를 얻도록 하여 **클래스당 객체를 오직 1개만 생성**하도록 강제하는 디자인 패턴 (GOF 패턴 중 하나) → [049_h_singleton_design_pattern.cpp](049_h_singleton_design_pattern.cpp)

---

## 7. 연산자 오버로딩

C++은 `+`, `-`, `++`, `[]`, `<<` 같은 연산자를 클래스에 맞게 재정의할 수 있습니다.

| 종류 | 설명 | 예제 |
| --- | --- | --- |
| 기본 오버로딩 | 멤버 함수 형태로 연산자 재정의 | [050](050_h_operator_overloading.cpp), [052](052_operator_overloading.cpp) |
| 전위 `++`/후위 `++` | 매개변수로 구분 (`operator++()` vs `operator++(int)`) | [053_pre_++.cpp](053_pre_++.cpp), [054_post_++.cpp](054_post_++.cpp) |
| 인덱스 연산자 `[]` | `operator[]`로 배열처럼 접근 | [057_index_operator.cpp](057_index_operator.cpp) |
| 포인터용 연산자 오버로딩 | `->`, `*` 등 | [058](058_pointer_operator_overloading.cpp), [059](059_h_pointer_operator_overloading.cpp) |
| friend 함수/클래스 | 특정 외부 함수·클래스에 한해 `private` 멤버 접근을 허용 (주로 `<<`, `>>` 연산자 오버로딩처럼 왼쪽 피연산자가 클래스 자신이 아닐 때 활용). 캡슐화(정보 은닉)를 깨는 문법이라 남용하지 않는 것이 좋음 | [060](060_friend.cpp), [061](061_friend.cpp), [062_friend_operator_overloading.cpp](062_friend_operator_overloading.cpp) |

---

## 8. 상속 (Inheritance)

부모(기반) 클래스의 멤버를 자식(파생) 클래스가 물려받아 재사용/확장하는 것.

```cpp
class Animal { ... };
class Dog : public Animal { ... };   // Dog는 Animal을 상속
```

- 기본 상속 문법: [063_inheritance.cpp](063_inheritance.cpp)
- 상속에서 생성자/소멸자 호출 순서 (자식 생성 시 부모 생성자 → 자식 생성자, 소멸 시 반대) : [064](064_생성자_소멸자.cpp)
- 멤버 함수 재정의(overriding): 자식이 부모와 동일한 시그니처의 함수를 다시 정의 → [066](066_멤버함수_재정의.cpp), [067](067_멤버함수_재정의.cpp)
- 다중 상속: 하나의 클래스가 여러 부모 클래스를 상속. 부모 클래스들에 동일한 이름의 멤버가 있으면 이름이 충돌하므로, `객체.부모클래스명::멤버` 형태로 어느 부모의 멤버인지 명시(scope resolution)해줘야 함. 이런 모호함 때문에 소프트웨어 공학적으로는 지양되는 편 → [068_다중_상속.cpp](068_다중_상속.cpp)

---

## 9. 다형성 (Polymorphism)

> "어떤 멤버 함수를 부를지, 그때그때 상황에 따라 달라진다"

- **정적 다형성(static)**: 함수/연산자 오버로딩 — 컴파일 시점에 결정. 빠르지만 실행 중 변경 불가.
- **동적 다형성(dynamic binding)**: `virtual` 키워드 + 포인터/참조 — 실제로 어떤 함수가 호출될지 **런타임에 결정**.

### 업캐스팅 / 다운캐스팅

| 개념 | 설명 | 예제 |
| --- | --- | --- |
| 업캐스팅(Upcasting) | 자식 객체를 부모 타입 포인터로 가리킴. 항상 안전 | [069_upcasting.cpp](069_upcasting.cpp) |
| 다운캐스팅(Downcasting) | 부모 타입 포인터를 자식 타입으로 강제 캐스팅. 실제로는 부모 크기만큼만 메모리가 있어 위험할 수 있음 | [070_downcasting.cpp](070_downcasting.cpp) |
| dynamic_cast | 위 다운캐스팅의 위험을 줄이기 위한 안전한 캐스팅 (실패 시 `nullptr` 반환, `virtual` 함수가 있어야 사용 가능) | [071_dynamic_cast.cpp](071_dynamic_cast.cpp) |

### virtual & 동적 바인딩

```cpp
class Animal {
public:
    virtual void speak() { cout << "Animal" << endl; }
};
class Dog : public Animal {
public:
    void speak() override { cout << "Dog" << endl; }
};

Animal* a = new Dog();
a->speak();   // virtual 덕분에 "Dog" 출력 (동적 바인딩)
```

- `virtual`이 없으면 포인터의 **정적 타입(Animal)** 기준으로 함수가 호출되고, `virtual`을 붙이면 **실제 객체 타입(Dog)** 기준으로 호출됨
- 동적 바인딩은 **포인터/참조 타입에서만** 성립 (값 타입 대입은 슬라이싱되어 부모 함수 호출됨)
- 예제: [072](072_p.cpp), [073_polymorphism.cpp](073_polymorphism.cpp), [074](074_v.cpp), [075_virtual.cpp](075_virtual.cpp), [076_복습.cpp](076_복습.cpp)

### 순수 가상 함수 & 추상 클래스 (인터페이스)

```cpp
class Shape {
public:
    virtual void draw() = 0;   // 순수 가상 함수 (구현 없음)
};
```

- `virtual 함수() = 0;` 형태 → **순수 가상 함수**, 이를 하나라도 가진 클래스는 **추상 클래스**(객체 생성 불가)
- 자식 클래스가 반드시 오버라이딩해서 구현해야 함 → 안 하면 컴파일 에러 → Java의 `interface`와 같은 역할
- 예제: [077_순수가상함수.cpp](077_순수가상함수.cpp), [078_순수가상함수_예시.cpp](078_순수가상함수_예시.cpp), [079_순수가상함수_기능.cpp](079_순수가상함수_기능.cpp)

---

## 10. 파일 입출력

| 개념 | 설명 | 예제 |
| --- | --- | --- |
| 텍스트 파일 출력/입력 | `ofstream` / `ifstream` | [080_파일출력.cpp](080_파일출력.cpp), [081_파일입력.cpp](081_파일입력.cpp) |
| 이진 파일 (binary) | `write()` / `read()`로 객체 자체를 바이너리로 저장·복원 | [082_이진파일_write.cpp](082_이진파일_write.cpp), [083_이진파일_read.cpp](083_이진파일_read.cpp) |
| Random Access File | `seekg`/`seekp`로 파일 임의 위치 접근 | [084_random_access_file.cpp](084_random_access_file.cpp) |

---

## 11. 예외 처리 (Exception Handling)

문제가 생길 수 있는 코드를 `try`로 감싸고, 문제 발생 시 `throw`로 예외를 던지면 `catch`에서 처리.

```cpp
try {
    if (person == 0) throw person;   // int 예외
    else throw 'c';                  // char 예외
}
catch (int e)  { /* int 타입 예외 처리 */ }
catch (char c) { /* char 타입 예외 처리 */ }
```

- 기본 예외 처리: [085_exception_handling.cpp](085_exception_handling.cpp)
- 여러 타입의 예외를 각각 다른 `catch`로 처리 (multiple catch): [087_multiple_catch.cpp](087_multiple_catch.cpp)

---

## 12. 템플릿 (Template)

같은 로직을 **타입만 바꿔가며** 재사용하기 위한 문법. "함수를 만들어내는 함수", "클래스를 만들어내는 클래스".

```cpp
template <typename T>
class Box {
    T data;
public:
    Box(T d) : data(d) {}
    T getData() { return data; }
};

Box<int> b1(10);   // int용 Box 클래스가 이 시점에 만들어짐
```

- 함수 템플릿: [086_함수_template.cpp](086_함수_template.cpp), [088_function_template.cpp](088_function_template.cpp)
- 클래스 템플릿: [089](089_class_template.cpp), [090_class_template.cpp](090_class_template.cpp)
- `vector<int>`처럼 STL 컨테이너들도 결국 클래스 템플릿으로 구현되어 있음

---

## 13. STL (Standard Template Library)

미리 만들어진 자료구조(컨테이너)와 알고리즘의 모음. 대부분 템플릿으로 구현되어 있어 어떤 타입이든 담을 수 있습니다.

### 컨테이너

| 컨테이너 | 특징 | 예제 |
| --- | --- | --- |
| `vector` | 동적 배열, 2차원 벡터 | [032](032_STL_vector.cpp), [034_STL_2차원_vector.cpp](034_STL_2차원_vector.cpp) |
| `array` | 고정 크기 배열 (STL 버전) | [035_STL_array.cpp](035_STL_array.cpp) |
| `list` | 이중 연결 리스트 | [092_list.cpp](092_list.cpp) |
| `deque` | 양방향 큐 | [094_deque.cpp](094_deque.cpp) |
| `set` | 중복 없는 정렬된 집합 | [095_set.cpp](095_set.cpp) |
| `map` | key-value 쌍 저장 (정렬됨) | [096_map.cpp](096_map.cpp) |
| `stack` | LIFO (컨테이너 어댑터, 기본 내부 컨테이너: `deque`) | [097_stack.cpp](097_stack.cpp) |
| `queue` | FIFO (컨테이너 어댑터, 기본 내부 컨테이너: `deque`) | [099_queue.cpp](099_queue.cpp) |
| `priority_queue` | 우선순위 큐 (힙 기반, 기본 내부 컨테이너: `vector`) | [100](100_priority_queue.cpp), [101](101_pritority_queue.cpp) |

> `stack`/`queue`/`priority_queue`는 컨테이너가 아니라, 다른 컨테이너 위에 LIFO/FIFO/힙 인터페이스만 씌운 **컨테이너 어댑터**입니다. `stack`·`queue`는 기본적으로 `deque`를 내부에서 사용하고, `priority_queue`는 기본적으로 `vector`를 사용합니다(둘 다 두 번째 템플릿 인자로 바꿀 수 있음: `stack<int, list<int>>`, `priority_queue<int, vector<int>, MyCompare<int>>`) → [098_container_adapter.cpp](098_container_adapter.cpp), [101_pritority_queue.cpp](101_pritority_queue.cpp)

### 반복자 & 알고리즘

| 개념 | 설명 | 예제 |
| --- | --- | --- |
| iterator | 컨테이너 원소들을 순회하는 포인터 같은 객체 | [093_iterator.cpp](093_iterator.cpp) |
| `<algorithm>` | STL이 제공하는 범용 알고리즘 헤더 | [033_STL_algorithm.cpp](033_STL_algorithm.cpp) |
| `find` / `find_if` | 값 찾기 / 조건으로 찾기 | [102_find.cpp](102_find.cpp), [103_find_if.cpp](103_find_if.cpp) |
| `sort` | 오름차순/내림차순 정렬 | [104_sort_asc_desc.cpp](104_sort_asc_desc.cpp) |
| `reverse` | 컨테이너 뒤집기 | [105_reverse.cpp](105_reverse.cpp) |
| `for_each` | 각 원소에 함수 적용 | [106_foreach.cpp](106_foreach.cpp) |
| 람다 함수 | 이름 없는 즉석 함수 `[](int x){ ... }` — 알고리즘 함수에 조건/동작을 넘길 때 자주 사용 | [107_Lambda_func.cpp](107_Lambda_func.cpp) |

---

## 14. OOP 4대 특징 요약

| 특징 | 한 줄 정의 | 관련 예제 |
| --- | --- | --- |
| **캡슐화 (Encapsulation)** | 데이터와 메서드를 하나로 묶고, `private`으로 정보를 은닉(information hiding)해 외부에서 함부로 접근하지 못하게 함 | [060_friend.cpp](060_friend.cpp), [030_getter_setter.cpp](030_getter_setter.cpp) |
| **상속 (Inheritance)** | 기존 클래스의 속성/기능을 물려받아 재사용·확장 | [063_inheritance.cpp](063_inheritance.cpp) |
| **다형성 (Polymorphism)** | 같은 이름의 함수 호출이 상황(오버로딩) 또는 실제 객체 타입(오버라이딩+virtual)에 따라 다르게 동작 | [073_polymorphism.cpp](073_polymorphism.cpp) |
| **추상화 (Abstraction)** | 복잡한 구현은 감추고, 반드시 필요한 인터페이스(순수 가상 함수)만 노출 | [077_순수가상함수.cpp](077_순수가상함수.cpp) |

---

### 참고: 디자인 패턴
- **싱글톤 패턴(Singleton)**: 클래스의 인스턴스를 오직 1개만 생성하도록 강제 → [049_h_singleton_design_pattern.cpp](049_h_singleton_design_pattern.cpp)
