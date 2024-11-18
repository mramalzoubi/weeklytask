# weeklytask1a
using System;

class CarsStore
{
    public string StoreName { get; set; }
    public string Location { get; set; }
    public string Owner { get; set; }

    public CarsStore(string storeName, string location, string owner)
    {
        StoreName = storeName;
        Location = location;
        Owner = owner;
    }

    public void DisplayStoreDetails()
    {
        Console.WriteLine($"Store Name: {StoreName}\nLocation: {Location}\nOwner: {Owner}");
    }
}

class Car
{
    public string CarName { get; set; }
    public decimal Price { get; set; }

    public Car(string carName, decimal price)
    {
        CarName = carName;
        Price = price;
    }

    public void DisplayCarDetails()
    {
        Console.WriteLine($"Car Name: {CarName}\nPrice: {Price:C}");
    }
}

class CarOnSale : Car
{
    public double DiscountPercent { get; set; }
    public decimal FinalPrice { get; set; }

    public CarOnSale(string carName, decimal price, double discountPercent) : base(carName, price)
    {
        DiscountPercent = discountPercent;
        FinalPrice = price - (price * (decimal)(discountPercent / 100));
    }

    public void DisplaySaleDetails()
    {
        Console.WriteLine($"Car Name: {CarName}\nOriginal Price: {Price:C}\nDiscount: {DiscountPercent}%\nFinal Price: {FinalPrice:C}");
    }
}

class Program
{
    static void Main(string[] args)
    {
        Console.WriteLine("Enter Store Details:");
        Console.Write("Store Name: ");
        string storeName = Console.ReadLine();
        Console.Write("Location: ");
        string location = Console.ReadLine();
        Console.Write("Owner: ");
        string owner = Console.ReadLine();

        CarsStore store = new CarsStore(storeName, location, owner);
        store.DisplayStoreDetails();

        Console.WriteLine("\nEnter Car Details:");
        Console.Write("Car Name: ");
        string carName = Console.ReadLine();
        Console.Write("Price: ");
        decimal price = decimal.Parse(Console.ReadLine());

        Console.WriteLine("\nEnter Discount Details:");
        Console.Write("Discount (%): ");
        double discount = double.Parse(Console.ReadLine());

        CarOnSale carOnSale = new CarOnSale(carName, price, discount);
        carOnSale.DisplaySaleDetails();
    }
}

------------------------------------------------------------------------------------------------------------
# weeklytask1b
// See https://aka.ms/new-console-template for more information
using System;

class MathOperations
{
    public static void PerformOperation(double? num1, double? num2, string operation)
    {
        try
        {
            num1 ??= 0; // Default to 0 if null
            num2 ??= 0; // Default to 0 if null

            switch (operation)
            {
                case "+":
                    Console.WriteLine($"Result: {num1 + num2}");
                    break;
                case "-":
                    Console.WriteLine($"Result: {num1 - num2}");
                    break;
                case "*":
                    Console.WriteLine($"Result: {num1 * num2}");
                    break;
                case "/":
                    Console.WriteLine(num2 != 0 ? $"Result: {num1 / num2}" : "Error: Division by zero");
                    break;
                case "^":
                    Console.WriteLine($"Result: {Math.Pow((double)num1, (double)num2)}");
                    break;
                case "sqrt":
                    Console.WriteLine($"Square Root of {num1}: {Math.Sqrt((double)num1)}");
                    break;
                default:
                    Console.WriteLine("Invalid Operation");
                    break;
            }
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error: {ex.Message}");
        }
    }

    static void Main(string[] args)
    {
        Console.WriteLine("Enter first number (or leave blank for null): ");
        double? num1 = double.TryParse(Console.ReadLine(), out double result1) ? result1 : (double?)null;

        Console.WriteLine("Enter second number (or leave blank for null): ");
        double? num2 = double.TryParse(Console.ReadLine(), out double result2) ? result2 : (double?)null;

        Console.WriteLine("Enter operation (+, -, *, /, ^, sqrt): ");
        string operation = Console.ReadLine();

        PerformOperation(num1, num2, operation);
    }
}
