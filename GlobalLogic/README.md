# GlobalLogic Interview Questions

**1. Liskov Substitution Principle**

**Ans:** Liskov Substitution Principle is one of the SOLID principle which states that objects of a superclass should be replaceable with objects of its subclasses without affecting the correctness of the program. In other words, if S is a subtype of T, then objects of type T may be replaced with objects of type S without altering any of the desirable properties of the program (correctness, task performed, etc.).

```java
class Employee{
    
    public int getSalary(){
        return 100000;
    }
    public int getBonus(){
        return 10000;
    }
}

class PermanentEmployee extends Employee{
    public int getSalary(){
        return 150000;
    }
    public int getBonus(){
        return 20000;
    }
}

class ContractEmployee extends Employee{
    public int getSalary(){
        return 80000;
    }
    public int getBonus(){
        throw new Exception("Not Applicable");
    }
}

```

In above example we have Employee class which has two method getSalary and getBonus, we have two subclass PermanentEmployee and ContractEmployee which extends Employee class. Now if we replace the Employee object with ContractEmployee object then it will throw an exception because ContractEmployee does not have bonus. This violates the Liskov Substitution Principle. To fix this we can create an interface Bonusable and implement it in PermanentEmployee class and ContractEmployee class will not implement it.


