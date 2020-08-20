# 초딩도 이해하는 PHP 기본

## PHP 작성법

```php
  <?php 로 시작하여 ?> 로 끝난다.
  
  ?>는 php만으로 되있으면 생략가능.
```

<hr />

## PHP echo

echo는 문장을 html에 출력해주는 역할을 하는 php 함수이다.

```php
  <!DOCTYPE HTML>
    <html lang = "ko">
    <head>
      <meta-charset="UTF-8">
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
      <meta http-equiv="X-UA-Compatible" content="ie=edge">
      <title>Document</title>
    </head>
    <body>
      <?php
        echo "<h1>Hello World!</h1>";
      ?>
    </body>
    </html>
```

<hr />

## PHP 변수

선언할때 변수명 앞에 $를 붙히면 된다.

```php
  <?php
    $a = 20; // 숫자형 변수
    $b = "String"; // 문자열 변수
    $c = [1,2,3,4]; // 배열변수
  ?>
```

<hr />

## 변수의 유효범위

전역변수를 사용하려면 global이라는 예약어를 사용해야한다.

```php
<?php
  $a = 20; // 전역변수
  
  function test(){
    $b = 30; 
    
    global $a;
    
    echo $a + $b;
    
  }
  
  test();
```

<hr />

## 변수의 선언 확인과 선언취소

isset은 변수가 선언되었는지 안되었는지 확인해주는 함수이다.

```php
  <?php
  isset( mixed $var [, mixed $...]) : bool
```

여러개의 변수를 넣었을 경우에 넣은 모든 변수가 선언이 되있어야지만 True를 반환한다.

변수가 선언되었으나 값이 비어있다면 False를 반환한다.

※ 선언된 변수를 지우는 경우에는 unset 함수를 사용한다.

```php
  unset(mixed $var [, mixed $...]) : void
```

<hr />

## 상수

상수와 변수의 차이는 상수는 한번 정의하면 스크립트가 실행되는 동안 값을 변경할 수 없다.

상수는 변수와 달리 앞에 $를 붙히지 않고 어디에 선언하여도 전역의 유효범위를 가진다.

```php
  define(string $name, mixed $value[, bool $case_insensitive = FALSE ] ) : bool
```

```php
  define("HOME", "\src");
  
  echo HOME . "<br>";
  fucntin test(){
    echo "In test :" . HOME;
  }
  test();
```

출력결과 : 345,

In test : 345

<hr />

## 마법상수

```php
<?php
  __LINE__ : 이 상수가 사용된 라인의 넘버
  
  __FILE__ : 현재 파일의 전체 경로와 파일명을 반환한다. 
              
             만약 파일 내부에 사용되었다면 include된 그 파일의 이름을 반환함.
             
 __DIR__ : 현재 파일의 디렉토리(폴더)를 반환한다.
 
 __FUNCTION__ : 현재 실행되고 있느 함수 이름을 반환한다.
 
 __CLASS__ : 현재 클래스의 이름을 반환한다.
 
 __TRAIT__ : trait 이름을 반환한다.
 
 __METHOD__ : 메소드의 이름을 반환한다.
 
 __NAMESPACE__ : 현재 네임스페이스의 이름을 반환한다.
 
 ClassName::class : 클래스 이름을 반환한다.
```

<hr />

## PHP 문자열

PHP에서 문자열은 큰 따옴표 또는 작은 따옴표로 감싸서 표현한다.

- 큰따옴표로 출력하면 해당변수의 내용이 출력된다.

- 작은 따옴표로 출력하면 쓰여진 그대로 출력이 된다.

```php
  <?php
  $name = "김민성";
  
  echo "안녕하세요 제 이름은 $name 입니다.";
  
  echo '안녕하세요 제 이름은 $name 입니다.';
  
```

출력결과

- 안녕하세요 제 이름은 김민성입니다.

- 안녕하세요 제 이름은 $name 입니다.

<hr />

## strlen

strlen은 문자열의 길이를 재는 함수이다.

```php
  <?php
    strlen(string $string) : int
```

```php
   <?php
    $str = 'abcdef';
  
    echo strlen($str) . "<br>";
```

출력결과 :  6

※ 그 외 문자열 함수

mb_strlen : 다국어의 길이를 올바르게 잴 수 있는 함수

strpos : 문자열에서 특정 위치를 얻어내는 함수

mb_strpos : 다국어의 위치를 올바르게 찾을 때 사용

strrpos : 문자열에 뒤에서부터 찾을때 사용 r = reverse

str_replace : 문자열 내에서 치환할 문자열을 찾아서 치환하는 작업을 하는 함수

substr : 문자열에서 일정부분만 잘라내는 함수

trim : 문자열의 공백을 제거하는 함수

ltrim, rtrim : 좌,우 문자열 공백 제거

<hr />

## 파라미터

\t | \n | \r | \0 | \x0B
---- | ---- | ---- | ---- | ---- |
탭문자 | 새로운 라인 문자 | 라인의 맨앞으로 나타내는 문자 | Null 바이트 문자 (0x00) | 세로 탭 문자

<hr />

## 조건문

조건문이란 어떤 조건에 부합하는지 아닌지에 따라 다른 명령을 수행하기 위한 일종의 의사결정과 같은 것이다.

if, else, if가 조건문이다.
구조

```php
  <?php
    if(expr)
      statement
```

<hr />

## 반복문

while문과 do while문 for문 foreach문을 모두 가지고 있다.

### 배열

정보없이 값만 들어가 있는 기본적인 방법

값을 넣을때 -별도의 인덱스키와 값을 지정하는 방법

```php
  <?php
    $arr = ['웹디자인 기능반', '게임기능반'];
    
    $info = ['name'=>'김민성', 'age'=>18];
    
    echo "{$human[0]}"; // 웹디자인 기능반 출력
    
    echo "{$human[1]}"; // 게임기능반 출력
    
    echo "{$human['name']}"; // 김민성 출력
    
    echo "{$human['age']}"; // 18 출력
```

<hr />

## array_push

별도의 함수를 호출하는 함수

```php
  <?php
    
    //방법 1
    
    $arr = ['김민성'];
    
    $arr = [] = '18';
    
    echo "{$arr[4]}"; // 18
    
    // 방법 2
    
    array_push($arr, "18");
    
    echo "{$department[5]}"; // 18
```

<hr />

## 배열 원소를 제거하는 방법

array_splice를 사용하면 배열 원소를 제거할 수 있다.

```php
  <?php
    array_splice(array &$input , int $offset [, int $length = count($input) [, mixed $replacement = array() ]] ) : array
```

<hr />

