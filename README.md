using System;

class Program
{
    static void Main()
    {
        List<int> numbers = new List<int>();
        bool running = true;

        while (running)
        {
            Console.WriteLine("\nP - Print numbers");
            Console.WriteLine("A - Add a number");
            Console.WriteLine("M - Display mean of the numbers");
            Console.WriteLine("S - Display the smallest number");
            Console.WriteLine("L - Display the largest number");
            Console.WriteLine("Q - Quit");
            Console.Write("Enter your choice: ");

            string choice = Console.ReadLine().ToUpper();

            if (choice == "P")
            {
                if (numbers.Count == 0)
                {
                    Console.WriteLine("[] - the list is empty");
                }
                else
                {
                    Console.Write("[ ");
                    for (int i = 0; i < numbers.Count; i++)
                    {
                        Console.Write(numbers[i] + " ");
                    }
                    Console.WriteLine("]");
                }
            }
            else if (choice == "A")
            {
                Console.Write("Enter an integer to add: ");
                if (int.TryParse(Console.ReadLine(), out int newNumber))
                {
                    numbers.Add(newNumber);
                    Console.WriteLine($"{newNumber} added");
                }
                else
                {
                    Console.WriteLine("Invalid input. Please enter a valid integer.");
                }
            }
            else if (choice == "M")
            {
                if (numbers.Count == 0)
                {
                    Console.WriteLine("Unable to calculate the mean - no data");
                }
                else
                {
                    int sum = 0;
                    for (int i = 0; i < numbers.Count; i++)
                    {
                        sum += numbers[i];
                    }
                    double mean = (double)sum / numbers.Count;
                    Console.WriteLine($"The mean is {mean}");
                }
            }
            else if (choice == "S")
            {
                if (numbers.Count == 0)
                {
                    Console.WriteLine("Unable to determine the smallest number - list is empty");
                }
                else
                {
                    int smallest = numbers[0];
                    for (int i = 1; i < numbers.Count; i++)
                    {
                        if (numbers[i] < smallest)
                        {
                            smallest = numbers[i];
                        }
                    }
                    Console.WriteLine($"The smallest number is {smallest}");
                }
            }
            else if (choice == "L")
            {
                if (numbers.Count == 0)
                {
                    Console.WriteLine("Unable to determine the largest number - list is empty");
                }
                else
                {
                    int largest = numbers[0];
                    for (int i = 1; i < numbers.Count; i++)
                    {
                        if (numbers[i] > largest)
                        {
                            largest = numbers[i];
                        }
                    }
                    Console.WriteLine($"The largest number is {largest}");
                }
            }
            else if (choice == "Q")
            {
                running = false;
                Console.WriteLine("Goodbye");
            }
            else
            {
                Console.WriteLine("Unknown selection, please try again");
            }
        }
    }
}
