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
- scanf(): 변수에 값을 입력받을 때 사용함, **빈칸**이 포함된 줄은 모두 읽을 수 없음.  
- getchar(): 표준 입력으로부터 아무 값이나 한 개 읽어올 때 사용함 (**오직 1개만!**), 빈칸도 읽음    

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
- Array는, '값 과 변수' 를 지닌 **data structure** 이다.  
- 배열 안의 요소들의 데이터타입은 **모두 같아야함**  
- 배열이 선언되면, 그 요소들을 **자동으로 0으로 설정한다**  
- char type 변수는 배열에서 subscript 로 쓰일 수 없다. unsigned long int type은 가능하다.  
- 다배열의 경우에는 그 배열의 크기를 **무조건 명시**해주어야 한다.  
- expression 을 subscript 로 사용하려고 한다면, 항상 그 값은 0 보다 커야한다.  
- 배열의 크기는 **최대 4차원**까지이다.  
- String variables cannot be used with the assignment operator.


- **malloc function**을 사용하여 만들어진 배열은 **'포인터 변수'**이다.  
- **sorting** is the process of arranging the elements of an array in order.  
  
  
#### 잘못된 배열 예시  
1.  
수정전 `int m[2,4]={(0,0,0,0)(1,1,1,1)};`  
수정후 `int m[2,4]={{0,0,0,0},{1,1,1,1}};`  
  
2. 
수정전 `float result[10]=0;`  
수정후 `float result[10]={0};`  

3.  
수정전 `char str1[4]="GOOD";`  
수정후 `char str1[5]="GOOD";`  
마지막에 '\0' 값이 string 배열에 입력되어있기 때문에 총 5 사이즈로 설정해주어야한다.  
  
### 12. 수학기호  
- character 변수에는 수학기호를 쓸 수 없다.  

### 13. ASCII 코드  
- 대문자가 소문자보다 앞선다.  
- 개수는 128개 인데, 특수문자까지 합치면 더 많다.  
- 아스키 코드값은 문자를 **1대1로 대응시킨 숫자**이다.  

-ASCII 함수: 문자열을 알파벳 순서로 정렬시키는데 쓰인다. 

### 14. C언어 문자열처리 라이브러리  
1. **strlen**  
    - string length를 의미한다.  
    - 문자열의 길이를 알려줌  
    - `unsinged int strlen(char* str);`
    
2. **strcmp**  
    - string compare 를 의미한다.  
    - 문자열을 비교해주고, return 값으로 그 비교 결과를 나타내준다.  
    - `int strcmp(const char* str1, const char* str2);`  
    - 리턴값 0: 동일한 문자열이다.  
    - 리턴값 1: str1이 str2보다 사전순서로 볼 때 뒤에 있다.  
    - 리턴값 -1: str1이 str2 보다 사전순서로 볼 때 앞에 있다.  

3. **strcpy**  
    - string copy  
    - `char* strcpy(char* dest, char* src);`  
    - src의 문자열을 dest로 복사시킴 
    - src는 char형 포인터여서, src의 주소로 가서 문자 하나하나 dest에 복사시키는 식으로 작동한다.  
    - dest의 배열 크기는 src보다 같거나 커야한다!!  
   **strncpy**
    - string number copy  
    - 마지막에 숫자를 parameter로 추가하여 src에서 원하는 범위의 문자열을 dest에 복사시키도록 하는 함수이다.  
4. **strncat**  
    - string concat  
    - `char* strncat(char* destination, char* source, size_t num);`  
    - destinaiont : 배열을 가르키는 포인터이다. C 문자열을 보관하며(null \0 포함), 합쳐진 문자열이 들어갈 만큼 충분한 크기를 가지고 있어야 한다!  
    - source: destination 끝에 덧붙여질 문자열이다  
    - num: source 에서 붙일 문자의 (최대) 개수이다.  
    - **총 3개의 parameter** 를 가질 수 있다!  
    
### 15. gets()  
- input function 이다.  
- 오직 string parameter 를 가진다.  
- 하나의 문자열만을 가져올 수 있다.  
- 예. `gets(s1,s2)` 는 불가.  

### 16. atoi, atof, atol  
- <stdlib.h> 헤더파일(Standard Library)이 필요하다!  
- atoi: 문자열을 정수 타입으로(char --> int)  
- atof: 문자열을 실수 타입으로(char --> float)  
- atol: 문자열을 long 정수 타입으로(char --> long int)  


### 17. strstr  
- <string.h> 헤더파일 필요  
- `char*strstr(char* str1, const char*str2);`  
- str1 에서 str2와 일치하는 문자열이 있는지 확인하는 함수!  
- str1 에 str2와 일치하는 문쟈열이 있으면 --> **해당 위치의 포인터를 반환함!!**  
- 없으면 --> **null값 반환**  
```c
char s1[] = "ANIL KUMAR GUPTA";
char s2[] = "KUMAR";
printf(strstr(s1,s2)); //s1에 s2와 일치하는 문자열이 있으면 그 위치값 반환

output:
KUMAR GUPTA
```

```c
main()
{
    char str1 []="Hi this is minseung's github";
    char str2 []="github";
    
    char* ptr = strstr(str1, str2); //반환되는 값이 주소이기 때문에 포인터로 받아줌
    if(ptr != NULL){ //ptr주소의 값으로 null 반환이 안되었다면, 즉 str1에서 str2와 일치하는 문자열을 발견했다면!
        strncpy(ptr, "dev blog", 8); //dev blog 문자열을 ptr 에 하나하나 복사시킨다, 즉 기존의 github --> dev blog
        printf("%s\n",str1);
        
    }
    // 출력값: Hi this is minseung's dev blog
}
```

### 18. puts()  
- printf() 함수 대신 쓰일 수 있음.   

### 19. gets(string)  
- read a line of string  

### 20. User-Defined Function 개념  
- C에서의 함수는 무조건 한 argument 는 가지고 있어야한다.  
- 'function'은 메인함수 이후, 그리고 메인함수 외부에서 선언된다.  
- return type은 기본적으로 int 로 설정된다.  
- function call 에서 불리워지는 parameter(매개변수)는 **'actual parameter'** 라고 불린다.  
- function 내부에서 선언되면 --> local(지역변수, internal),  
  외부(before main function)는 global(전역변수, external)  
- **prototype** : the region where a variable is actually variable for use  
- **recursive function (재귀함수)**: 스스로를 호출하는 함수  

#### function 선언 방법 관련  
잘못된 예:  
1. actual parameter를 void 로 입력받을 때에는 한번만!   
수정전: `void fun(void, void);`  
수정후: `void fun(void);`  

2.  
수정전: `int fun (int a,b);`  
수정후: `void fun(int a, int b);`   

3. data type 만 쓰는 것 가능  
예: `void fun(int, float, char);`  

### 21. 매개변수를 전달하는 두가지 방법  
1. Pass by value ( call by value )  
2. Pass by pointers ( call by pointers )  

### 22. static 변수와 auto 변수 (자동변수)  
1. **static**변수  
    - storage class(기억 영역 분류)를 명시해주어야함  
    - 디폴트 값으로 0 을 output 값으로 지정함  
    - 눈에 보이는 변수이다  
    - 다른 함수들 간에서도 그 값을 유지한다.  
    - static 변수는 컴파일러에 의해 첫번째로 컴파일 되어야 한다.  
    - 어디에서 어떻게 선언되었느냐에 따라 전역, 지역 변수가 될 수 있다.  
2. **auto**변수  
    - storage class가 디폴트값으로 지정된다.  
    - 지정이 안되면 디폴트로 'garbage'값을 output으로 지정한다.  
    - 선언된 곳에서는 가시적이다.  
    - 값이 유지된다.  
    - 스태틱 변수 다음으로 컴파일 된다.  
    - auto 변수는 **항상 지역변수**이다.  


### 23. Pointer 의 정의  
- pointer란, **"derived data type in C"** 이자, **"특정 value 의 메모리 주소값을 지니는 것"**이다.  
- operator "&"의 역할:  
    앞의 변수의 주소를 return 해준다.  
- 안되는 것:  
    `&125` :상수를 포인터로 포인트 할 수 없다.  
    `int x[10]`
     `&x`       : array 이름을 포인트 할 수 없다.  
     `&(x+y)`: expression을 포인트 할 수 없다.
- **pointer에서의 바이트는 다르다!**  
    - 원래는 integer(4byte), float(4byte), character(1byte) 이다!  
    - `sizeof(int*)` = 8byte  
    - `sizeof(float*)` = 8byte  
    - `sizeof(char*)` = 8byte  
- pointer에 쓰이는 **asterisk**의 용도  
    1. 포인터를 선언할 때  
    2. 해당 주소에 값이 접근하는 용도  
    ```c
    main()
    {
    int a=5;
    int* address= &a;
    printf("문자값은: %d, 포인터값은:%x, 포인터를 통해 표현하는 문자값:%d\n", a, address, *address);
    
    // 출력값:문자값은: 5, 포인터값은:efbff53c, 포인터를 통해 표현하는 문자값:5
    }
    ```
