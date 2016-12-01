using System;
using System.Collections.Generic;
using System.Linq;

namespace Number
{
    class Program
    {
        public static Dictionary<string, long> TableNumber = new Dictionary<string, long>
        {
            {"zero",0},{"one",1},{"two",2},{"three",3},{"four",4},
            {"five",5},{"six",6},{"seven",7},{"eight",8},{"nine",9},
            {"ten",10},{"eleven",11},{"twelve",12},{"thirteen",13},
            {"fourteen",14},{"fifteen",15},{"sixteen",16},
            {"seventeen",17},{"eighteen",18},{"nineteen",19},{"twenty",20},
            { "thirty",30}, { "forty", 40}, { "fifty", 50}, {" sixty", 60 },
            {"seventy", 70 }, { "eighty", 80}, { "ninety", 90}
        };

 public static int GetNumber (String text, out Boolean OK)
        {
            String[] num = text.Split(' ');           
            int result = 0;
            OK = true;
            for (int i = 1; i <= num.Count(); i++)
            {
                var numbers = TableNumber.Where(x => x.Key == text).ToList();
                if (numbers.Count != 0)
                {
                    OK = false;
                    return 0;
                }
                foreach (var number in numbers)
                {
                    result = (int)number.Value + result;
                }                                
            }                      
            return result;
        }

        static void Main(string[] args)
        {
            string Number1text, NUmber2text;
            Boolean OK = false;
            int NUmber1, Number2, Total;
            Console.WriteLine("type the first number");
            Number1text = Console.ReadLine();
            Console.WriteLine("type the second number");
            NUmber2text = Console.ReadLine();
            NUmber1 = GetNumber(Number1text.ToLower(), out OK);
            if(OK)
            {
                Number1text = "zero";
            }
            Number2 = GetNumber(NUmber2text.ToLower(), out OK);
            if(OK)
            {
                NUmber2text = "zero";
            }
            Total = NUmber1 + Number2;
            Console.WriteLine(Number1text + " + " + NUmber2text + " = " + Total.ToString());
            Console.ReadKey();            
        }
    }
}