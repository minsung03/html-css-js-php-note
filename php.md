# 초딩도 이해하는 PHP 기본 

### 작성자 : 김민성

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

출력결과 : ```345```,

In test : ```345```

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

- ```안녕하세요 제 이름은 김민성입니다.```

- ```안녕하세요 제 이름은 $name 입니다.```

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

출력결과 :  ```6```

※ 그 외 문자열 함수

```mb_strlen``` : 다국어의 길이를 올바르게 잴 수 있는 함수

```strpos``` : 문자열에서 특정 위치를 얻어내는 함수

```mb_strpos``` : 다국어의 위치를 올바르게 찾을 때 사용

```strrpos``` : 문자열에 뒤에서부터 찾을때 사용 r = reverse

```str_replace``` : 문자열 내에서 치환할 문자열을 찾아서 치환하는 작업을 하는 함수

```substr``` : 문자열에서 일정부분만 잘라내는 함수

```trim``` : 문자열의 공백을 제거하는 함수

```ltrim, rtrim``` : 좌,우 문자열 공백 제거

<hr />

## 파라미터

\t | \n | \r | \0 | \x0B
---- | ---- | ---- | ---- | ---- |
탭문자 | 새로운 라인 문자 | 라인의 맨앞으로 나타내는 문자 | Null 바이트 문자 (0x00) | 세로 탭 문자

<hr />

## 조건문

조건문이란 어떤 조건에 부합하는지 아닌지에 따라 다른 명령을 수행하기 위한 일종의 의사결정과 같은 것이다.

```if```, ```else```, ```else if```가 조건문이다.

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

값을 넣을때 별도의 인덱스키와 값을 지정하는 방법

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

### array_push

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

### 배열 원소를 제거하는 방법

array_splice를 사용하면 배열 원소를 제거할 수 있다.

```php
  <?php
    array_splice(array &$input , int $offset [, int $length = count($input) [, mixed $replacement = array() ]] ) : array
```

<hr />

### for

```php
  <?php
    $arr = ['김민성', '노승재'];
    
    for($i = 0; $i < count($arr); $i++){
      echo "{$i}의 이름 : {$arr[$i]}";
    }
```

출력결과 : ```1번의 이름 : 김민성```
           ```2번의 이름 : 노승재```
           
<hr />
 
### while

```php
  <?php
    $arr = ['김민성', '노승재'];
    
    while(count($arr) > 0){
      $item = array_pop($arr);
      echo "{$item}을 꺼냈습니다.";
    }
```

array_pop은 배열을 넣으면 열에서 하나를 빼는 구조를 가지고 있다. 결과값은 빼어낸 원소를 반환하도록 되어있다.

<hr />

### foreach 

$array 안에 있는 모든 것을 $value 라고 하고 $value에 대해 무엇인가를 작업할 때 사용한다.

foreach는 키 => 밸류 기반의 배열이나 오브젝트에서 사용된다.

```php
  <?php
    $human = ['name' => '김민성', 'age' => 18, 'job' => '고등학생'];
    
    foreach($human => $key as $item){
      echo "{$key}: {$item}<br />";
    }
```

출력결과
```
name: 김민성
age: 18
job: 고등학생
```
<hr />

## PHP 배열

```php
  <?php
    $arr = [
      [1,2,3,4,5],
      [6,7,8,9,10]
    ];
    
    for($i = 0; $i < 2;  $i++){
      for($j = 0; $j < 2; $j++){
        echo "{$data[$j][$i]}";
      }
      echo "<br>";
    }
```

출력결과 :
```
1 6
2 7
3 8
4 9
5 10
```

※ 배열 관련 함수

- `is_array` : 배열인지 확인하는 함수
- `in_array` : 배열에서 특정 원소가 존재하는 지 찾아주는 함수
- `array_combine` : 2개의 배열을 키와 값을 가지는 연관배열로 합치는 함수이다.
- `array_chunk` : 배열을 지정된 크기로 쪼개는 함수
- `array_diff` : 배열간의 차이점을 분석해주는 함수 
- `arrat_diff_assoc` : 배열간의 차이점과 인덱스까지 비교해주는 함수
- `array_diff_uassoc` : 배열 원소를 비교할 때 어떻게 비교할지 비교함수를 지정하여 처리하는 함수
- `array_fill`() : 시작 인덱스 값부터 지정된 객수만큼 지정된 값을 채워넣은 배열을 반환한다.
- `array_shift`() : 배열의 맨 앞에서 원소를 하나 제거하고 반환하는 함수
- `array_unshift`() : 배열의 맨 앞에 원소들을 집어넣고 집어넣어진 원소의 개수를 반환하는 함수이다.
- `array_map` : 배열을 특정함수에 맵핑시켜서 가공한 배열을 반환하는 함수이다.

 

<hr />

## 정렬 관련 함수

### sort

배열을 정렬해주는 가장 기본적인 함수

```php
  <?php
    sort(array &$arrat[, int $sort_flags = SORT_REGULAR ] ) : bool
```

<hr />

### sort_flag

어떤식으로 정렬할 지를 나타내는 것

- `SORT_REGULAR` : 타입을 변화시키지 않고 일반적인 방법으로 비교
- `SORT_NUMERIC` : 아이템들을 숫자로 변화시켜서 비교
- `SORT_STRING` : 아이템들을 문자열로서 비교
- `SORT_LOCALSTRING` : 현재 locale에 맞추어 문자열로 비교 (locale 값은 setlocale() 함수를 통해 변경가능)
- `SORT_NATURAL` : 아이템을 정렬할 때 자연정렬방식으로 정렬한다.

※ 기본적으로 sort 함수는 오름차순으로 정렬하게 되어 있다.

   내림차순으로 정렬하려면 rsort라는 함수를 사용하면 된다.
   
```php
  <?php
    rsort(array &$array [, int $sort_flags = SORT_REGULAR ] ) : bool
```

다만, sort 함수는 정렬이 되긴하지만 키값은 유지되지 않는다는 단점이 있다.

그 외 sort 함수

- `asort` : 정렬이 이루어지고 난뒤에도 키 값을 유지시켜주는 함수
- `ksort` : 키를 기준으로 정렬해주는 함수
- `usort` : user가 정의한 비교방법으로 정렬하는 함수
- `callback(mixed $a, mixed $b)` : int


<hr />

## 날짜와 시간 다루기
```php
  <?php
    date (string $format [, int $timestamp = time() ] ): string
```

```php
  echo date('Y-m-d') . "<br>";
  
  echo date('Y.m.d' H:i:s') . "<br>";
  
  echo date('y, M , D') . "<br>";
```

출력결과 : 
```
2020-08-21

2020.08.21 11:09:23
          
21, Aug, Fri
```

<hr />

### 포맷문자

*day*

- ```d``` : 0으로 시작하는 두자리의 날짜(몇일)
- ```D``` : 3글자로 표현되는 요일 Mon 부터 Sun까지
- ```j``` : 0으로 시작하지 않는 날짜(몇일) 1 부터 31까지
- ```ㅣ(소문자L)``` : 요일 표시 (Sunday -> Saturday)
- ```N``` : 숫자로 표현한 요일 1(월요일) 부터 6(토요일) 까지 반환
- ```S``` : 서수형식으로 날짜 표현 st, nd, rd, th 등
- ```W``` : 숫자로 표현한 요일 0(일요일)부터 6(토요일)까지 반환
- ```z``` : 해당 년도에 몇번째 날짜인지 표현 0부터 시작해서 365까지 반환

*Week*

- ```W``` : 월요일을 기준으로 지금이 몇번째 주인지 출력

*Month*

- ```F``` : 영문으로 표현된 월 (January 부터 December)
- ```m``` : 0으로 시작하는 숫자표시 유ㅗㄹ 01 ~ 12까지
- ```M``` : 3글자 영어로 표현되는 월 표시 Jan 부터 Dec 까지
- ```n``` : 0으로 시작하지 않는 월 숫자 표시 1 ~ 12까지
- ```t``` : 해당 월의 일자수 28 ~ 31까지

*Year*

- ```L``` : 윤년인지 여부를 출력 윤년이면 1, 아니면 0
- ```Y``` : 4자리 년도
- ```o``` : Y와 동일
- ```y``` : 2자리 년도

*Time*

- ```a``` : am ,pm의 소문자 표시
- ```A``` : am ,pm의 대문자 표시
- ```B``` : 시계회사 Switch에서 제시한 인터넷 시간의 표시
- ```g``` : 12시간 포맷의 시간 (0으로 시작 안함)
- ```G``` : 24시간 포맷의 시간 (0으로 시작 안함)
- ```h``` : 12시간 포맷의 시간 (0으로 시작함)
- ```H``` : 24시간 포맷의 시간 (0으로 시작함)
- ```i``` : 0으로 시작하는 분 00 ~ 59
- ```s``` : 0으로 시작하는 초 00 ~ 59
- ```u``` : 마이크로 초를 표시
- ```v``` : 밀리초로 표시

*TimeZone*

```e``` : 타임존 식별자 (UTC, GMS, Asia/Seoul 등)

*대문자*

```|(대문자)|``` : daylight saving time인지 알려주는 문자 1 일때 daylight saving time

<hr />

### strtotime

문자열을 시간으로 만들어주는 함수

```php
  <?php
    $time = strtotime("2020-08-21 2:06:47");
    
    echo date('Y-m-d h:i:s', "+10 day", $time));
```

출력결과 

```
  2020-08-31 2:06:47
```

<hr />

### date_default_timezone_get();

이 함수는 타임존을 설정하는 함수입니다.

<hr />

## PHP에서 파일 다루기

```txt
  으헤헤헤 나는 바보다
```

```php
  <?php
    $fileName = "txt";
    
    if(file_exsists($fileName)){
      $file = fopen($fileName, "r");
      if($file){
        $size = filesize($filename);
        echo "파일 크기 : {$size} \n";
        $text = fread($file, $size);
        echo $text;
      }else{
        echo "파일 열기에 실패했습니다.";
      }else{
        echo "파일이 존재하지 않습니다.";
      }
    }
```

출력결과

```
$php test.php
파일크기 : (파일크기 출력됨)
으헤헤헤 나는 바보다
```

※ 사용된 함수들

```file_exists``` : 해당 파일이 존재하는지 검사하는 함수

```fopen``` : 실제로 파일을 여는 함수

```filesize``` : 파일의 크기를 바이트 단위로 반환하는 함수

```fread``` : 파일의 내용을 읽어오는 역할을 한다.

```fwrite``` : 파일을 생성하고 그 안에 내용을 기록할 수 있다.

```file_get_contents``` : 파일 내용 전체를 읽어올 때 사용한다.

<hr />

## PHP 다른 파일을 가져오기

```php
  <?php
    funtion dump($value){
      echo "<div class='dump' style='display:inline-block; width: 50%;'>";
      echo "<pre>";
      var_dump($value);
      echo "<pre>";
      echo "</div>";
  }
```
<hr />

### ```_once``` 
  
  ```_once```라는 함수는 한번만 가져온다는 것을 뜻한다.
  
  또한 once가 붙는 함수는 require나 include된 파일을 다시 포함되지 않도록 막아준다
  
  ```php
    <?php
    require_once("lib.php"); // lib.php를 가져옴
    $arr = [1,2,3];
    dump($arr);
  ```

<hr />
  
### 파일 업로드와 다운로드

```html
  <form action="upload_ok.php" method="POST" enctype="multipart/form-data"></form>
```

```코드를 보면 enctype이 있는데 파일을 전송할때는 폼에 반드시 multipart/form-data를 적어주어야 파일이 전송이 된다.```

upload_ok.php

```php
  <?php
    echo "<pre>";
    var_dump($_FILES);
    echo "</pre>";
```

파일의 이름이나 내용은 업로드한 파일에 따라 달라진다.

```$_FILES``` 라는 변수는 전역변수인데, 이 변수는 업로드된 모든 파일이 배열로 저장된다.

upload_ok.php

```php
  $tmpName = $_FILES["upload"]["tmp_name"];
  $realName = $_FILES["upload"]["name"];
  
  if(!file_exists("upload")){
    mkdir("upload");
  }
  
  move_uploaded_file($tmpName. "upload\" . $realName);
```

<hr />

### move_uploaded_file

move_uploaded_file은 업로드된 임시파일을 내가 지정한 폴더로 이동시켜주는 역할을 하는 함수이다.

```php
  <?php
    move_uploaded_file(string $filename, string $destination ) : bool
```

```위에 코드는 파일 이동 성공시 true를 반환하고 실패시 false를 반환한다.```

<hr />

### readfile

함수의 내용을 읽어서 아웃버퍼로 출력해주는 함수

```php
  <?php
    readfile(string $filename [, bool $use_include_path = FALSE [, resource $context ]] ) : int
```

```나중에 if문을 활용하여 권한이 없는 사용자는 파일 다운로드가 되지 않도록 하면 된다.```

<hr />

## PHP 함수와 클래스

### 사용자 정의 함수 만들기

```php
  <?php
    function test($param1, $param2){
      $param1 = $param1 + 20;
      $param2 = $param2 + 10;
      
      return $param1 + param2;
    }
    $a = 20;
    $b = 30;
    
    $result = test($a, $b);
    echo $result . "\n";
    echo $a . "\n";
    echo $b . "\n";
```

출력결과 :
```
  80
  
  20
  
  30
```

```코드를 보면 함수안에서 $a 와 $b 값이 더해져서 나온결과가 리턴되지만  a,b 값은 변경되지 않았다. 이러한 것을 값에 의한 전달이라고 한다.```

```참조에 의한 전달로 보내고 싶다면 매개변수에 &를 붙혀서 참조처리하면 된다 객체의 경우 별도로 참조기호를 붙히지 않아도 참조전달을 한다.```

```php
  <?php
    fucntion test(&$param1, $param2){
      $param1 = $param1 + 20;
      $param2 = $param2 + 10;
    }
```

```$param1 앞에만 & 표시를 해서 해당 값만 함수 호출이 끝난뒤에도 유지된다.```

<hr />

### Object

특정변수 앞에 괄호를 열고 (Object)를 붙혀주면 해당 변수를 객체로 형변환 해준다.

```array``` : 배열

```bool``` : true/false

```callable``` : 함수 또는 호출 가능한 메서드

```float``` : 부동소수점 수

```int``` : 정수

```string``` : 문자열

```클래스명``` : 해당 클래스의 인스턴스 

인자뿐 아니라 반환값의 타입도 지정할 수 있다. 함수의 이름뒤에 콜론과 함께 반환형을 적어주면 된다.

```php
  function countdown(int $top) : int{
    return $top * 3 / 2;
  }
  
  echo countdown(4);
  echo countdown(7);
```

만약 리턴 값이 소수라도 반환값은 자동으로 형변환되어 정수로 나와서 두번째 7을 넣었을 때 10.5가 아닌 10이 나온다.

자동으로 형변환이 가능하면 변환이 되지만 문자열을 반환하면 Fatal Error가 나게 된다.

<hr />

### PHP 클래스

클래스는 변수, 상수, 함수를 포함하는 객체이다. 

클래스 안에서 함수는 메소드라고 한다.

객체를 복사해야 할때는 clone이라는 키워드를 이용하여 복사한다.

```php
  $h1 = new Human("김민성", ["프로그래밍", "농구"]);
  $h2 = clone $h1;
```

<hr />

### 클래스의 상속

```php
  <?php
    spl_autiload_register([callable $autoload_function [, bool $prepend = FALSE]]] ) : bool
```

spl_autoload_register는 오토로드 함수들의 큐의 맨 마지막에 새롭게 함수를 추가한다.

하지만 마지막 prepend변수를 true로 설정하면 큐의 맨뒤가 아니라 맨 앞으로 함수를 추가한다.

<hr />

### PHP namespace

namespace란 같은 이름의 클래스가 있어도 다른 이름 공간에 있다면 이것은 다른 클래스로 인식하는 것이다.

```php
  <?php
    namespace Gondr;
    
    class Human {
      public $name;
      public $hobbies = [];
      
    }
```

<hr />

## PHP Database Object - PDO

PDO 기본 사용

PHP Data Object의 줄임말

PDO란 PHP에서 사용하던 각 데이터베이스별로 접속이 상이한 방식을 벗어나 손쉽게 데이터베이스에 접속하기 위해서 만들어진 데이터베이스 오브젝트이다.

생성된 테이블의 모양

이름 | 종류 | 길이 | 인덱스
---- | ---- | ---- | ---- |
id | varchar | 100 | primary key
name | varchar | 100 |    |
password | varchar | 100 |     
level | Int |      |      |

<hr />
0
dbtest.php

```php
  <?php
    $host = "localhost";
    $dbname = "myblog";
    $charset = "utf8mb4";
    $user = "root";
    $pass = "";
    
    $db = new PDO("mysql:host{$host}l dbname={$dbname}; charset={$charset}", $user, $pass);
    
    var_dump ={$db};
```
dbtest.php의 역할은 데이터베이스를 연결하는 것이다.

각각 코드의 역할

- 어떤 데이터베이스 유형인지(mysql)

- 데이터베이스가 위치한 호스트는 어디인지(localhost)

- 해당 호스트에서 어떤 데이터베이스에 접속하려고하는지(myblog)

- 연결할 때 해당 데이터들의 인코딩은 어떤지.(utf8mb4)

<hr />

## PDO를 통해 SQL 작업하기

```php
  $sql = "INSERT INTO users (`id`, `name`, `password`, `level)
  VALUES('ms0716', '김민성', 'PASSWORD('1234'), 1')";
  
  $db->exec($sql);
```

 ```이 코드는 SQL INSERT문에서 고정된 값을 INSERT 하도록 되어있다.```

```exec 메서드는 PDO 클래스에서 단순하게 쿼리를 실행해주는 역할을 하고있다. 만약 쿼리가 insert 도는 delete와 같이 조회값이 없으면 row 숫자를 리턴해준다.```

```SELECT와 같이 조회값이 있는 쿼리라면 exec로는 실행할 수 없다. 조회값을 가져오려면 query라는 별도의 메서드를 사용해야 한다.```

- 코드 수정

```php
  <?php
    $sql = "INSERT INTO users(`id`, `name`, `password`, `level`)
            VALUES('ms0716', '김민성', PASSWORD('1234'), 1)";
            
    $db -> exec($sql);
    
    $host = "localhost";
    
    $dbname = "myblog";
    
    $charset = "utf8mb4";
    
    $user = "root";
    
    $pass = "";
    
    $db = new PDO("mysql:host={$host}; dbname = {$dbname}; charset = {$charset}" , $user, $pass);
    
    $sql = "SELECT * FROM users";
    
    $result = $db->query($sql);
    
    echo "<pre>";
    
    echo "<br><br>";
    
    var_dump($result);
```

결과
```
  query를 통해 가져온 결과 값은 fetch라는 특수한 동작을 통해서 값을 가져올 수 있는 PDOStatement 객체이다. 
  
  이곳에서 값을 가져올 때는 foreach로 돌리거나 fetch 나 fetchAll을 사용해야 한다.
  
  foreach로 돌려야하는 이유는 배열이아니라 객체(object)이기 떄문이다
  
  해당 객체의 public 멤버는 queryString 밖에 없기 때문에 var_dump로 출력한다면 단순한 오브젝트 쿼리가 나오게 된다.
  
  
```
<hr />

### fetchAll

값을 리스트로 가져오고 싶으면 fetchAll을 사용하면 된다.

```php
  <?php
    $list = $result->fetchAll();
    
    echo "<pre>";
    
    var_dump($list);
    
    echo "</pre>";
```

```
fetchAll은 리스트 형태로 값을 가져온다. 만약 첫번째부터 한 개씩 가져오고 싶다면 순서대로 fetch()를 호출해주면 한개씩 넘어온다. id의 경우 ["id"]로도 값이 담기고 [0]에도 값이 담긴다.
```

