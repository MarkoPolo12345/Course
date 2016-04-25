# Course
namespace MarinaPikulCourse
{
    public partial class Form1 : Form
    {
      

        public Form1()
        {
            InitializeComponent();
            //textboxes.Add
            
        }

        private void nemirToolStripMenuItem_Click(object sender, EventArgs e)//Добавить заключенного
        {
            Form c = new Adding();
            c.Show();
        }



        private void marinaToolStripMenuItem1_Click(object sender, EventArgs e)//Найти заключенного
        {
            textBox12.Visible = true;
            comboBox1.Visible = true;
            button2.Visible = true;
            checkedListBox1.Visible = true;


        }

     

        private void marinaToolStripMenuItem_Click(object sender, EventArgs e)
        {
           
        }

        private void AboutToolStripMenuItem_Click(object sender, EventArgs e)
        {
            Form c = new About();
            c.Show();
        }

        
        

       
        private void button2_Click(object sender, EventArgs e)// Найти
        {
            StreamReader streamReader = new StreamReader("mainfile.txt");
            string str = "";
            int counter = 0;
            while (!streamReader.EndOfStream)
            {

                str = streamReader.ReadLine();
                counter++;

               
            }
            object[] arr = new object[counter];
            str = "";
            counter = 0;
            streamReader = new StreamReader("mainfile.txt");
            while (!streamReader.EndOfStream)
            {

                str = streamReader.ReadLine();
                arr[counter] = str;
                counter++;
            }

            checkedListBox1.Items.AddRange(arr);
            
            label1.Visible = true;
        }

        private void button3_Click(object sender, EventArgs e)
        {
            FileInfo file = new FileInfo("mainfile.txt");
            if (file.Exists == true) //Если файл существует
            {
                file.Delete(); //Удаляем
            }
            else MessageBox.Show("Файла не существует!!");
        }
        namespace MarinaPikulCourse.Model
{
    [Serializable]
    class ListOfPrisoners: CommonFunc
    {
        List<Prisoner> pris = new List<Prisoner>();
       
        public List<Prisoner> Pris
            {
                set { pris = value; }
                get { return pris; }
            }

            /// <summary>
            /// Индексатор списка.
            /// </summary>
            /// <param name="i"></param>
            /// <returns></returns>
            public Prisoner this[int i]
            {
                set { pris[i] = value; }
                get { return pris[i]; }
            }

            /// <summary>
            /// Длина списка.
            /// </summary>
            public int Length
            {
                get { return pris.Count; }
            }

            /// <summary>
            /// Сериализация списка.
            /// </summary>
            public void Save()
            {
                BinaryFormatter binFormat = new BinaryFormatter();
                using (Stream fStream = new FileStream("listOfAuthors.dat", FileMode.OpenOrCreate))
                {
                    binFormat.Serialize(fStream, pris);
                }
            }

            /// <summary>
            /// Десериализация списка.
            /// </summary>
            public void Open()
            {
                BinaryFormatter binFormat = new BinaryFormatter();
                try
                {
                    using (Stream fStream = new FileStream("listOfAuthors.dat", FileMode.OpenOrCreate))
                    {
                        pris = (List<Prisoner>)binFormat.Deserialize(fStream);
                    }
                }
                catch { }
            }

            /// <summary>
            /// Добавление нового автора в список.
            /// </summary>
            /// <param name="a"></param>
            public void Add(Prisoner a)
            {
                pris.Add(a);
            }

            /// <summary>
            /// Удаление автора по индексу в списке.
            /// </summary>
            /// <param name="n"></param>
            public void RemoveAt(int n)
            {
                pris.RemoveAt(n);
            }

            /// <summary>
            /// Проверка на то, если ли уже определенный автор в списке.
            /// </summary>
            /// <param name="ic"></param>
            /// <returns></returns>
            public bool IsCopy(Prisoner ic)
            {
                foreach (Prisoner a in pris)
                {
                    if (a.Name == ic.Name && )
                        return true;
                }
                return false;
            }
        }
    }
}
