## ����� �� ������������ ������ � 3

#### � ������: `��-2402`

#### ��������: `����� �������� ����������`

#### �������: `15`

### C���������:

- [���������� ������](#1-����������-������)
- [����� ��������� ������](#2-�����-���������-������)
- [��������](#3-��������)
- [���������](#4-���������)
- [������ ������������ �������](#5-������-������������-�������)

### 1. ���������� ������


> ### ���������� ���������
>������� ��������:  
����������� ��������� ��� ������ � ����������� ��������� �� ���������. �����������
���������� ���������� � �������� ���������, ���������� �������� �� ��������, �
����� ��������� ��������, ��������� � �����������.
�������� �����������
>1. ����� ����������
����������� ���������� � �������:
�������������1: hh:mm, hh:mm
�������������2: hh:mm, hh:mm
��� ������� ������� � ���������� ����������� ��������������.
>2. ���������� ������� ������� ��������
���������� ������� �������� �������� �� ��� ������ � ������� � ������� �hh:mm�.
���� �������� � ������ ������� ��� ���, �� ����������� � ����������. ���� ��������� ����� ��� ����, ��� �� �����������.
>3. �������� �������� �� ����������
�������� �������� � ��������� ������� �� ����������.
>4. �������� ������� ������� ��������
�������� ����������� ������� �������� �������� �� ��� ������ � ����������
�������.
>5. ���������� �������� � �������������� ����������� (�� ����������)
���������� ��������, ������� �������� ������ � ���������� ������� � ������
��������� ����� �������� �������� (� �������). ����������� ����� ��������,
����� ������, �������� � ���������� ���������.
>6. ���������� �������� � �������������� ����������� (�� �������)
���������� ��������, ������� �������� ������ � ���������� ������� � ������
��������� ����� �������� �������� �� ���������� ������� ������������. ����������� ����� ��������, ����� ������, �������� � �������� �����.
>7. �������� �������� ���������
������� �������� �� ��������� � ��������� ����� � ��� ������� � ����������
������� ����������� ���������� �����. ����������, ������� �� ������� ��������.
>8. �������� �� ������� ������� (� �������� �����)
���������� ������ ���������, ������� ��������� �� ��������� � ��������� ������� ������� (��� ����������). �������������, ��� ������� ������� ��������� �
�������� ����� �����.
>9. �������� �� ������� ������� (����� �������)
���������� ������ ���������, ������� ��������� �� ��������� � ��������� ������� �������, ������� ������� ����� ������� (��� ����������).
>10. ������ ������� ��� ��������
������� �������� �� ��������� � ��������� ����� � ������� �� ������ �������
�� ����������� ������ �������. ���������� ����� ��������, ������� �������
������.

### 2. ����� ��������� ������

|     | ���          |
|-----|--------------|
| BusNunber  |ArrayList<Integer>      |
| CountTime   | ArrayList<Integer>      |
| BusTime | ArrayList<LocalTime> |
 `BusNunber`- ������������� ������������ ������, ��� ��� ���������������, ��� �������� ������� ��� ������ ���������(����� �����), � ���������������, ��� � ������ ����� ��������� ����������� ���-�� ���������
`CountTime` - ��������������� ������, ���������� �������� ����� ������� ����������(����� �����) ��������� ��� ������� ��������.
`BusTime` - ������ � ���������� ������� �������� ���������.


### 3. ��������
#### ����� ���������:  
![alt text](image-1.png)
������ � �������� �������:
>�� ������ ���������� � ����������� ����� ������. ��� ���� ����� � ������� � �������� ������������ �������� �������������� ������ ��������, � ��� ��� ������� ������ �������� ������������ ����� �� ���������������� ������� � ����������� ���������, ��� ������ ������� ������ ������� ���������� ��������� ����� ���� ��������� ���������������� ������� �� ������� ���, ��� ���� ����� �������� ������� ������� � ������ ������� ���������������� ������ ��������.  

�������� ��������:  
>�� ���� �� �� ������ �� ������������ � �������� �������, ����������� ���� � ��������� �������.�� ����� ������ ������� ��� �������, ����� �� �������� ���������� ��� �������� ���������������� ������� ���� ��� ����� �� ������ ������ ��� ���� ������� �������, � ��� ��� ������ ������� ���������������� ������� �������������� �������� ������ ��������, �� ����� ����� ����� ������ ��� ����� ��������.


### 4. ���������

```java
import java.io.PrintStream;
import java.time.LocalTime;
import java.util.Scanner;
import java.util.ArrayList;
import java.time.format.DateTimeFormatter;
import java.util.*;
// �������� ������ ������
class BusStation {
    public static Scanner in = new Scanner(System.in);
    public static PrintStream out = System.out;
    //��������� ������������ ������ ��� ������� ��������
   ArrayList<Integer> BusNunber;
   //��������� ������������ ������ � ����������� ��������� ��������
   ArrayList<Integer> CountTime;
   //��������� ������������ ������ ���������� ��� ��������� ����� ������� ���������
   ArrayList<LocalTime> BusTime;
    //����� �������� (������� 1)
   @Override
    public String toString() {
       //���������� ��� ������ ��������
       String a="";
       //���������� ��� ������ �������
       int SumBegin=0;
       //�������� ������������ ������������ ������
       if ((BusNunber==null)) {
           return "���������� ���!!!";
       }
       else if (BusNunber.size()==0) {
           return "���������� ���!!!";
       }
       //���������� ������ (������ 1)
       else {
           for (int i = 0; i < BusNunber.size(); i++) {
               //���������� ������ ��������
               a = a +"����� �������� �"+ BusNunber.get(i) + " :";
               //���������� ����� �� ���� �� ����� �������� ����� � ������������� ��������
               for (int j = 0; j < i; j++) {
                   SumBegin = SumBegin + CountTime.get(j);
               }
               //����� ������� ������� � ������������� ��������
               for (int j = SumBegin; j < SumBegin+CountTime.get(i); j++) {
                   a = a + " " + BusTime.get(j);
               }
               //��������� ����� ������ ������ ������ �������
               SumBegin=0;
               //������� �� ��.������
               a = a + "\n";
           }
       }
       //����� ���������� ������������� ������
       return a;
   }
   //����������� ������
   public BusStation() {
       this.BusNunber=new ArrayList<>();
       this.BusTime=new ArrayList<>();
       this.CountTime=new ArrayList<>();
   }

   // ���������� ������� ������� �������� (������ 2)
   public void AddBus(int n,LocalTime t){
       //���������� ��� ��������� ��������� ���������������� �������
       int he=0;
       //���������� ��� ������ ������� ������� �������
       int SumTime=0;
       boolean flag=true;
       // �������� �� ������ ������ ��������
       if (!(BusNunber.contains(n))) {
           //���� ������ ������ ���, �� ��������� ����� ����� ��������, ��������� ����� ����� 1 � ��������������� ������, � ����� ��������� ����� ������� ������ ��������
               this.BusNunber.add(n);
               this.CountTime.add(1);
               this.BusTime.add(t);
       }
       else
       {
           //����� ���������� 1 � ��� ������������� �������� ���������������� �������
           he= CountTime.get(BusNunber.indexOf(n));
           this.CountTime.set(BusNunber.indexOf(n), he + 1);
           //���������� ������� � �������� ���������� ����� ������� ��������
           for (int i = 0; i < BusNunber.indexOf(n); i++) {
               SumTime = SumTime + CountTime.get(i);
           }
           //�������� �� ������ ������� �������
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
   //�������� �������� �� ����������(������ 3)
   public void DeleteBus(int n){
       // ��������� ������ ������� ������
       int IndexBus=BusNunber.indexOf(n);
       // ���������� ��� ������ � �������� �������
       int sum=0;
       //�������� ������ ��������
       this.BusNunber.remove(IndexBus);
       //����� ������� ������� ��� ������ � ��������
       for (int i = 0; i < IndexBus; i++) {
           sum = sum + CountTime.get(i);
       }
       //�������� ������� ������� ��������
       for(int j=0;j<CountTime.get(IndexBus);j++){
           this.BusTime.remove(sum);
       }
       //�������� �������� ���������������� �������
       CountTime.remove(IndexBus);
   }
   //�������� ������� ������� ��������(������� 4)
    public void DeleteTime(int n,LocalTime t){
       //���������� ��� ������ � �������� �������
       int sum=0;
       //����� ������� ������� ��� ������ � �������� �������
       for(int i=0;i<BusNunber.indexOf(n);i++){
           sum = sum + CountTime.get(i);
       }
       //�������� ��������� ������� � ������� ��������
       for (int i=sum;i<CountTime.get(BusNunber.indexOf(n))+sum;i++){
           if (t.equals(BusTime.get(i))){
               BusTime.remove(sum);
               //���������� �� 1, �������� ����.������� ���������������� ������� ������ ��������
               this.CountTime.set(BusNunber.indexOf(n),CountTime.get(BusNunber.indexOf(n)) - 1);
               break;
           }
       }

    }
    //���������� �������� � �������������� ����������� (�� ����������) (������� 5)
    public void PeriodsStops(int n,LocalTime t,LocalTime in,int countSt){
       // ����� ������� ������� ��� ������ � �������� �������
        int sum=0;
        for(int i=0;i<BusNunber.indexOf(n);i++){
            sum = sum + CountTime.get(i);
        }
        // ���������� ������� ������� countSt ���
        for (int i=sum;i<countSt+sum;i++){
            BusTime.add(sum,t);
            //���������� ������ ��������
            t=t.plusHours(in.getHour()).plusMinutes(in.getMinute());
            this.CountTime.set(BusNunber.indexOf(n),CountTime.get(BusNunber.indexOf(n)) + 1);
        }
    }
    // ���������� �������� � �������������� ����������� (�� �������)(������� 6)
    public void PeriodsStops1(int n,LocalTime t,LocalTime in,LocalTime tc){
        // ����� ������� ������� ��� ������ � �������� �������
        int sum=0;
        for(int i=0;i<BusNunber.indexOf(n);i++){
            sum = sum + CountTime.get(i);
        }
        //���������� ������� �������
        while (!(t.equals(tc))){
            BusTime.add(sum,t);
            // ���������� ����� ���������
            t=t.plusHours(in.getHour()).plusMinutes(in.getMinute());
            this.CountTime.set(BusNunber.indexOf(n),CountTime.get(BusNunber.indexOf(n)) + 1);
        }
        // ���������� ���������� ��������
        BusTime.add(sum,t);
        // ���������� ���� � �������� ���������������� �������
        this.CountTime.set(BusNunber.indexOf(n),CountTime.get(BusNunber.indexOf(n)) + 1);
    }
    //�������� �������� ���������(������� 7)
    public boolean ExpectationBus(int n,LocalTime t,LocalTime exp){
       //���������� ��� ������
       boolean flag=false;
        // ����� ������� ������� ��� ������ � �������� �������
        int sum=0;
        for(int i=0;i<BusNunber.indexOf(n);i++){
            sum = sum + CountTime.get(i);
        }
        //�������� �� �������� �������
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
    //�������� �� ������� ������� (� �������� �����)(������� 8)
    public ArrayList<Integer> Otr(LocalTime j, LocalTime t){
       int sum=0;
       //������ ��� ����� ������ ������� ���������
        ArrayList<Integer> fa=new ArrayList<>();
        for (int i=0;i<BusTime.size();i++){
            //�������� �� ��������� � ������ ��������
            if (j.compareTo(BusTime.get(i)) <=0){
                if(t.compareTo(BusTime.get(i)) >=0){
                    //����� ������� �������, ������ ������ ��������� �� �������� ������
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
    //�������� �� ������� ������� (����� �������)(������ 9)
    public ArrayList<Integer> Otr1(LocalTime j, LocalTime t){
        int sum=0;
        //������ ��� ����� ������ ������� ���������
        ArrayList<Integer> fa=new ArrayList<>();
        //���� ������ ������� ��������, ����� ������� ����� ��������, ����� �������� ���� ������ � �������� ���������, �� ������� 24 ����
        if (j.compareTo(t)==0){
            return BusNunber;
        }
        // ����� ������� ������ �� �������� 8 �������
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
                // ������ ������� �� ��������� ����
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
    // ������ ������� ��� ��������(������� 10)
    public int FirstBus(LocalTime t){
       // ���������� ��� ������ ������� �������, ���� ��� ������ ����� ������ ������� ���������� �������� ������� ��������� �����
       LocalTime s=LocalTime.of(00,00);
       int sum=0;
       int end=0;
       //����� ������� ������� ������� ������ �������
       for (int i=0;i<BusTime.size();i++){
           if (BusTime.get(i).compareTo(t)>0){
               s=BusTime.get(i);
               break;
           }
       }
       // ����� ������� ����������� ������������� ���������� �������
        for (int i=0;i<BusTime.size();i++){
            if ((BusTime.get(i).compareTo(t)>0)&&(BusTime.get(i).compareTo(s)<0)) {
                s = BusTime.get(i);
            }
        }
        //����� ������� ������ ��������
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

### 5. ������ ������������ �������

1. #### ������� 1:
(�������� ���������)  
>BusStation bs = new BusStation();  
out.println(bs);
- Input:
    ```
    ```
- Output:
    ```
    ���������� ���!!!
    ```

2. #### ������� 1 � 2:
(�������� ���������)  
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
   ����� �������� �123 : 12:00
   ����� �������� �345 : 21:56
   ����� �������� �120 : 04:45
    ```
3. #### ������� 2
(�������� ���������)  
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
    ����� �������� �123 : 04:45 12:00
   ����� �������� �345 : 21:56
    ```

4. #### ������� 3
(�������� ���������)
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
     ����� �������� �345 : 21:56
    ```

5. #### ������� 4
(�������� ���������)
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
    ����� �������� �123 : 12:00
    ����� �������� �345 : 21:56
    ```

6. #### ������� 5
(�������� ���������)
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
    ����� �������� �123 : 12:00
    ����� �������� �234 : 07:30
    ����� �������� �333 : 12:00 11:30 11:00 10:30 10:00 23:00
    ```

7. ##### ������� 6
(�������� ���������)
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
    ����� �������� �123 : 15:00 14:30 14:00 13:30 13:00 12:30 12:00
    ����� �������� �333 : 10:00
    ����� �������� �222 : 09:00
    ```

8. ##### ������ 7(true)
(�������� ���������)
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

9. ##### ������ 7(false)
(�������� ���������)
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
10. ##### ������ 8
(�������� ���������)
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
11. ##### ������ 9
(�������� ���������)
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
12. ##### ������ 10
(�������� ���������)
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
