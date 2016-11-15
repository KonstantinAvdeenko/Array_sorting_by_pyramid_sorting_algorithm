using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;

namespace SortirovkaPiramide
{
    class Class1
    {
        static void Main(string[] args)
        {   // заполняет массив случайными числами
            Int32[] arr = new Int32[100];
            Random rd = new Random();
            for (Int32 i = 0; i < arr.Length; ++i)
            {
                arr[i] = rd.Next(1, 101);
            }
            System.Console.WriteLine("Массив до пирамидальной сортировки:");
            foreach (Int32 x in arr)
            {
                System.Console.Write(x + " ");
            }

            Pyramid_Sort(arr, arr.Length); // результат пирамидальной сортировки из метода Pyramid_Sort 

            System.Console.WriteLine("\n\nМассив после пирамидальной сортировки:");
            foreach (Int32 x in arr)
            {
                System.Console.Write(x + " ");
            }
            System.Console.WriteLine("\n\nНажмите enter для выхода");
            System.Console.ReadLine();
        }

        static Int32 add2pyramid(Int32[] arr, Int32 i, Int32 N)
        {
            Int32 imax;
            Int32 buf;
            if ((2 * i + 2) < N) // Преобразование массива к первичной пирамидальной куче или двоичному дереву
            {
                if (arr[2 * i + 1] < arr[2 * i + 2]) imax = 2 * i + 2; // меньшие элементы ставятся в правую часть пирамидальной кучи от первого элемента
                else imax = 2 * i + 1; // большие элементы ставятся в левую часть пирамидальной кучи от первого элемента
            }
            else imax = 2 * i + 1; // наименьший элемент ставится на вершину пирамидальной кучи  
            if (imax >= N) return i; // после преобразования пирамидальной кучи все ее элементы передаются для сортировки в метод Pyramid_Sort  
            if (arr[i] < arr[imax])  // в случае не соответствия условию полного перебора элементов массива данный метод повторяется с уже внесенными изменениями  
            {
                buf = arr[i];
                arr[i] = arr[imax];
                arr[imax] = buf;
                if (imax < N / 2) i = imax;  
            }
            return i;
        }

        static void Pyramid_Sort(Int32[] arr, Int32 len)
        {
            // постройка пирамиды, ее просеивание с нижнего уровня и полное деление пирамидальной кучи на левую и правую части, где в обоих частях наименьшие числа вверху пирамиды
            for (Int32 i = len / 2 - 1; i >= 0; --i)
            {
                long prev_i = i;
                i = add2pyramid(arr, i, len);
                if (prev_i != i) ++i;
            }

            // сортировка построенной пирамиды начиная с последнего элемента массива
            Int32 buf;
            for (Int32 k = len - 1; k > 0; --k)
            {  // фиксация перестановок элементов массива по значиниям в них
                buf = arr[0];
                arr[0] = arr[k];
                arr[k] = buf;
                Int32 i = 0, prev_i = -1;
                while (i != prev_i)
                {
                    prev_i = i;
                    i = add2pyramid(arr, i, k);
                }
            }
        }
    }
}