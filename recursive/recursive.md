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

