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
