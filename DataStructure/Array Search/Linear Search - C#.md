	using System;
	using System.Linq;
	using System.Collections.Generic;
	
	public class Program
	{
		public static void Main()
		{
			// Program for Linear Serach in C#
	
			string userInputString;
			int userSearchInput;
			int[] inputIntegerArray;
			List<int> elementFoundPositions = new List<int>();
	
			Console.WriteLine("Enter number's with comma to be in list to be searched: ");
			userInputString = Console.ReadLine();
	
			Console.WriteLine("Enter the number to be searched: ");
			int.TryParse(Console.ReadLine(), out userSearchInput);
	
			inputIntegerArray = userInputString.Split(',').Select(item => int.Parse(item)).ToArray();
	
			for (int i = 0; i < inputIntegerArray.Length; i++)
			{
				if (inputIntegerArray[i] == userSearchInput)
				{
					elementFoundPositions.Add(i + 1);
				}
			}
	
			Console.Write("Your input Integer items: " + " ");
	
			foreach (var item in inputIntegerArray)
			{
				Console.Write(item + " ");
			}
			Console.WriteLine();
	
			Console.WriteLine("You searched for: " + userSearchInput);
	
			Console.Write("Your items found at position: ");
	
			foreach (var position in elementFoundPositions)
			{
				Console.Write(position + " ");
			}
			
			//Preventing Console from flashing out.
			Console.Read();
		}
	}
	