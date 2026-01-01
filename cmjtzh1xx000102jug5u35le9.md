---
title: "Comparable Part-2"
datePublished: Wed Dec 31 2025 12:19:35 GMT+0000 (Coordinated Universal Time)
cuid: cmjtzh1xx000102jug5u35le9
slug: comparable-part-2
tags: java-comparable, comparable, compare-to, string-compareto, dsending, dsending-order

---

Earlier, we learned how to sort the `Car` class by **mileAge**.  
In this article, we will focus on sorting cars by their **color**, helping us understand how `Comparable` works with `String` values.

> If you haven’t read it yet, you can check it out here:  
> 👉 [**Sorting Car Objects by Mileage Using Comparable in Java**](https://javaeduacademy.hashnode.dev/comparable-in-java)

## Sorting Car Objects By Color:

```java
public class Car implements Comparable<Car>{
    String brand;
    String color;
    int mileAge;
    int numOfSeaters;

    public Car(String brand, String color, int mileAge, int numOfSeaters) {
        this.brand = brand;
        this.color = color;
        this.mileAge = mileAge;
        this.numOfSeaters = numOfSeaters;
    }

    @Override
    public int compareTo(Car o) {
        return this.color.compareTo(o.color); //ascending order
    }


    @Override
    public String toString() {
        return "Car{" +
                "brand='" + brand + '\'' +
                ", Color='" + color + '\'' +
                ", mileAge=" + mileAge +
                ", numOfSeaters=" + numOfSeaters +
                '}';
    }
}
```

```java
import java.util.ArrayList;
import java.util.Collections;
import java.util.List;
public class SortWithColor {
    public static void main(String[] args) {
        List<Car> cars= new ArrayList<Car>();
        cars.add(new Car("BMW", "RED",100,5));
        cars.add(new Car("MARUTI", "BLUE",80,3));
        cars.add(new Car("AUDI", "GREEN",60,7));
        cars.add(new Car("Toyota", "WHITE",120,4));
        Collections.sort(cars);
        cars.forEach(System.out::println);
    }
}
```

> `this.color.compareTo(o.color)`
> 
> Here, `this.color` represents the color of the **current** `Car` object. Since `color` is of type `String`, it can directly use the `compareTo()` method provided by the `String` class.
> 
> Internally, the `String` class implements the `Comparable` interface and defines its own `compareTo()` method. By calling `compareTo(o.color)`, we pass the **color of the other** `Car` object to this method.
> 
> The `String.compareTo()` method compares both string values and arranges them in their **natural (alphabetical) order**, which enables the `Car` objects to be sorted based on color.

### Output :

```java
Car{brand='MARUTI', Color='BLUE', mileAge=80, numOfSeaters=3}
Car{brand='AUDI', Color='GREEN', mileAge=60, numOfSeaters=7}
Car{brand='BMW', Color='RED', mileAge=100, numOfSeaters=5}
Car{brand='Toyota', Color='WHITE', mileAge=120, numOfSeaters=4}
```

## Sorting Car Objects By Color (Descending order):

```java
public class Car implements Comparable<Car>{
    String brand;
    String color;
    int mileAge;
    int numOfSeaters;

    public Car(String brand, String color, int mileAge, int numOfSeaters) {
        this.brand = brand;
        this.color = color;
        this.mileAge = mileAge;
        this.numOfSeaters = numOfSeaters;
    }

    @Override
    public int compareTo(Car o) {
        return o.color.compareTo(this.color); //descending order
    }


    @Override
    public String toString() {
        return "Car{" +
                "brand='" + brand + '\'' +
                ", Color='" + color + '\'' +
                ", mileAge=" + mileAge +
                ", numOfSeaters=" + numOfSeaters +
                '}';
    }
}
```

```java
import java.util.ArrayList;
import java.util.Collections;
import java.util.List;
public class SortWithColor {
    public static void main(String[] args) {
        List<Car> cars= new ArrayList<Car>();
        cars.add(new Car("BMW", "RED",100,5));
        cars.add(new Car("MARUTI", "BLUE",80,3));
        cars.add(new Car("AUDI", "GREEN",60,7));
        cars.add(new Car("Toyota", "WHITE",120,4));
        Collections.sort(cars);
        cars.forEach(System.out::println);
    }
}
```

### Output :

```java
Car{brand='Toyota', Color='WHITE', mileAge=120, numOfSeaters=4}
Car{brand='BMW', Color='RED', mileAge=100, numOfSeaters=5}
Car{brand='AUDI', Color='GREEN', mileAge=60, numOfSeaters=7}
Car{brand='MARUTI', Color='BLUE', mileAge=80, numOfSeaters=3}
```

> o.color.CompareTo(this.color)
> 
> In this case, the order of comparison is **reversed**. Instead of comparing the current car’s color with the other car’s color, we compare the **other car’s color** with the **current car’s color**.
> 
> Because of this reversal, the result of the comparison is also reversed, which causes the `Car` objects to be sorted in **descending (reverse alphabetical) order** based on color.