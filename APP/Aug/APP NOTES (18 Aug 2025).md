---
updated_at: 2025-08-18T16:46:51.758+05:30
edited_seconds: 360
---
#APP 
# Arrays
	Arrays come in set sizes
```Java
class Employee
{
	int Emp_id;
	String Emp_Name = "John";
	int Emp_Salary;
}
public class Demo {
	public static void main(String args[]){
		/*In Java, string is not a datatype, String is (NOTE THE CAPITALIZATION)*/
		Employee Emp1 = new Employee();
			Emp1.Emp_ID = 1003;
			Emp1.Emp_Name = 'John';
			Emp1.Emp_Salary = 500000;
		Employee Emp2 = new Employee();
			Emp2.Emp_ID = 5004;
			Emp2.Emp_Name = 'Cena';
			Emp2.Emp_Salary = 400000;
		Employee Employees[] = new Employee[2];
			Employee[0] = Emp1;
			Employee[1] = Emp2;
		for (int i = 0; i<Employees.length; i++){
			System.out.println(Employees[i].Emp_id+ " "+Employees[i].EMP_Name+" "+Employees[i].Emp_Salary);
			
	}
}
```

---
# Question
```Java
#import Java.util.Scanner;
class RNo{
	int R_ID;
	String S_Name;
	String S_Section;
}
public class main{
	public static void main(String[] args){
		int n;
		Scanner input = new Scanner(System.in);
		System.out.println("Enter No. Of Students: ");
		n = input.nextInt();
		RNo R1 = new RNo(n);
		for (int i = 0; i<=n; i++){
			System.out.println("Enter Roll No.: ");
			R1[i].R_ID; = input.nextInt();
			System.out.println("Enter Name: ");
			R1[i].S_Name = input.nextLine();
			System.out.println("Enter Section: ");
			R1[i].S_Section = input.nextLine();
		}
	}
}
```