[![Open in Codespaces](https://classroom.github.com/assets/launch-codespace-2972f46106e565e64193e422d61a12cf1da4916b45550586e14ef0a7c637dd04.svg)](https://classroom.github.com/open-in-codespaces?assignment_repo_id=24051483)
# Практична робота "Масиви, вирази, керування виконанням програми"

## В рамках практичної роботи ви маєте зробити наступне:
1. модифікувати стартовий код таким чином, щоб метод ```Calculate``` класу ```Exercise``` містив код обчислення значення у відповідності до обраного вами завдання (у разі необхідності можна додавати до класу нові приватні методи)
2. рядок, який виводиться у результаті виконання методу ```main``` класу ```TestResult``` теж слід скоригувати у відповідності до специфіки завдання
3. **README.MD репозиторію має містити опис обраного вами завдання** (краще - з картинками та форматуванням :blush:)!
4. **УВАГА!** Не слід вважати, що завдання дуже прості! Вам необхідно подбати про:
    * **оптимізацію програми - обрати оптимальні з точки зору обсягу використовуваної пам'яті типи даних**
    * **іменування змінних і констант у відповідності до рекомендацій**
    * **javadoc-коментарі для класу ```Exercise```, які пояснюють що саме обчислюється і які вихідні дані для цього потрібні**
5. здати завдання. **Нагадую, що здаючи завдання через Google Classroom, слід вказати посилання на створений для вас репозиторій!**

## Список завдань (Обирала за номером в журналі)
8. Відсортувати одновимірний масив, розбиваючи його на групи елементів по 1, 2, 4, 8 і т.д. Дозволяється використовувати допоміжний масив.

## 1. Код класу Exercise.java (у папці src/domain)

```java
package domain;

import java.util.List;

/**
 * @author Kozlova
 */
public class Exercise {

    /**
     * @param numbers 
     * @param delimiter 
     * @return 
     */
    public static String Calculate(int[] numbers, char delimiter) {
        if (numbers == null || numbers.length == 0) {
            return "";
        }
        
        StringBuilder sb = new StringBuilder();
        for (int i = 0; i < numbers.length; i++) {
            sb.append(numbers[i]);
            if (i < numbers.length - 1) {
                sb.append(delimiter).append(" ");
            }
        }
        return sb.toString();
    }

    /**
     * @param numbers
     * @param delimiter 
     * @return 
     */
    public static String Calculate(List<Integer> numbers, String delimiter) {
        if (numbers == null || numbers.isEmpty()) {
            return "";
        }
        
        StringBuilder sb = new StringBuilder();
        for (int i = 0; i < numbers.size(); i++) {
            sb.append(numbers.get(i));
            if (i < numbers.size() - 1) {
                sb.append(delimiter);
            }
        }
        return sb.toString();
    }
}
```
## 2. Код класу TestResult.java (у папці src/test)

```java
package test;

import domain.Exercise;
import java.util.ArrayList;
import java.util.List;

/**
 * @author Kozlova
 */
public class TestResult {

    public static void main(String[] args) {
        System.out.println("Method Overloading");
        System.out.println("Text representation of numbers\n");

        int[] arrayData = {01, 31, 20, 0, 8};
        char charSep = '-';
        String arrayResult = Exercise.Calculate(arrayData, charSep);
        
        System.out.println("Test 1 (Array + char):");
        System.out.println("Result: " + arrayResult);
        System.out.println("-------------------------");

        List<Integer> listData = new ArrayList<>();
        listData.add(67);
        listData.add(228);
        listData.add(43);
        String stringSep = " * ";
        String listResult = Exercise.Calculate(listData, stringSep);
        
        System.out.println("Test 2 (List + String):");
        System.out.println("Result: " + listResult);
        System.out.println("-------------------------");
    }
}
```

## 3. Результат виконання програми
![result](https://github.com/ppc-ntu-khpi/java-3-kkkseeekk/blob/master/result.png)
