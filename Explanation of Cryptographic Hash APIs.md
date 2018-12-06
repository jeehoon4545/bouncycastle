# Explanation of Cryptographic Hash APIs



# 1.암호화 해시 함수

# (cryptographic hash function)

+ 해시 값으로부터 원래의 입력값과의 관계를 찾기 어려운 성질을 가지는 경우를 의미
  + **역상 저항성**(preimage resistance):주어진 해시 값에 대해, 그 해시 값을 생성하는 입력값을 찾는 것이 계산상 어렵다. 즉, [제 1 역상 공격](https://ko.wikipedia.org/wiki/%EC%97%AD%EC%83%81_%EA%B3%B5%EA%B2%A9)에 대해 안전해야 한다.
  + **제 2 역상 저항성**(second preimage resistance):입력 값에 대해, 그 입력의 해시 값을 바꾸지 않으면서 입력을 변경하는 것이 계산상 어렵다. [제 2 역상 공격](https://ko.wikipedia.org/wiki/%EC%97%AD%EC%83%81_%EA%B3%B5%EA%B2%A9)에 대해 안전해야 한다.
  + **충돌 저항성**(collision resistance): [해시 충돌](https://ko.wikipedia.org/wiki/%ED%95%B4%EC%8B%9C_%EC%B6%A9%EB%8F%8C)에 대해 안전해야 한다. 같은 해시 값을 생성하는 두 개의 입력값을 찾는 것이 계산상 어려워야 한다.

즉, 입력값과 해시 값에 대해서, 해시 값을 망가뜨리지 않으면서 입력값을 수정하는 공격에 대해 안전해야 한다. 이러한 성질을 가지는 해시 값은 원래 입력값을 의도적으로 손상시키지 않았는지에 대한 검증 장치로 사용할 수 있다.

--------------------------------------

# 2. API 

## (Application Programming Interface)

* 응용프로그램에서 사용할 수 있도록, 운영체제(OS) 나 프로그래밍 언어가 제공하는 기능을 제어할 수 있게 만든 인터페이스를 뜻함.
* 파일 제어, 창 제어, 화상 처리, 문자 제어 등을 위한 인터페이스를 제공.

---------------------------

### 이용

+ API는 응용 프로그램 이진 인터페이스(ABI)와는 구별한다.

  #### 절차적 언어에서의 API

  대부분의 절차적 언어에서 API는 특정한 작업을 수행할 함수들의 집합을 규정하며, 

  특정 소프트웨어 구성 요소와 상호 작용할 수 있게 한다.

  유닉스 명령어 `man 3 sqrt`는 `sqrt` 함수의 시그니처를 대표한다:

```
SYNOPSIS
            #include <math.h>
            double sqrt(double X);
            float  sqrtf(float X);
DESCRIPTION
       sqrt computes the positive square root of the argument. ...
RETURNS
       On success, the square root is returned. If X is real and positive...
```

이와 비슷하게, 다른 언어들은 절차적 라이브러리를 갖고 있다.

```
$ perldoc -f sqrt
       sqrt EXPR
       sqrt    #Return the square root of EXPR.  If EXPR is omitted, returns
               #square root of $_.  Only works on non-negative operands, unless
               #you've loaded the standard Math::Complex module.
```

<u>Member1 최선호</u>