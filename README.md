## Отчет по лабораторной работе № 3

#### № группы: `ПМ-2402`

#### Выполнил: `Лапин Владимир Евгеньевич`

#### Вариант: `15`

### Cодержание:

- [Постановка задачи](#1-постановка-задачи)
- [Выбор структуры данных](#2-выбор-структуры-данных)
- [Алгоритм](#3-алгоритм)
- [Программа](#4-программа)
- [Анализ правильности решения](#5-анализ-правильности-решения)

### 1. Постановка задачи


> ### Автобусная остановка
>Краткое описание:  
Разработать программу для работы с расписанием автобусов на остановке. Реализовать
функционал добавления и удаления автобусов, управления временем их прибытия, а
также обработки запросов, связанных с расписанием.
Описание функционала
>1. Вывод расписания
Отображение расписания в формате:
НомерАвтобуса1: hh:mm, hh:mm
НомерАвтобуса2: hh:mm, hh:mm
Все моменты времени в расписании упорядочены хронологически.
>2. Добавление времени прихода автобуса
Добавление времени прибытия автобуса по его номеру и времени в формате «hh:mm».
Если автобуса с данным номером ещё нет, он добавляется в расписание. Если указанное время уже есть, оно не добавляется.
>3. Удаление автобуса из расписания
Удаление автобуса с указанным номером из расписания.
>4. Удаление времени прихода автобуса
Удаление конкретного времени прибытия автобуса по его номеру и указанному
времени.
>5. Добавление автобуса с периодическими остановками (по количеству)
Добавление автобуса, который начинает ходить с указанного времени и делает
остановки через заданный интервал (в минутах). Указывается номер автобуса,
время начала, интервал и количество остановок.
>6. Добавление автобуса с периодическими остановками (по времени)
Добавление автобуса, который начинает ходить с указанного времени и делает
остановки через заданный интервал до указанного времени включительно. Указывается номер автобуса, время начала, интервал и конечное время.
>7. Ожидание автобуса человеком
Человек приходит на остановку в указанное время и ждёт автобус с переданным
номером определённое количество минут. Определяет, дождётся ли человек автобуса.
>8. Автобусы на отрезке времени (в пределах суток)
Возвращает номера автобусов, которые приезжают на остановку в указанный отрезок времени (без повторений). Гарантируется, что отрезок времени находится в
пределах одних суток.
>9. Автобусы на отрезке времени (через полночь)
Возвращает номера автобусов, которые приезжают на остановку в указанный отрезок времени, включая переход через полночь (без повторений).
>10. Первый автобус для человека
Человек приходит на остановку в указанное время и садится на первый автобус
из переданного списка номеров. Возвращает номер автобуса, который приедет
первым.

### 2. Выбор структуры данных

|     | Тип          |
|-----|--------------|
| BusNunber  |ArrayList<Integer>      |
| CountTime   | ArrayList<Integer>      |
| BusTime | ArrayList<LocalTime> |  


 `BusNunber`- целочисленный динамический массив, так как подразумевается, что элементы матрицы это номера автобусов(целые числа), и подразумевается, что в массив можно добавлять бесконечное кол-во автобусов
`CountTime` - вспомогательный массив, элементами которого будут являтся количества(целые числа) остоновок для каждого автобуса.
`BusTime` - массив с значениями времени прибытия автобусов.


### 3. Алгоритм
#### Общая концепция:  
![alt text](image-1.png)
Работа с массивом времени:
>Во многих подзадчачх я использовал такую логику. Нам надо найти в массиве с временем оперделенные значения соответсвующие номеру автобуса, а так как каждому номеру автобуса соответсвует обект из вспомогательного массива с количеством остановок, при поиске нужного списка времени достаточно посчитать сумму всех элементов вспомогательного массива до нужного нам, это чило будет индексом первого элемета в списке времени соответствующего номеру автобуса.  

Обратный алгоритм:  
>По сути та же логика но реализованая в обратном порядке, применялось мной в последних задачах.Мы знаем индекс нужного нам времени, далее мы начинаем складывать все элементы вспомогательного массива пока эта сумма не станет больше или рана индексу времени, а так как каждый элемент вспомогательного массива сооответствует элементу номера автобуса, мы легко можем найти нужный нам номер автобуса.


### 4. Программа

```java
import java.io.PrintStream;
import java.time.LocalTime;
import java.util.Scanner;
import java.util.ArrayList;
import java.time.format.DateTimeFormatter;
import java.util.*;
// Создание нового класса
class BusStation {
    public static Scanner in = new Scanner(System.in);
    public static PrintStream out = System.out;
    //Описываем Динамический массив для номеров автобуса
   ArrayList<Integer> BusNunber;
   //Описываем Динамический массив с количеством остановок автобуса
   ArrayList<Integer> CountTime;
   //Описываем Динамический массив содержащий все возможное время прихода автобусов
   ArrayList<LocalTime> BusTime;
    //Вывод значения (Задание 1)
   @Override
    public String toString() {
       //Переменная для вывода значения
       String a="";
       //Переменная для вывода времени
       int SumBegin=0;
       //Проверка корректности существующих данных
       if ((BusNunber==null)) {
           return "Расписания НЕТ!!!";
       }
       else if (BusNunber.size()==0) {
           return "Расписания НЕТ!!!";
       }
       //Реализация вывода (Задача 1)
       else {
           for (int i = 0; i < BusNunber.size(); i++) {
               //Добавление Номера автобуса
               a = a +"Номер Автобуса №"+ BusNunber.get(i) + " :";
               //Вычисление места от куда мы будем выводить время к определенному автобусу
               for (int j = 0; j < i; j++) {
                   SumBegin = SumBegin + CountTime.get(j);
               }
               //Вывод нужного времени к оперделенному автобусу
               for (int j = SumBegin; j < SumBegin+CountTime.get(i); j++) {
                   a = a + " " + BusTime.get(j);
               }
               //Обнуление места начала вывода списка времени
               SumBegin=0;
               //Перенос на сл.строку
               a = a + "\n";
           }
       }
       //Вывод строкового представления класса
       return a;
   }
   //Конструктор класса
   public BusStation() {
       this.BusNunber=new ArrayList<>();
       this.BusTime=new ArrayList<>();
       this.CountTime=new ArrayList<>();
   }

   // Добавление времени прихода автобуса (Задача 2)
   public void AddBus(int n,LocalTime t){
       //Переменная для изменения элементов вспомогательного массива
       int he=0;
       //Переменная для поиска индекса нужного времени
       int SumTime=0;
       boolean flag=true;
       // Проверка на повтор номера автобуса
       if (!(BusNunber.contains(n))) {
           //Если такого номера нет, то добавляем новый номер автобуса, добавляем новое число 1 в вспомогательный массив, а также добавляем время прихода нового автобуса
               this.BusNunber.add(n);
               this.CountTime.add(1);
               this.BusTime.add(t);
       }
       else
       {
           //Иначе прибавляем 1 к уже существующему элементу вспомогательного массива
           he= CountTime.get(BusNunber.indexOf(n));
           this.CountTime.set(BusNunber.indexOf(n), he + 1);
           //Вычисление индекса с которого начинается время нужного автобуса
           for (int i = 0; i < BusNunber.indexOf(n); i++) {
               SumTime = SumTime + CountTime.get(i);
           }
           //Проверка на повтор данного времени
             for (int i=SumTime; i<(SumTime+CountTime.get(BusNunber.indexOf(n))-1); i++){
                 if (t.equals(BusTime.get(i))){
                     flag=false;
                 }
             }
             if (flag) {
                 this.BusTime.add(SumTime , t);
             }
             else{
                 he= CountTime.get(BusNunber.indexOf(n));
                 this.CountTime.set(BusNunber.indexOf(n), he - 1);
             }
           }
   }
   //Удаление автобуса из расписания(Задача 3)
   public void DeleteBus(int n){
       // Сохраняем индекс данного номера
       int IndexBus=BusNunber.indexOf(n);
       // Переменная для работы с массивом времени
       int sum=0;
       //Удаление номера автобуса
       this.BusNunber.remove(IndexBus);
       //Поиск нужного индекса для работы с временем
       for (int i = 0; i < IndexBus; i++) {
           sum = sum + CountTime.get(i);
       }
       //Удаление времени данного автобуса
       for(int j=0;j<CountTime.get(IndexBus);j++){
           this.BusTime.remove(sum);
       }
       //Удаление элемента вспомогательного массива
       CountTime.remove(IndexBus);
   }
   //Удаление времени прихода автобуса(Задание 4)
    public void DeleteTime(int n,LocalTime t){
       //Переменная для работы с массивом времени
       int sum=0;
       //Поиск нужного индекса для работы с массивом времени
       for(int i=0;i<BusNunber.indexOf(n);i++){
           sum = sum + CountTime.get(i);
       }
       //Удаление указаного времени у данного автобуса
       for (int i=sum;i<CountTime.get(BusNunber.indexOf(n))+sum;i++){
           if (t.equals(BusTime.get(i))){
               BusTime.remove(sum);
               //Уменьшение на 1, элемента впом.массива соответствующего индексу номера автобуса
               this.CountTime.set(BusNunber.indexOf(n),CountTime.get(BusNunber.indexOf(n)) - 1);
               break;
           }
       }

    }
    //Добавление автобуса с периодическими остановками (по количеству) (Задание 5)
    public void PeriodsStops(int n,LocalTime t,LocalTime in,int countSt){
       // Поиск нужного индекса для работы с массивом времени
        int sum=0;
        for(int i=0;i<BusNunber.indexOf(n);i++){
            sum = sum + CountTime.get(i);
        }
        // Добавление нужного времени countSt раз
        for (int i=sum;i<countSt+sum;i++){
            BusTime.add(sum,t);
            //Прибавляем нужный интервал
            t=t.plusHours(in.getHour()).plusMinutes(in.getMinute());
            this.CountTime.set(BusNunber.indexOf(n),CountTime.get(BusNunber.indexOf(n)) + 1);
        }
    }
    // Добавление автобуса с периодическими остановками (по времени)(Задание 6)
    public void PeriodsStops1(int n,LocalTime t,LocalTime in,LocalTime tc){
        // Поиск нужного индекса для работы с массивом времени
        int sum=0;
        for(int i=0;i<BusNunber.indexOf(n);i++){
            sum = sum + CountTime.get(i);
        }
        //Добавление нужного времени
        while (!(t.equals(tc))){
            BusTime.add(sum,t);
            // Прибавляем время интервала
            t=t.plusHours(in.getHour()).plusMinutes(in.getMinute());
            this.CountTime.set(BusNunber.indexOf(n),CountTime.get(BusNunber.indexOf(n)) + 1);
        }
        // Добавление последнего элемента
        BusTime.add(sum,t);
        // Прибавляем один к элементу вспомогательного массива
        this.CountTime.set(BusNunber.indexOf(n),CountTime.get(BusNunber.indexOf(n)) + 1);
    }
    //Ожидание автобуса человеком(Задание 7)
    public boolean ExpectationBus(int n,LocalTime t,LocalTime exp){
       //Переменная для вывода
       boolean flag=false;
        // Поиск нужного индекса для работы с массивом времени
        int sum=0;
        for(int i=0;i<BusNunber.indexOf(n);i++){
            sum = sum + CountTime.get(i);
        }
        //Проверка на диапозон времени
        for (int i=sum;i<CountTime.get(BusNunber.indexOf(n))+sum;i++){
            if (t.compareTo(BusTime.get(i)) <=0){
                if ((t.plusHours(exp.getHour()).plusMinutes(exp.getMinute())).compareTo(BusTime.get(i))>=0){
                    flag=true;
                    break;
                }
            }
        }
       return flag;
    }
    //Автобусы на отрезке времени (в пределах суток)(Задание 8)
    public ArrayList<Integer> Otr(LocalTime j, LocalTime t){
       int sum=0;
       //Массив для сбора нужных номеров автобусов
        ArrayList<Integer> fa=new ArrayList<>();
        for (int i=0;i<BusTime.size();i++){
            //Проверка на попадание в нужный диапозон
            if (j.compareTo(BusTime.get(i)) <=0){
                if(t.compareTo(BusTime.get(i)) >=0){
                    //Поиск нужного индекса, масива номера автобусов по обратной логике
                    for(int k=0;k<CountTime.size()-1;k++){
                        sum=sum+CountTime.get(k);
                         if (sum==i) {
                             if (!fa.contains(BusNunber.get(k+1))){
                                 fa.add(BusNunber.get(k+1));
                             }
                             k=CountTime.size();
                        }
                         else if(sum>i){
                             if(!fa.contains(BusNunber.get(k))){
                                 fa.add(BusNunber.get(k));
                             }
                             k=CountTime.size();
                         }
                    }
                    sum=0;
                }
            }
        }
        return fa;
    }
    //Автобусы на отрезке времени (через полночь)(Задача 9)
    public ArrayList<Integer> Otr1(LocalTime j, LocalTime t){
        int sum=0;
        //Массив для сбора нужных номеров автобусов
        ArrayList<Integer> fa=new ArrayList<>();
        //Если начало времени ожидания, равно времени конца ожидания, можем выводить весь массив с номерами автобусов, тк пройдет 24 часа
        if (j.compareTo(t)==0){
            return BusNunber;
        }
        // Поиск нужного номера по сценарию 8 Задания
        if (j.compareTo(t)<0) {
            for (int i = 0; i < BusTime.size(); i++) {
                if (j.compareTo(BusTime.get(i)) <= 0) {
                    if (t.compareTo(BusTime.get(i)) >= 0) {
                        for (int k = 0; k < CountTime.size() - 1; k++) {
                            sum = sum + CountTime.get(k);
                            if (sum == i) {
                                if (!fa.contains(BusNunber.get(k + 1))) {
                                    fa.add(BusNunber.get(k + 1));
                                }
                                k = CountTime.size();
                            } else if (sum > i) {
                                if (!fa.contains(BusNunber.get(k))) {
                                    fa.add(BusNunber.get(k));
                                }
                                k = CountTime.size();
                            }
                        }
                        sum = 0;
                    }
                }
            }
            return fa;
        }
        else{
            for (int i = 0; i < BusTime.size(); i++) {
                // Учесть переход на следующий день
                if ((j.compareTo(BusTime.get(i)) <= 0)||(t.compareTo(BusTime.get(i)) >= 0)) {
                        for (int k = 0; k < CountTime.size() - 1; k++) {
                            sum = sum + CountTime.get(k);
                            if (sum == i) {
                                if (!fa.contains(BusNunber.get(k + 1))) {
                                    fa.add(BusNunber.get(k + 1));
                                }
                                k = CountTime.size();
                            } else if (sum > i) {
                                if (!fa.contains(BusNunber.get(k))) {
                                    fa.add(BusNunber.get(k));
                                }
                                k = CountTime.size();
                            }
                        }
                        sum = 0;
                }

            }
            return fa;
        }
    }
    // Первый автобус для человека(Задание 10)
    public int FirstBus(LocalTime t){
       // Переменная для поиска нужного времени, если все данное время меньше времени полученого функцией смотрим следующие сутки
       LocalTime s=LocalTime.of(00,00);
       int sum=0;
       int end=0;
       //Поиск первого времени которое больше данного
       for (int i=0;i<BusTime.size();i++){
           if (BusTime.get(i).compareTo(t)>0){
               s=BusTime.get(i);
               break;
           }
       }
       // Поиск времени максимально приближенного полученому времени
        for (int i=0;i<BusTime.size();i++){
            if ((BusTime.get(i).compareTo(t)>0)&&(BusTime.get(i).compareTo(s)<0)) {
                s = BusTime.get(i);
            }
        }
        //Поиск нужного номера автобуса
        for (int k = 0; k < CountTime.size() - 1; k++) {
            sum = sum + CountTime.get(k);
            if (sum == BusTime.indexOf(s)) {
                end= BusNunber.get(k+1);
                break;
            } else if (sum > BusTime.indexOf(s)) {
                end= BusNunber.get(k);
                break;
            }
        }
        return end;
    }
}
```

### 5. Анализ правильности решения

1. #### Задание 1:
(Основная программа)  
>BusStation bs = new BusStation();  
out.println(bs);
- Input:
    ```
    ```
- Output:
    ```
    Расписания НЕТ!!!
    ```

2. #### Задание 1 и 2:
(Основная программа)  
>BusStation bs = new BusStation();  
bs.AddBus(in.nextInt(),LocalTime.of(in.nextInt(),in.nextInt()));  
bs.AddBus(in.nextInt(),LocalTime.of(in.nextInt(),in.nextInt()));  
bs.AddBus(in.nextInt(),LocalTime.of(in.nextInt(),in.nextInt()));  
out.println(bs);
- Input:
    ```
  123 12:00
  345 21:56
  120 4:45
    ```
- Output:
    ```
   Номер Автобуса №123 : 12:00
   Номер Автобуса №345 : 21:56
   Номер Автобуса №120 : 04:45
    ```
3. #### Задание 2
(Основная программа)  
>BusStation bs = new BusStation();  
bs.AddBus(in.nextInt(),LocalTime.of(in.nextInt(),in.nextInt()));  
bs.AddBus(in.nextInt(),LocalTime.of(in.nextInt(),in.nextInt()));  
bs.AddBus(in.nextInt(),LocalTime.of(in.nextInt(),in.nextInt()));  
out.println(bs);
- Input:
    ```
  123 12:00
  345 21:56
  123 4:45
    ```
- Output:
    ```
    Номер Автобуса №123 : 04:45 12:00
   Номер Автобуса №345 : 21:56
    ```

4. #### Задание 3
(Основная программа)
>BusStation bs = new BusStation();  
        bs.AddBus(in.nextInt(),LocalTime.of(in.nextInt(),in.nextInt()));  
        bs.AddBus(in.nextInt(),LocalTime.of(in.nextInt(),in.nextInt()));  
        bs.AddBus(in.nextInt(),LocalTime.of(in.nextInt(),in.nextInt()));  
        bs.DeleteBus(in.nextInt(),LocalTime.of(in.nextInt(),in.nextInt()));  
        out.println(bs);
- Input:
    ```
  123 12:00
  345 21:56
  123 4:45

  123
    ```
- Output:
    ```
     Номер Автобуса №345 : 21:56
    ```

5. #### Задание 4
(Основная программа)
>BusStation bs = new BusStation();  
        bs.AddBus(in.nextInt(),LocalTime.of(in.nextInt(),in.nextInt()));  
        bs.AddBus(in.nextInt(),LocalTime.of(in.nextInt(),in.nextInt()));  
        bs.AddBus(in.nextInt(),LocalTime.of(in.nextInt(),in.nextInt()));  
        bs.DeleteTime(in.nextInt(),LocalTime.of(in.nextInt(),in.nextInt()));  
        out.println(bs);
- Input:
    ```
  123 12:00
  345 21:56
  123 4:45

  123 4:45
    ```
- Output:
    ```
    Номер Автобуса №123 : 12:00
    Номер Автобуса №345 : 21:56
    ```

6. #### Задание 5
(Основная программа)
>BusStation bs = new BusStation();  
        bs.AddBus(in.nextInt(),LocalTime.of(in.nextInt(),in.nextInt()));  
        bs.AddBus(in.nextInt(),LocalTime.of(in.nextInt(),in.nextInt()));  
        bs.AddBus(in.nextInt(),LocalTime.of(in.nextInt(),in.nextInt()));
        bs.PeriodsStops(in.nextInt(),LocalTime.of(in.nextInt(),in.nextInt()),LocalTime.of(in.nextInt(),in.nextInt()),in.nextInt());  
        out.println(bs);
- Input:
    ```
  123 12:00
  234 7:00
  333 23:00

  333 10:00 00:30 5
    ```
- Output:
    ```
    Номер Автобуса №123 : 12:00
    Номер Автобуса №234 : 07:30
    Номер Автобуса №333 : 12:00 11:30 11:00 10:30 10:00 23:00
    ```

7. ##### Задание 6
(Основная программа)
>BusStation bs = new BusStation();  
        bs.AddBus(in.nextInt(),LocalTime.of(in.nextInt(),in.nextInt()));  
        bs.AddBus(in.nextInt(),LocalTime.of(in.nextInt(),in.nextInt()));  
        bs.AddBus(in.nextInt(),LocalTime.of(in.nextInt(),in.nextInt()));  
        bs.PeriodsStops1(in.nextInt(),LocalTime.of(in.nextInt(),in.nextInt()),LocalTime.of(in.nextInt(),in.nextInt()),LocalTime.of(in.nextInt(),in.nextInt()));
        out.println(bs);
- Input:
    ```
  123 12:00
  333 10:00
  222 9:00

  123 12:30 0:30 15:00
    ```
- Output:
    ```
    Номер Автобуса №123 : 15:00 14:30 14:00 13:30 13:00 12:30 12:00
    Номер Автобуса №333 : 10:00
    Номер Автобуса №222 : 09:00
    ```

8. ##### Задане 7(true)
(Основная программа)
>BusStation bs = new BusStation();  
        bs.AddBus(in.nextInt(),LocalTime.of(in.nextInt(),in.nextInt()));  
        bs.AddBus(in.nextInt(),LocalTime.of(in.nextInt(),in.nextInt()));  
        bs.AddBus(in.nextInt(),LocalTime.of(in.nextInt(),in.nextInt()));  
        out.println(bs.ExpectationBus(in.nextInt(),LocalTime.of(in.nextInt(),in.nextInt()),LocalTime.of(in.nextInt(),in.nextInt())));
- Input:
    ```
  123 12:00
  333 23:45
  555 5:45

  555 5:40 00:20
    ```
- Output:
    ```
    true
    ```

9. ##### Задане 7(false)
(Основная программа)
>BusStation bs = new BusStation();  
        bs.AddBus(in.nextInt(),LocalTime.of(in.nextInt(),in.nextInt()));  
        bs.AddBus(in.nextInt(),LocalTime.of(in.nextInt(),in.nextInt()));  
        bs.AddBus(in.nextInt(),LocalTime.of(in.nextInt(),in.nextInt()));  
        out.println(bs.ExpectationBus(in.nextInt(),LocalTime.of(in.nextInt(),in.nextInt()),LocalTime.of(in.nextInt(),in.nextInt())));
- Input:
    ```
  123 12:00
  333 23:45
  555 5:45

  555 5:20 00:20
    ```
- Output:
    ```
    false
    ```
10. ##### Задане 8
(Основная программа)
>BusStation bs = new BusStation();
        bs.AddBus(in.nextInt(),LocalTime.of(in.nextInt(),in.nextInt()));
        bs.AddBus(in.nextInt(),LocalTime.of(in.nextInt(),in.nextInt()));
        bs.AddBus(in.nextInt(),LocalTime.of(in.nextInt(),in.nextInt()));
        LocalTime a=LocalTime.of(in.nextInt(), in.nextInt());
        LocalTime b=LocalTime.of(in.nextInt(), in.nextInt());
        for (int i=0;i<bs.Otr(a,b).size();i++ ){
            out.print(bs.Otr(a,b).get(i)+" ");
        }
- Input:
    ```
  123 12:00
  333 13:00
  555 21:00

  11:00 19:00
    ```
- Output:
    ```
    123 333
    ```
11. ##### Задане 9
(Основная программа)
>BusStation bs = new BusStation();
        bs.AddBus(in.nextInt(),LocalTime.of(in.nextInt(),in.nextInt()));
        bs.AddBus(in.nextInt(),LocalTime.of(in.nextInt(),in.nextInt()));
        bs.AddBus(in.nextInt(),LocalTime.of(in.nextInt(),in.nextInt()));
        LocalTime a=LocalTime.of(in.nextInt(), in.nextInt());
        LocalTime b=LocalTime.of(in.nextInt(), in.nextInt());
        for (int i=0;i<bs.Otr1(a,b).size();i++ ){
            out.print(bs.Otr1(a,b).get(i)+" ");
        }
- Input:
    ```
  123 12:00
  333 13:00
  555 21:00

  20:00 12:30
    ```
- Output:
    ```
    123 555
    ```
12. ##### Задане 10
(Основная программа)
>BusStation bs = new BusStation();
        bs.AddBus(in.nextInt(),LocalTime.of(in.nextInt(),in.nextInt()));
        bs.AddBus(in.nextInt(),LocalTime.of(in.nextInt(),in.nextInt()));
        bs.AddBus(in.nextInt(),LocalTime.of(in.nextInt(),in.nextInt()));
        LocalTime a=LocalTime.of(in.nextInt(), in.nextInt());
        out.print(bs.FirstBus(a));
- Input:
    ```
  123 12:00
  333 13:00
  555 21:00

  20:00 
    ```
- Output:
    ```
     555
    ```    
