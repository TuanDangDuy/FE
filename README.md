# Object-Oriented-Programming-OOP


1. Định nghĩa
OOP là viết tắt của Object-Oriented Programming dịch ra là lập trình hướng đối tượng. Lập trình hướng đối tượng là kỹ thuật, phương pháp lập trình sử dụng các đối tượng (objects) để xây dựng ứng dụng. Hầu hết các ngôn ngữ như: C#, Java, PHP, Ruby… đều hỗ trợ lập trình hướng đối tượng.

#

2. Class và Object
Trong OOP, Lớp (Class) là 1 kiểu dữ liệu, 1 khuôn mẫu giúp mô hình hóa các đối tượng thực tế. Class sẽ có các thuộc tính (properties) và các phương thức (methods) tương ứng với thuộc tính và hành động thực tế bên ngoài.

       //(C# code)
       public class Developer
       {
              private string Name {get;set;}
              public void AnalyzeRequirement()
              {
                     //Do something
              }
              
              public void WriteCode()
              {
                    // Do something
              }
              
              public void Deploy()
              {
                     //Do something
              }
       }
       
#

4. Tính đóng gói (Encapsulation)
Tính đóng gói (Encapsulation) hay còn gọi là** hiding information** giúp gom nhóm lại các thuộc tính (properties), phương thức (methods), biến (variables) và nhiều thành phần khác thành một đối tượng hay một đơn vị.

Tính đóng gói được triển khai bằng cách sử dụng access modifier: public, private, protected, internal.

public: Có thể truy cập từ bất cứ đâu
private: Chỉ có thể truy cập ở bên trong class
protected: Chỉ có thể truy cập ở bên trong class và các class kế thừa từ class đó
internal: Giống như public nhưng chỉ hạn chế trong 1 assembly.
Giải thích về intenal: Hiểu đơn giản là ta có 1 ứng dụng U gọi 1 thư viện bên ngoài L. Trong thư viện L này có class C khai báo internal. Các class khác trong thư viện L này có thể truy cập class C này nhưng ứng dụng U thì không thể do khác assembly.

Ví dụ:

    //(C# code)
    public class BankAccount
    {
          private string Name {get;set;}

          private string AccountNumber {get;set;}

          private Datetime CreateDate {get;set;}

          public string GetAccountName()
              {
                  return Name;
              }
    }
       
#

5. Tính kế thừa (Inheritance)

Tính kế thừa cho phép tạo ra 1 class con từ 1 class có sẵn và mở rộng class đó. Các class con có thể kế thừa lại các thuộc tính (properties) và phương thức (methods) của class cha, có thể không cần định nghĩa lại các phương thức hoặc tái định nghĩa (override) hoặc thêm các phương thức sử dụng riêng ở lớp con. Tính chất này giúp tái sử dụng, tận dụng mã nguồn có sẵn.

Ví dụ:

    //(C# code)
    class Vehicle  // base class (parent) 
    {
      public string brand = "Ford";  // Vehicle field
      public void honk()             // Vehicle method 
      {                    
        Console.WriteLine("Tuut, tuut!");
      }
    }

    class Car : Vehicle  // derived class (child)
    {
      public string modelName = "Mustang";  // Car field
    }

    class Program
    {
      static void Main(string[] args)
      {
        // Create a myCar object
        Car myCar = new Car();

        // Call the honk() method (From the Vehicle class) on the myCar object
        myCar.honk();

        // Display the value of the brand field (from the Vehicle class) and the value of the modelName from the Car class
        Console.WriteLine(myCar.brand + " " + myCar.modelName);
      }
    }
    
#

6. Tính đa hình (Polymorphism)
Tính đa hình cho phép một hành động có thể được thực hiện bằng nhiều cách khác nhau.

Có 2 cách vận dụng tính đa hình:

Method overloading(đa hình khi biên dịch(compile time)): Trong 1 lớp (class) các phương thức (methods) có cùng tên nhưng kiểu trả về và tham số truyền vào khác nhau (số lượng, kiểu) 
Ví dụ:

    //(C# code)
    public class BankAccount()
    {
      public object GetAccountInformation(int bankId)
        {
      //To do something
        }

      public object GetAccountInformation(string bankName)
        {
      //To do something
        }

        public object GetAccountInformation(string bankName, string address)
        {
      //To do something
        }
    }

Method overriding(đa hình ở thời điểm thực thi(runtime)): Các phương thức được thực hiện ở các lớp con kế thừa từ lớp cha (base class). Nội dung thực hiện bên trong mỗi lớp khác nhau tùy vào logic nghiệp vụ. Chỉ khi nào runtime ta mới biết được đối tượng sẽ sử dụng phương thức nào. 
Ví dụ:

    //(C# code)
    public class BankAccount //Base class
    {
      public decimal GetTotalPrice()
      {
        //To do something
        }
    }

    public class CreditCard: BankAccount 
    {
        public decimal GetTotalPrice()
      {
        //To do something
        }
    }

    public class DebitCard: BankAccount 
    {
        public decimal GetTotalPrice()
      {
        //To do something
        }
    }

    public class Program
    {
           public static void Main(string[] args)
           {
                   BankAccount bank = new CreditCard();
                   Console.WriteLine(bank .GetTotalPrice());
                   Console.Read();
           }
    }

#

7. Tính trừu tượng (Abstraction)
So với 3 tính chất trên thì tính trừu tượng để giải thích hơi khó hiểu 1 tí bởi vì rất trừu tượng. ^^

Tính trừu tượng cho phép tổng quát hóa một đối tượng. Nghĩa là ẩn đi những thông tin chi tiết bên trong, chỉ thể hiện ra những thông tin bên ngoài. Và nhìn vào thông tin bên ngoài đó ta có thể hiểu được đối tượng đó làm gì.

Tính chất này được thể hiện qua việc sử dụng interface hoặc abstract class.

Lưu ý: Câu thần chú Abstraction - Ẩn chi tiết, thể hiện tổng quan.

Ví dụ: khi thực hiện hành động thanh toán sẽ có có nhiều bước và nghiệp vụ bên trong hành động này. Bằng cách chia tách nhỏ nghiệp vụ thành từng phương thức và sử dụng interface ta có thể dể dàng hiểu được tổng quan những bước, những hành động khi thanh toán. Mà không cần đi vào chi tiết mỗi hành động làm gì.

    //C# code
    //Checkout:
    public Interface Checkout
    {
    //Chỉ hiển thị tên phương thức, tham số, kiểu trả về
    //không thể hiện cách thực hiện chi tiết, logic nghiệp vụ bên trong
      Bool ValidateAccount(object BankAccount); 
      Decimal CaculateTotalPrice(object BankAccount);
      int Checkout(object BankAccount));
    }
       
