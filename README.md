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
 
 5.  number은 1과 같기 때문에 if 문을 타고 1를 리턴한다.
 6.  factorial(1)가 종료되면서 스택에 가장 위에 있는 factorial(2)가 실행된다.
 7.  마지막 factorial(1)에서 리턴 값이 1에서 스택에 있는 데이터 값 n을 곱해서 스택에 남아 있는 데이터가 있을 때까지 곱한다.
 8.   5! 의 대한 값을 다 구하면 main 함수에서 출력한다.



 > 순열 
 > > 서로 다른 n 계층에 r개를 선택하는 경우의 수를 의미한다.(순서 상관 있음)
 > >  
 > > 공식 
 
  $$ {n}P{r} = \frac{n!}{(n-r)!}  $$
  
  
 > > (Swap을 이용한 ) 순열 코드
 ```java
   public class Practice {
    static int count=0;
    void permutation(int arr[], int depth, int n, int r) {
     if(depth==r){
         for (int i = 0; i <r; i++) {

             System.out.print(arr[i]+" ");
         }
         count++;
         System.out.println();
         return ;
     }
        for (int i = depth; i <n; i++) {
            swap(arr,depth,i);
            permutation(arr, depth+1,n,r);
            swap(arr,depth,i);
        }
    }
    void swap(int arr[] ,int depth, int index){
        int tmp=arr[depth];
        arr[depth]=arr[index];
        arr[index]=tmp;
    }
    public static void main(String[] args) {
        int[] arr = {1, 2, 3, 4};
        Practice p = new Practice();
        p.permutation(arr, 0, 4, 3  );
        System.out.println("경우의 수 : "+count);
     } 
  }
```

swap 함수를 만들어서 배열들의 값을 직접 바꾸는 방법이다.

배열의 첫 값부터 순서대로 하나씩 바꾸며 모든 값을 한번씩 swap 한다.

depth 를 기준으로 인덱스 하여 depth 보다 인덱스가 작은 값들은 그대로 고정하고 

depth 보다 인덱스가 큰 값들만 가지고 다시 swap을 한다.



> 중복 순열 
> > 중복 순열은 중복 가능한 n 계층에서 r 개를 선택하는 경우의 수를 의미한다.
> >
> > 공식

 $$ {n}\prod_{}^{} r = n^r$$
 
> > 코드 
```java 
 public class DoublePermutation {
    public static void permutation(int[] arr, int[] out, int depth, int r){
        if(depth == r){
            for(int num: out) System.out.print(num);
            System.out.println();
            return;
        }
        for(int i=0; i<arr.length; i++){
            out[depth] = arr[i];
            permutation(arr, out, depth+1, r);
        }
    }

    public static void main(String[] args){
        int[] arr = {1, 2, 3};
        int r = 2;
        permutation(arr, new int[r], 0, r);
     }
 } 
```

순열과 중복 순열을 중복의 차이점만 가지고 있다.


 > 원순열 
 > > 원 순열을 원 모양의 데이블에 n개의 원소를 나열하는 경우의 수이다.
 > >
 > > 공식 
 
  $$ \frac{n!}{n} = (n-1)! $$
  
> > 코드 
```java 
 public class  CirclePermutation{
    public static void main(String[] args) {
        int n = 4;
        int result = 1;

        for (int i = 1; i < n; i++) {
            result *= i;
        }
        System.out.println("값 = " + result);
    }
  }
```  
 예를 들어 원 모양의 테이블에 4명을 앉힐려고 한다면 
 
 1에서 시작해서 1234로 앉히던
 
 2에서 시작해서 2341로 앉히던
 
 3에서 시작해서 3412로 앉히던

 4에서 시작해서 4123로 앉히던
 
 원을 돌리면 모두 같다.
 
 그렇기 때문에 위의 공식 처럼 4(n)팩토리얼을 4(n)로 나누어준다면 결과는 6이 나오게된다. 




> 조합 
> > 조합은 서로 다른 n개 중에서 r개를 선택하는 경우의 수 (순서x , 중복x)
> >
> > 공식 

$$ {n}C{r}= \frac{n!}{(n-r)!r!}= \frac{{n}P{r}}{r!} $$

> > 코드 (1,2,3,4 에서 세자리 자연수를 만들기)

```java
  public class Practice {
    void combination(int[] arr, boolean[] visited, int depth, int n, int r) {

        if(r==0){
            for (int i = 0; i <n ; i++) {
                if(visited[i]){
                    System.out.print(arr[i]+" ");
                }
            }
            System.out.println();
            return;
        }

        if(depth==n){
            return;
        }


        visited[depth]= true;
        combination(arr,visited,depth+1,n,r-1);

        visited[depth]=false;
        combination(arr,visited,depth+1,n,r);
    }
    
    public static void main(String[] args) {
        int[] arr = {1, 2, 3, 4};
        boolean[] visited = {false, false, false, false};

        Practice p = new Practice();
        p.combination(arr, visited, 0, 4, 3);
     }
  }
```

> > 중복조합
> > 
> >서로 다른 n개 중에서 r개를 선택하는 경우의 수(순서x, 중복o)
> > 
> > 순서 없이 뽑는 조합과 동일하지만, 이미 뽑은 것을 또 뽑을 수 있다. 즉 중복이 가능하다는 차이점을 가지고 있다.
> >
> >공식 

$$ {n}H{r}={n+r-1}C{r} $$

> > 코드 

```java
  public class Practice2 {
    public static void combination(int[] arr, int[] out, int start, int depth, int r){
        if(depth == r){
            for(int num : out) System.out.print(num);
            System.out.println();
            return;
        }
        for(int i=start; i<arr.length; i++){
            out[depth] = arr[i];
            combination(arr, out, i, depth+1, r);
        }
    }

    public static void main(String[] args){
        int[] arr = {1, 2, 3};
        int r = 2;
        combination(arr, new int[r], 0, 0, r);
      }
  }
```



> 연결리스트 
> > 
> > 연결리스트는 데이터를 링크로 연결해서 관리 하는 자료 구조 이며,각 노드가 데이터와 포인터를 가지고 한 줄로 연결되어 있는 방식의 자료구조이다. 데이터를 담고 있는 노드들이 연결되어      있고, 노드의 포인터가 이전, 다음 노드와의 연결을 담당한다.
> > 
> > 연결 리스트 기본구조 

    헤더(head)         
 |data1 |next |
|------|  ---|         



> > 코드 

``` java

```




> 이진 검색
> 
> > 이진 검색은 요솨 오름차순 또는 내림차순 으로 정렬된 배열에서 검핵하는 알고리즘이며, 이진 검색은 선형 검색보다 좀 더 빠르게 검색 할수 있다는 장점을 가지고 있다.
> >

> > 코드 
``` java 
  import java.util.Arrays;
import java.util.Scanner;

public class Main {
   static int index;
   
    static int findData(int arr[], int data,int left,int right){
        int mid=(left+right)/2;
        if(arr[mid]<data){
            findData(arr,data,mid+1,right);
        }else if(arr[mid]>data){
            findData(arr,data,left,mid-1);
        }else if(left==arr.length|| right==0){
           index=1;
        }else if(arr[mid]==data){
            index= mid;
        }
        return index;
    }
    public static void main(String[] args) {
     Scanner scan=new Scanner(System.in);
        System.out.print("요솟수: ");
        int n= scan.nextInt();
        int arr[]=new int[n];
        for (int i = 0; i <arr.length ; i++) {
            System.out.print("arr["+i+"]: ");
            arr[i]= scan.nextInt();
        }
        System.out.print("검색할 값 : ");
        int data=scan.nextInt();
        int index=findData(arr,data,0,arr.length);
         if(index==-1){
             System.out.println("없는 데이터입니다,");
         }else{
             System.out.println("arr["+index+"]에 있습니다.");
         }
     } 
 }
```

|---|---|---|---|---|---|---|---|---|---|
| 5 | 7 | 15| 28| 29| 31| 39|58| 68| 70|
