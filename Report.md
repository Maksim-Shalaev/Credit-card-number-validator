# Отчёт о тестировании Credit card number validator
## Краткое описание
24/03/2021 - 24/03/2021 было проведено функциональное тестирование приложения **Credit card number validator**.    
 
На тестирование затрачено: 4 часа    
 
В результате тестирования выявлены следующие дефекты:    

* [Валидные карты Diners Club - Carte Blanche с 14 значным номерами признаны невалидными](https://github.com/Maksim-Shalaev/Credit-card-number-validator/issues/1)
* [Валидные карты Diners Club - International с 14 значным номерами признаны невалидными](https://github.com/Maksim-Shalaev/Credit-card-number-validator/issues/2)
* [Валидные карты American Express с 15 значными номерами признаны невалидными](https://github.com/Maksim-Shalaev/Credit-card-number-validator/issues/3)
* [Валидные карты VISA с 19 значными номерами признаны невалидными](https://github.com/Maksim-Shalaev/Credit-card-number-validator/issues/4)
* [Валидные карты DISCOVER с 19 значными номерами признаны невалидными](https://github.com/Maksim-Shalaev/Credit-card-number-validator/issues/5)
* [Валидные карты JCB с 19 значными номерами признаны невалидными](https://github.com/Maksim-Shalaev/Credit-card-number-validator/issues/6)   

## Описание процесса тестирования
В процессе тестирования использовались следующие артефакты:  
 
* [Руководство по установке IntelliJ IDEA](https://github.com/netology-code/javaqa-homeworks/blob/master/intro/idea.md)
* Исходный код
    
		`public class Main {   
            public static void main(String[] args) {
		     // TODO: подставлять номер карты нужно сюда между двойными кавычками, без пробелов   
		     String number = "5351719427810741";  
    	     System.out.println(String.format("Result is %s", isValidCardNumber(number) ? "OK" : "FAIL"));
             }

            public static boolean isValidCardNumber(String number) {
             if (number == null) {
              return false;
             }

             if (number.length() != 16) {
              return false;
             }

             long result = 0;
             for (int i = 0; i < number.length(); i++) {
              int digit;
              try {
                digit = Integer.parseInt(number.charAt(i) + "");
              } catch (NumberFormatException e) {
                return false;
              }

              if (i % 2 == 0) {
                digit *= 2;
                if (digit > 9) {
                  digit -= 9;
                }
              }
              result += digit;
             }

             return (result != 0) && (result % 10 == 0);
            }
          }

В качестве тестовых данных использовались данные:   

* [Генератор номеров карт](https://www.freeformatter.com/credit-card-number-generator-validator.html) 
  
* **Diners Club- Cart Blanche (14 значные номера):**
 * 30043414279277
 * 30332778337536
 * 30578793561902
* **Diners Club- International (14 значные номера):**
 * 36908313829584
 * 36840782634262
 * 36306588991504
* **American Express (15 значные номера):**
 * 373398696534194
 * 349102925513875
 * 345619114342315
* **VISA (19 значные номера):**
 * 4716698541456130142
* **DISCOVER (19 значные номера):**
 * 6011520576361701007
* **JCB (19 значные номера):**
 * 3531696330842162258
  
   
Тестирование производилось в следующем окружении: 

* Windows 7   
* Java 11.0.10  
* Google Chrome 89.0.4389.90