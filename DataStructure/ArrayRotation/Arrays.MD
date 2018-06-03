		using System;
		
		namespace TestBench
		{
			class Program
			{
				static void Main(string[] args)
				{
					int[] a = { 1, 2, 3, 4, 5 };
		
					//var result = rotLeft(a, 3);
		
					var result = LeftRotationArray(a, 3);
		
					foreach (int item in result)
					{
						Console.Write(item);
					}
		
					Console.Read();
				}
		
				static int[] rotLeft(int[] inputArray, int leftRotationValue)
				{
		
					int dataOut = 0;
		
					int arrayLength = inputArray.Length - 1;
		
					for (int i = 1; i <= leftRotationValue; i++)
					{
						for (int j = 0; j <= arrayLength; j++)
						{
							if (j == 0)
							{
								dataOut = inputArray[0];
							}
							if (j < arrayLength)
							{
								inputArray[j] = inputArray[j +1];
							}
		
							else if (j == arrayLength)
							{
								inputArray[j] = dataOut;
							}
						}
					}
		
					return inputArray;
				}
		
				static int[] LeftRotationArray(int[] inputArray, int leftRotationValue)
				{
					int[] RoatationUpdatedArray = new int[inputArray.Length];
					int inputArrayLength = inputArray.Length;
					int newArrayLocation;
					for (int i = 0; i < inputArray.Length; i++)
					{
						newArrayLocation = (i + (inputArrayLength - leftRotationValue)) % inputArrayLength;
						RoatationUpdatedArray[newArrayLocation] = inputArray[i];
					}
		
					return RoatationUpdatedArray;
				}
			}
		}
		