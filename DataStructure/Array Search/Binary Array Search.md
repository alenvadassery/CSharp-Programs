	using System;
	using System.Linq;
	
	namespace ProgramTextEditor
	{
		class Program
		{
			// Pogram for Binary Serach in C#
	
			string UserInputString;
			int UserSearchInput;
			int[] InputIntegerArray;
			int ElementFoundPosition;
	
			// Will be used for searching
			int MidValue;
			int InputArrayLength;
	
			static void Main(string[] args)
			{
				Program program = new Program();
	
				program.UserConsoleInput();
				program.ArraySorting();
				program.ElementFoundPosition = program.BinarySearch(program.InputIntegerArray, 0, program.InputArrayLength - 1, program.UserSearchInput);
				program.UserOutputDisplay();
	
				//Preventing Console from flashing out.
				Console.Read();
			}
	
			private void UserConsoleInput()
			{
				Console.WriteLine("Enter number's with comma to be in list to be searched: ");
				UserInputString = Console.ReadLine();
	
				Console.WriteLine("Enter the number to be searched: ");
				int.TryParse(Console.ReadLine(), out UserSearchInput);
	
				InputIntegerArray = UserInputString.Split(',').Select(item => int.Parse(item)).ToArray();
				InputArrayLength = InputIntegerArray.Length;
			}
	
			private void ArraySorting()
			{
				//Sorting of Array : ca also be done in traditional way.
				Array.Sort(InputIntegerArray);
			}
	
			private int BinarySearch(int[] integerArray, int leftArrayValue, int rightArrayValue, int searchItem)
			{
				if (leftArrayValue <= rightArrayValue)
				{
					MidValue = Convert.ToInt32(Math.Round(Convert.ToDouble(((leftArrayValue + rightArrayValue) / 2))));
	
					if (integerArray[MidValue] == searchItem)
					{
						return MidValue + 1;
					}
					else if (integerArray[MidValue] > searchItem)
					{
					return BinarySearch(integerArray, leftArrayValue, MidValue - 1, searchItem);
					}
					else
					{
						return BinarySearch(integerArray, MidValue + 1, rightArrayValue, searchItem);
					}
				}
	
				return -1;
			}
		
			private void UserOutputDisplay()
			{
				Console.Write("Your sorted input Integer items: " + " ");
	
				foreach (var item in InputIntegerArray)
				{
					Console.Write(item + " ");
				}
				Console.WriteLine();
	
				Console.WriteLine("You searched for: " + UserSearchInput);
	
				if (ElementFoundPosition == -1)
				{
					Console.Write("Your items not found in the Array.. Sorry");
				}
				else
				{
					Console.Write("Your items found at position: " + ElementFoundPosition);
				}
			}
		}
	}
	