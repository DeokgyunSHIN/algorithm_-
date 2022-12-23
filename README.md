# 알고리즘 

### 순열 
 > 팩토리얼 
 > > 1에서 n까지 모든 자연수의 곱 (n!)
 > > 
 > > 예) 1! = 1 / &nbsp; &nbsp; &nbsp;  2! = 2x1   &nbsp; &nbsp; &nbsp;   /    &nbsp; &nbsp; &nbsp;   5!= 5x4x3x2x1 
 > > 
 > > 공식 : n!= n(n-1)(n-2)... 1
 > > 
 > >  코드 

```java
     
public class Main {     
       public static  int factorial(int number){
        if(number<=1){
            return 1;
        }else{
            return number*factorial(number-1);
        }
    }
    
    public static void main(String[] args) {
     int number=5;
        System.out.println(number+"!= "+ factorial(number));
    }
  }

```

  1. 처음 factorial 이 불리게된 이유는 main 함수에서 호출 했기 때문이다.
  2. number의 값이 5이고 numberd은 1보다 크기때문에 else 문을 탄다.
  3. 여기서 처음 호출된 factorial(5)는 사용되지 않고 스택에 쌓이기 된다.
       
       스택 
       ---|
      | factorial(5) |
      
  4. factorial(5)가 호출한 factorial(4)가 실행된다. 
  
      스택 
       ---|
      | factorial(4) |
      | factorial(5) |
      
        👇
        
        👇
        
        👇
        
        
      스택 
       ---|
      | factorial(2) |
      | factorial(3) |
      | factorial(4) |
      | factorial(5) |
 
 factorial(2)가 호출한 factorial(1) 실행된다.
 
 5. number은 1과 같기 때문에 if 문을 타고 1를 리턴한다.
 6. factorial(1)가 종료되면서 스택에 가장 위에 있는 factorial(2)가 실행된다.
 7. 마지막 factorial(1)에서 리턴 값이 1에서 스택에 있는 데이터 값 n을 곱해서 스택에 남아 있는 데이터가 있을 때까지 곱한다.
 8.  5! 의 대한 값을 다 구하면 main 함수에서 출력한다.


 > 순열 
 > > 순서를 정해서 나열한다.
 > > 
 > > 순열이란 n 개의 값 중에서 r 개의 숫자를 모든 순서대로 뽑는 경우를 말합니다.
 > > 
