# php 기본

## php 작성법

```php
  <?php 로 시작하여 ?> 로 끝난다.
  
  ?>는 php만으로 되있으면 생략가능.
```

<hr />

## php echo

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

## php 변수

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

전역변수 : 어디서나 접근 가능한 함수 밖의 변수

지역변수 : 내부에서만 사용가능한 변수

```php
<?php
  $a = 20; // 전역변수
  
  function test(){
    $b = 30; // 지역변수
    
    global $a; // 전역변수를 사용하려면 global이라는 예약어를 사용해야한다.
    
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

선언된 변수를 지우는 경우에는 unset 함수를 사용한다.

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

