## Understanding Access Modifiers in TypeScript OOP

# Introduction
Object-Oriented Programming (OOP) in TypeScript allows developers to organize code using classes and objects. Access modifiers control how class properties and methods can be accessed from different parts of a program. TypeScript provides four commonly used modifiers: public, private, protected, and readonly. Each has a different purpose and helps developers manage data access and maintain better code structure.

# Detailed Discussion
The public modifier allows a property or method to be accessed from anywhere. It is the default access modifier in TypeScript, so we do not need to write it explicitly.
The private modifier restricts access to the class where the property or method is declared. It cannot be accessed directly from outside that class or from its subclasses.
The protected modifier is similar to private, but it also allows access from child classes through inheritance. This is useful when a parent class needs to share certain properties with its subclasses.

class Employee {
  public name: string;
  private salary: number;
  protected department: string;
  readonly employeeId: number;

  constructor(name: string, salary: number, department: string, employeeId: number) {
    this.name = name;
    this.salary = salary;
    this.department = department;
    this.employeeId = employeeId;
  }
  public getSalary(): number {
    return this.salary;
  }
}
class Manager extends Employee {
  showDepartment(): void {
    console.log(this.department);
  }
}
const employee = new Employee("Swarup", 50000, "IT", 101);


Here, name can be accessed directly because it is public. The salary is private, so it can only be accessed inside the Employee class. The department property is protected, allowing the Manager class to access it through inheritance.

The readonly modifier allows a property to be assigned only during its declaration or inside the constructor. After that, its value cannot be changed.

# Conclusion
Access modifiers help control how data is accessed and modified in TypeScript classes. I use public for properties that need external access, private for internal data, and protected when child classes need access to parent properties. The readonly modifier is useful for values such as employee IDs that should not change after an object is created. Using these modifiers properly makes OOP applications more organized and secure.