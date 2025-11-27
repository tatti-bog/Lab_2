## Отчет по лабораторной работе № 2

#### № группы: `ПМ-2502`

#### Выполнила: `Богоявленская Татьяна Сергеевна`

#### Вариант: `1`

### Cодержание:

- [Задача 1](#1-задача-1)
- [Задача 2](#2-задача-2)
- [Задача 3](#3-задача-3)
- [Задача 4](#4-задача-4)

### 1. Задача  1
Ваша задача – посмотреть, какие значения принимает последовательность при разных a0 и n, вывести закономерность, по которой строится последовательность и запрограммировать ее самостоятельно.


первые 10 членов последовательности при а0 = 1 

3, 5, 15, 17, 51, 53, 159, 161, 483, 485


первые 9 членов последовательности при а0 = 4

12, 14, 42, 44, 132, 134, 402, 404, 1212


#### 1. Алгоритм

##### Алгоритм выполнения программы:

   
#### 2. Программа
```java
import java.util.Scanner;

public class Main {
    public static Scanner in = new Scanner(System.in);
    public static void main(String[] args) {
        System.out.println("Какой элемент нулевой: ");
        int a = in.nextInt();
        System.out.println("Сколько элементов последовательности вывести: ");
        int n = in.nextInt();

        for (int i = 1; i <= n; i++) {

            if (i % 2 == 0) {
                a += 2;
            }

            else {
                a *= 3;
            }

            System.out.print(a);

            if (i < n) {
                System.out.print(", ");
            }
        }
    }
}
```
#### 3. Анализ правильности решения

Программа работает корректно на всем множестве решений с учетом ограничений.

1. Тест на ``:

    - **Input**:
        ```
       
        ```

    - **Output**:
        ```
       
        ```

### 2. Задача 2
Среди натуральных чисел, не превышающих 10^8, найдите количество чисел, соответствующих маске “7?*2?”, которые являются простыми.

"?" заменяет ровно одну любую цифру

"*" заменяет последовательность цифр любой длины (включая пустую последовательность)

100 000 000 = 10^8 

=> максимальное число по маске это 


 79 999 929
 
 7? ___ _2?
 
 т.е после ? и до двойки может быть максимум 4 цифры  
 всего цифр в числе от 4 до 8
 
#### 1. Алгоритм

##### Алгоритм выполнения программы:

#### 2. Программа
```java
public class Main {
    public static void main(String[] args) {
        int count = 0;

        for (int len = 4; len <= 8; len++) {

            for (int digit1 = 0; digit1 <= 9; digit1++) {

                for (int digit2 = 0; digit2 <= 9; digit2++) {

                    int dlina_sr = len - 4; // from 0 to 4

                    long chislo_min_seredina = (long)(7 * Math.pow(10, len - 1) + digit1 * Math.pow(10, len - 2) + 2 * 10 + digit2); // число целиком с минимальным значением середины
                    double maks_seredina = (Math.pow(10, dlina_sr) - 1) * 100; // максимальное значение середины
                    long chislo_maks_seredina = chislo_min_seredina + (long)(maks_seredina); // максимальное значение числа с такой серединой

                    for (long num = chislo_min_seredina; num <= chislo_maks_seredina; num += 100) { //цикл от минимального значения числа с такой серединой и цифрами на местах до максимального
                                                                                    //идем с шагом 100 тк последние две цифры в числе постоянные для конкретной середины
                        if (isPrime(num)) {
                            count++;
                        }
                    }
                }
            }
        }

        System.out.println("Количество чисел: " + count);
    }

    public static boolean isPrime(long n) {
        if (n < 2) return false;
        if (n == 2) return true;
        if (n % 2 == 0) return false;

        for (long i = 3; i * i <= n; i += 2) {
            if (n % i == 0) return false;
        }
        return true;
    }
}
```
#### 6. Анализ правильности решения

### 3. Задача 3

#### 1. Алгоритм

##### Алгоритм выполнения программы:

1. **Ввод данных:**  
  
2. **Корректность ввода:**
   
#### 2. Программа
```java
import java.util.Scanner;
public class Main {
    public static Scanner in = new Scanner(System.in);
    public static void main(String[] args) {
        System.out.println("Какой долг по кредиту: ");
        int d = in.nextInt();
        System.out.println("Какой процент по кредиту: ");
        int r = in.nextInt();
        System.out.println("Какой платеж по кредиту: ");
        int p = in.nextInt();

         if (p <= d*r/100.0) {
             System.out.println("NO");
             return;
         } // если платеж меньше начисленных процентов кредит не выплатить сразу no

        int months = 0;
        double currentDebt = (double)(d);
        double lastPayment = 0;

        while (currentDebt > 0) { 
            currentDebt = currentDebt * (1 + r / 100.0);
            months++;

            if (currentDebt <= p) {
                lastPayment = currentDebt;
                currentDebt = 0;
            }

            else {
                currentDebt -= p;
                lastPayment = p;
            }

            if (months > 1000) {
                System.out.println("NO");
                return;
            }
        }

        System.out.println(months + " " + Math.round(lastPayment));

    }
}
```
### 4. Задача 4

#### 1. Алгоритм

##### Алгоритм выполнения программы:

1. **Ввод данных:**  
  
2. **Корректность ввода:**
   
#### 2. Программа
```java
