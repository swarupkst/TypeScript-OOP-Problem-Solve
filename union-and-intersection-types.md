## Combining Union and Intersection Types in TypeScript with a Practical Example

# Introduction
TypeScript provides Union (|) and Intersection (&) types to make type definitions more flexible. A Union type allows a variable to hold one of several possible types, while an Intersection type combines multiple types into a single type. Using them together is useful when developing applications that handle different categories of data with some shared properties.

# Detailed Discussion
A Union type (|) means a value can follow one of several defined types. For example, an employee's ID might be either a number or a string.

type EmployeeID = number | string;
let id: EmployeeID = 101;
id = "EMP-101";

Both assignments are valid because the EmployeeID type accepts either a number or a string.

An Intersection type (&) combines multiple types. The resulting object must contain all the properties defined in the combined types.

type Person = {
  name: string;
  age: number;
};
type EmployeeDetails = {
  department: string;
  salary: number;
};
type Employee = Person & EmployeeDetails;

Now, an Employee object must contain all four properties.

We can combine Union and Intersection types in a practical employee management example.

type Person = {
  name: string;
  age: number;
};

type EmployeeDetails = {
  employeeId: number | string;
  department: string;
};

type AdminPermissions = {
  canManageUsers: boolean;
};

type Employee = Person & EmployeeDetails;

type Admin = Employee & AdminPermissions;

const admin: Admin = {
  name: "Swarup",
  age: 25,
  employeeId: "EMP-101",
  department: "IT",
  canManageUsers: true
};

Here, the Union type allows employeeId to accept either a number or a string. The Intersection type combines Person, EmployeeDetails, and AdminPermissions into one complete Admin type.

This approach is useful when building systems where different user roles share common information but also have additional properties.
# Conclusion
Union and Intersection types solve different problems in TypeScript. Union types provide flexibility by allowing multiple possible types, while Intersection types combine existing types into a single structure. Combining them helps developers create reusable and flexible type definitions without repeating the same properties in multiple places.