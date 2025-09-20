```java  
#Question 1
import java.util.Scanner;  
public class Tutorial1Q1 {  
    public static void main(String[] args){  
        Scanner input = new Scanner(System.in);  
        System.out.println("Enter Age: ");  
        int va = input.nextInt();  
        if (va>=18){  
            System.out.println("Eligible to vote");  
        }  
        else{  
            System.out.println("Not eligible to vote");  
        }  
        input.close();  
    }  
}

#Question 2
  
import java.util.Scanner;  
  
public class Tutorial1Q2 {  
    public static void main(String[] args){  
        Scanner input = new Scanner(System.in);  
        System.out.println("Enter a number: ");  
        int no = input.nextInt();  
        if (no%2==0){  
            System.out.println("Number is even");  
            input.close();  
        }  
        else{  
            System.out.println("Number is odd");  
        }  
  
    }  
}

#Question 3

import java.util.Scanner;  
public class Tutorial1Q3 {  
    public static void main(String[] args){  
        Scanner scanner = new Scanner(System.in);  
        System.out.println("Enter a number: ");  
        int no = scanner.nextInt();  
        if (no%3==0){  
  
            System.out.println("it is divisible by 3");  
        }  
        else{  
            System.out.println("It is NOT divisible by 3");  
        }  
        scanner.close();  
    }  
}

#Question 4

import java.util.Scanner;  
  
public class Tutorial1Q4 {  
    public static void main(String[] args){  
        Scanner input = new Scanner(System.in);  
        System.out.println("Enter sentence: ");  
        String sen = input.nextLine();  
        String[] words = sen.trim().split("\\s+");  
        for (String word : words){  
            System.out.println(word);  
        }  
        input.close();  
    }  
}
```
