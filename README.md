# c-programming-notes ✨
> 중앙대학교 김상욱 교수님의 수업을 들으며 작성한 C programming 노트입니다!  
다른 언어를 공부한 후에 c언어를 배운 케이스라서, 기초부터는 아니고 **완전 제 기준으로** c언어에서 새로 배운 부분들을 정리해보았습니다!  

도움을 주시고싶은 분들은 fork 후 pull request 해주시면 감사감사베리감사입니당    
이 글이 도움이 되셨다면 ⭐ 를 눌러주세요0___<✨  

<br />

## 목차

---

| No. | 나름의 Index                                                                                                                                                                                 |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
|     | **C 언어 정복 (이라고 쓰고 A+ 주세요 라고 읽는다)**                                                                                                                                                                           |  |
| 1  | [C언어 기초](#1-c언어-기초)                                                                                                                                                                                |
| 2  | [getchar()함수](#2-getchar()-함수)                                                                                                                                                                                 |       



### 1. c언어 기초

### 2. getchar() 함수
#### getchar() 함수를 다양한 character string받는데 사용하기  
```c
main()
char character;
character=''; //캐릭터 값을 일단 빈칸으로 설정해줌 
while(character!='\n') //엔터가 들어오지 않는 동안 계속되도록 함 
{
    character =getchar(); //getchar()으로 계속 받고, character 변수에 값 저장 
}
```

### 3. putchar() 함수  
#### putchar() 함수를 여러개 character를 가진 string 값에 사용하기  
=multi character strings 라고 불린다.  
multi character strings 를 읽기 위해 0값이 나오기 전까지 putchar()하도록 코드를 짠다.  
```c
main()
{
char str[] ="Hello World";
int i=0;
    while(str[i] != '\0'){
        putchar(str[i++];
    }
}
```
### 3. scanf() 함수  
c언어에 있어서 **'standard input function'(표준 입력 함수)** 인 함수이다.  
헤어파일 'stdio.h'(Standard Input Output library, 표준입출력 라이브러리)안에 정의되어 있다.  
scanf 의 의미는 **scan formatted** 이다. 즉, 양식으로 스캔을 해오겠다는 의미이다!  

#### 함수의 형식 지정자 종류  
| **code** | **Meaning** |
|:--------|:--------:|
| %c | 글자 하나하나를 읽음 (single character) |
| %d | 10진수로 된 정수형 (decimal integer)|
| %i | 10진수,16진수, 8진수로 된 정수형 (decimal, hexadecimal, or octal integer)|
| %e | 실수 (a floating point value)|
| %f | 실수 (a floating point value)|
| %g | 실수 (a floating point value)|
| %o | 8진수로 된 부호가 없는 정수 (an octal integer)|
| %s | 문자열 (a string)|
| %u | 10진수로 된 부호가 없는 정수 (an unsigned decimal integer)|
| %[] | 문자들 (a string of words)|

#### scanf() input 에 따라 다르게 출력되는 경우  
```c
scanf("%3d %3d", &a, &b);
```
위의 코드에서, 
| **input값** | **출력값** |
|:--------|:--------:|
|1 4|a에는 1, b에는 4|
|123 456| a에는 123, b에는 456|
|1234567| %뒤에 3으로 '공간'을 세개씩 할당해놓았기 때문에, a=123, b=456 으로 7은 무시된다|
|123 4 56| a=123, b=4 로 할당됨. 빈칸은 data item separator 역할을 한다!|

### 4. swtich문  
- 모든 타입이 되는것은 아니다  
- default case 는 무조건 있어야한다  

### 5. scanf()와 getchar() 의 차이  
- scanf(): 변수에 값을 입력받을 때 사용함  
- getchar(): 표준 입력으로부터 아무 값이나 한 개 읽어올 때 사용함 (**오직 1개만!**)  

### 6. 다양한 loop  
- for loop 에서, i와 같은 control variable 의 시작 값은 끝나는 값 보다 작아야한다.  
- n번 loop가 실행되면 --> 실제로는 **n-1번** 돌게 된다.  

#### 무한반복문  
- 조건문이 없는 for loop 는 'infinite loop'(무한반복문) 이라고 불리운다.  

#### 감시값 제어 반복문 (sentinel-controlled loop)  
- 감시값이라고 부르는 특정 값들의 하나가 나올 때까지 반복문 몸체(body)가 반복적으로 실행되는 루프이다!  
- 예를 들어 'stop'이 scan 될 때 까지만 돌게 하는 등.. 의 루프를 '감시값 제어 반복문'이라고 부른다.  
- indefinite repitition 루프이다.  

#### 계수기 제어 반복문 (count-controlled loop)  
- 말 그대로 count 를 따로 해주면서 loop 를 돌리는 반복문이다.  
- 보통 cnt, count 등으로 .. 또는 총합을 구하려고 할 때에는 sum 을 변수로 선언하고, 값을 초기화 한 후에 loop 문 안에서 더해지도록 한다.  
```c
int sum = 0;
for (int count = 1; count <= 100; count ++)
    if (count%2 == 0) sum = sum + count; //count가 2로 나누어 떨어질 때에만 총합 값에 count를 더하도록 한다. 
```
### 7. loop 에서 개인적으로 헷갈렷던 부분  
```c
main()
{
    int count=5;
    while(count-- >0)
    printf("%d",count);
}
```
출력값: 4 3 2 1 0

```c
main()
{
    int count=5;
    while(--count >0)
    printf("%d",count);
}
```
출력값: 4 3 2 1

#### for(; ;)  
- infinity loop를 만들고자 할 때 쓰는 조건문이다. 

### 8. continue 문  
- unstructured 프로그래밍으로 고려된다!  
- 루프 안에서 일정 부분을 'skip' 하기 위해서 쓰인다.  

### 9. do loop 문  
do 문은 while 조건문이 맨 마지막에 나오고, **반드시 세미콜론으로 끝내야한다**.  
```c
name =0;
do
{
name = name+1;
printf("my name is jhon\n");
}
while(name==1); //세미콜론 붙이기! 그냥 베이직한 while문에서는 세미콜론이 안들어간다. do 문에서만 ! 
```
### 10. for 문 예제  
```c
main()
{
    //(a) 1,2,4,8,16,32 
    
    for(int i=1;i<=32;i=i*2){
    printf("%d, ",i);
    }
    
    printf("\n"); //엔터

    //(b) 1,3,9,27,81,243
    for(int i=1;i<=243;i=i*3){
       printf("%d, ",i);
       }
    
    printf("\n"); //엔터

    //(c) -4,-2,0,4
    for(int i=-4;i<=4;i=i+2){
    printf("%d, ",i);
    }
    
    printf("\n"); //엔터

    //(d) -10,-12,-14,-18,-26,-42
    int cnt = 1;
    for(int i=-10;i>=-10;)
    {
        printf("%d, ",i);
        for(i=-12;i>=-42;i-=cnt)
        {
            printf("%d, ",i);
            cnt=cnt*2;
        }
    }
}
````

### 11. Array 개념  
- 배열 안의 요소들의 데이터타입은 **모두 같아야함**  
- 배열이 선언되면, 그 요소들을 **자동으로 0으로 설정한다**  
- char type 변수는 배열에서 subscript 로 쓰일 수 없다. unsigned long int type은 가능하다.  
- 다배열의 경우에는 그 배열의 크기를 **무조건 명시**해주어야 한다.  
- expression 을 subscript 로 사용하려고 한다면, 항상 그 값은 0 보다 커야한다.  
- 배열의 크기는 **최대 4차원**까지이다.  

- **malloc function**을 사용하여 만들어진 배열은 **'포인터 변수'**이다.  
- **sorting** is the process of arranging the elements of an array in order.  

#### 잘못된 배열 예시  


