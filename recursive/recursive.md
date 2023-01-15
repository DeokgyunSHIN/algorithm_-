# 재귀 

> 재귀는 어떤 사건이 자기 자신을 포함하고 있거나 또는 자기 자신을 사용하여 정의하고 있을 때 이를 재귀적이라고 한다.


예시) 팩토리얼로 재귀적으로 정의하기 

```java
 public class Factorial {

	static int factorial(int n) {
		if(n>0) {
			return n* factorial (n-1);
		}else {
			return 1;
		}
	}
 
	public static void main(String[] args) {
		Scanner scan=new Scanner(System.in);
		
		System.out.print("정수를 입력하시오:  ");
		int n=scan.nextInt();
		
		System.out.println(n+"의 팩토리얼은 "+factorial(n)+"입니다.");
	}
 }
```

3의 팩토리얼값을 재구적으로 구하는 과정 

factorial(3); 

▼

▼

n=3

```
static int factorial(int n) {
 if(n>0) {
   return n* factorial (n-1);   // 자기 자신 호출 
   }else {
    return 1;
 }
}
```
▼

▼

n=2
```
static int factorial(int n) {
 if(n>0) {
   return n* factorial (n-1);   // 자기 자신 호출 
   }else {
    return 1;
 }
}
```

|스택|
|---|
|3|

▼

▼

n=1
```
static int factorial(int n) {
 if(n>0) {
   return n* factorial (n-1);   // 자기 자신 호출 
   }else {
    return 1;
 }
}
```

|스택|
|---|
|2|
|3|

▼

▼

n=0
```
static int factorial(int n) {
 if(n>0) {
   return n* factorial (n-1);   // 자기 자신 호출못함 n이 0이라서 조건문을 못탐 
   }else {
    return 1;
 }
}
```

|스택|
|---|
|1|
|2|
|3|

▼

▼

|스택|
|---|
|1|
|2|
|3|

return 1*1;

▼

▼

|스택|
|---|
|2|
|3|

return 1*2;

▼

▼

|스택|
|---|
|3|

return 2*3;

▼

▼

|스택|
|---|
|없음|

<br>
<br>
<br>

### 직접 재귀와 간접 재귀 

> 직접 재귀는 자기 자신을 같은 메소드를 호출하는것
>
> 간접 재귀는 다른 메소드를 통해 자기 자신과 같은 메소드를 호출한은 것.

#### 직접 재귀 

|메소드a|
|-----|
|a();|

▼

▼


|메소드a|
|-----|
|b();|


#### 간접 재귀 

|메소드a|
|-----|
|b();|

▼

▼


|메소드b|
|-----|
|a();|

▼

▼


|메소드a|
|-----|
|b();|
