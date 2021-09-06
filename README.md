# C-101
class Program
    {
        static void Main(string[] args)
        
        {
            var studentNameList = new ArrayList();
            var studentGradeList = new ArrayList();




            addToData(ref studentNameList, ref studentGradeList);




            ShowResults(studentNameList, studentGradeList);
            Console.Write("Enter 1 to change the results, or 2 to close the progrm: ");//بعد عرض النتائج يتأكد البرنامج اذا اليوزر حاب يعدل شي او لا اذا لا يقفل البرنامج
            if (Console.ReadLine() == "1")
            {
                update(ref studentNameList, ref studentGradeList);//بحال اليوزر يبي يغير قيمه يتم نداء الدالة ذي
            }


        }
        static string gradeRate(int grade)
        {

            if (grade >= 60)
            {
                return "Pass";

            }
            else
            {
                return "Failed";
            }

        }
        static void addToData(ref ArrayList s_List, ref ArrayList g_List)
        {

            while (true)
            {

                //تسمح القيمة ذي ان اللوب يعيد بشكل لا نهائي الى ان يتم ايقافه عن طريق البريك الي بذكرها تخت

                Console.Write("Enter Student Name, or hit ENTER to view results: ");
                var studentName = Console.ReadLine();
                if (studentName == "")
                {

                    break;
                }
                s_List.Add(studentName);
                Console.Write("Enter Student grade: ");
                g_List.Add(Int32.Parse(Console.ReadLine()));
            }

        }
        static void ShowResults(ArrayList s_List, ArrayList g_List)
        {
            Console.WriteLine("\n#" + "\tName" + "\tGrade" + "\tResult");
            for (int i = 0; i < s_List.Count; i++)
            {
                Console.WriteLine("{0}\t{1}\t{2}\t{3}", i + 1, s_List[i], g_List[i], gradeRate((int)g_List[i])); 

            }
        }
        static void update(ref ArrayList s_List, ref ArrayList g_List)
        {
            Console.Write("\nEnter the # of the data entry you would like to update: ");
            var indexOfChange = int.Parse(Console.ReadLine());
            Console.Write("Enter 1 to change name or 2 to change the grade; ");
            var changedValue = Console.ReadLine();
            if (changedValue == "1")
            {
                Console.Write("Enter the new name: ");
                s_List[indexOfChange - 1] = Console.ReadLine();//بحال اراد المستخدم تغيير قيمة الاسم ندخل على القيمة باستخدام الانديكس ونغيرها للقيمة الجديدة الي ادخلها المستخدم
            }
            else
            {
                Console.Write("Enter the new grade: ");
                g_List[indexOfChange - 1] = int.Parse(Console.ReadLine());//الجزئية الي فيها -1 ذي عشان الاختلاف بين الاندكس وادخال اليوزر. عند اليوزر القيم تبدا من 1 في الطباعه بس معنا تبدا من صفر


            }

            Console.WriteLine("\nPrinting new data table...\n");//بحال اراد المستخدم تغيير قيمة الدرجة ندخل على القيمة باستخدام الانديكس ونغيرها للقيمة الجديدة الي ادخلها المستخدم وعند الطباعه يتم اعادة حساب الرسوب او النجاح
            ShowResults(s_List, g_List);
        }

