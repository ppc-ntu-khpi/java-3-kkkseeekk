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

/**
 * @author Kozlova
 */
public class Exercise {

    /**
     * @param array 
     * @return 
     */
    public static String Calculate(int[] array) {
        if (array == null || array.length == 0) {
            return "";
        }

        int n = array.length;
        int[] temp = new int[n]; 

        for (int size = 1; size < n; size *= 2) {
            
            for (int leftStart = 0; leftStart < n; leftStart += 2 * size) {
                
                int mid = Math.min(leftStart + size, n);
                int rightEnd = Math.min(leftStart + 2 * size, n);
                
                int i = leftStart;
                int j = mid;
                int k = leftStart;
                
                while (i < mid && j < rightEnd) {
                    if (array[i] <= array[j]) {
                        temp[k++] = array[i++];
                    } else {
                        temp[k++] = array[j++];
                    }
                }
                
                while (i < mid) {
                    temp[k++] = array[i++];
                }
                
                while (j < rightEnd) {
                    temp[k++] = array[j++];
                }
            }
            
            for (int i = 0; i < n; i++) {
                array[i] = temp[i];
            }
        }

        StringBuilder sb = new StringBuilder();
        for (int i = 0; i < n; i++) {
            sb.append(array[i]);
            if (i < n - 1) {
                sb.append(", ");
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

/**
 * @author Kozlova
 */
public class TestResult {

    public static void main(String[] args) {

        int[] arrayData = {1, 31, 20, 0, 8, 67, 43}; 

        System.out.println("Practical Work 3");
        System.out.println("Merge Sort");
        
        System.out.print("Source array: ");
        for (int i = 0; i < arrayData.length; i++) {
            System.out.print(arrayData[i] + (i < arrayData.length - 1 ? ", " : ""));
        }
        System.out.println();

        String sortedResult = Exercise.Calculate(arrayData);

        System.out.println("Sorted array: " + sortedResult);
    }
}
```

## 3. Результат виконання програми
![result](https://github.com/ppc-ntu-khpi/java-3-kkkseeekk/blob/master/result.png)

