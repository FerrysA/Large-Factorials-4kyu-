# Large-Factorials-4kyu-
# 18.11.2022
# Вычисление факториала больших чисел
# [cылка на задание](https://www.codewars.com/kata/557f6437bf8dcdd135000010/train/java)
# Код:
``` java

public static String Fact(int n) {
        if (n == 0) {
            return "1";
        }

        return Pro(Integer.toString(n), Fact(n - 1));
    }
////////// вспомогательные функции
  public static String Pro(String a, String b) {
        int n = a.length();
        int m = b.length();
        int k = 0;
        String res = "0";
        int vume = 0;
        int x = 0;
        int y = 0;
        int z = 0;
        String delta = "0";


        for (int i = 1; i <= m; i++) {

            delta = pro(a, Character.toString(b.charAt(m - i)));


            for (int j = 1; j < i; j++) {
                delta += "0";
            }


            res = Sum(delta, res);


        }

        if (vume != 0) {
            res += vume;
        }


        return res;
    }

    public static String pro(String a, String b) {
        int n = a.length();

        int k = 0;
        String res = "";
        int vume = 0;
        int x = 0;
        int y = 0;
        int z = 0;


        for (int i = 1; i <= n; i++) {
            x = Character.digit(a.charAt(n - i), 10);
            y = Character.digit(b.charAt(0), 10);
            z = x * y;
            res += (z + vume) % 10;
            vume = (z + vume) / 10;

        }

        if (vume != 0) {
            res += vume;
        }

        String tmp = res;
        k = res.length();
        res = "";
        int cont = 0;
        for (int i = 0; i < k; i++) {
            if (tmp.charAt(k - i - 1) == '0' && cont == 0) {
                continue;
            }
            cont = 1;
            res += Character.toString(tmp.charAt(k - i - 1));

        }

        return res;
    }

    public static String Sum(String a, String b) {
        int n = a.length();
        int m = b.length();
        int k = 0;
        String res = "";
        int vume = 0;
        int x = 0;
        int y = 0;
        int z = 0;
        int zres = 0;
        int min = Math.min(n, m);


        for (int i = 1; i <= min; i++) {
            x = Character.digit(a.charAt(n - i), 10);
            y = Character.digit(b.charAt(m - i), 10);
            z = x + y;
            res += (z + vume) % 10;
            vume = (z + vume) / 10;

        }
        if (n > m) {
            for (int i = m + 1; i <= n; i++) {
                x = Character.digit(a.charAt(n - i), 10);
                y = 0;
                z = x + y;
                res += (z + vume) % 10;
                vume = (z + vume) / 10;

            }

        }
        if (m > n) {
            for (int i = n + 1; i <= m; i++) {
                y = Character.digit(b.charAt(m - i), 10);
                x = 0;
                z = x + y;

                res += (z + vume) % 10;
                vume = (z + vume) / 10;

            }

        }
        if (vume == 1) {
            res += vume;
        }

        String tmp = res;
        k = res.length();
        res = "";
        int cont = 0;
        for (int i = 0; i < k; i++) {
            if (tmp.charAt(k - i - 1) == '0' && cont == 0) {
                continue;
            }
            cont = 1;
            res += Character.toString(tmp.charAt(k - i - 1));

        }

        return res;
    }

```
# Понравившееся решение(Автор IvoRama)
```java
import java.util.ArrayList;

public class Kata
{

 public static String Factorial(int n) {
    if(n<0){
      return null;
    }
    if(n ==0){
      return 1+"";
    }
    ArrayList<Long> results = new ArrayList<>();
    int value = n; 
    while(value > 0){
      results.add((long) (value % 10));
      value= value/10;
    }
    
    
  
    for(int i = n-1 ; i > 1 ; i--){
      ArrayList<Long> temp = new ArrayList<>();
      Long carry = (long) 0;
      for(Long j: results){
        long prod = i * j + carry;
        temp.add( (prod%10));
        carry = prod /10;
      
      }
      if(carry!=0){
        if(carry < 10){
          temp.add(carry);
        }
        else{
          while(carry > 0){
            temp.add((long) (carry % 10));
            carry= carry/10;
          }
        }
      }
      results = temp;
    }
    
    String result = "";
    for(Long v: results){
      result= v + result;
    }
    return result;
  
    }

}
    
