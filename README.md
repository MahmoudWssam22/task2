# task2
using System.Security.Cryptography;

internal class Program
{
    private static void Main(string[] args)
    {
        char choise;
        Console.WriteLine("Hello, World!");
        library newBook = new library("0","0",0,0);
        while (true)
        {
            Console.WriteLine("**********************************************************");
            Console.WriteLine("LIBRARY MANIGMENT SYSTEM");
            Console.WriteLine("1. Add a Book");
            Console.WriteLine("2. Disblay Book");
            Console.WriteLine("3. Serch by Titel");
            Console.WriteLine("4. Serch by ID");
            Console.WriteLine("5. Exit");
            choise =Char.Parse(Console.ReadLine());
            switch (choise)
            {
                case '1':
                    Console.WriteLine("enter the Titel : ");
                    string TITEL = Console.ReadLine();
                    Console.WriteLine("enter the Auther : ");
                    string AUTHER = Console.ReadLine();
                    Console.WriteLine("enter the ID : ");
                    int ID =Convert.ToInt32(Console.ReadLine());
                    Console.WriteLine("enter the publitied year : ");
                    int PUBLITIONYEAR = Convert.ToInt32(Console.ReadLine());
                    newBook.Set(TITEL,AUTHER,ID,PUBLITIONYEAR);
                    break;

                case '2':
                    newBook.get();
                    break;
            }
        }

    }
}

 class Book
{   // THE VARIABYLS AS PRotected to inheret to the library class
     
    protected int Id , PublitiYear;
    protected string Titel , Auther ;

    // THE CONSTRACTOR
    public Book(string _Titel, string _Auther, int _Id, int _PublitiYear)
    {
        Titel = _Titel;
        Auther = _Auther;
        Id = _Id;
        PUBLITIONYEAR= _PublitiYear;
    }
    //THE PROPARTES
    public int ID
    {
        set { Id = value; }
        get { return Id; }
    }
    public int PUBLITIONYEAR
    {
        set { PublitiYear = value; }
        get { return PublitiYear; }
    }
    public string TITEL
    {
        set { Titel = value; }
        get { return Titel; }
    }
    public string AUTHER
    {
        set { Auther = value; }
        get { return Auther; }
    }

}

 class library :Book
{   // a list to store the data
    List<Book> books = new List<Book>();

    // a constructor based on the inhereted Book class
    public library(string _Titel, string _Auther, int _Id, int _PublitiYear) : base(_Titel, _Auther, _Id, _PublitiYear){}

    // a set method to store the data
    public void Set(string _Titel, string _Auther, int _Id, int _PublitiYear)
    {
        Titel = _Titel;
        Auther = _Auther;
        Id = _Id;
        PublitiYear = _PublitiYear;

        books.Add(new Book(Titel, Auther, Id, PublitiYear));
    }
    // a get method to display the data
    public void get()
    {
        foreach (Book book in books) 
        {
            Console.WriteLine($"The Titel : "+Titel);
            Console.WriteLine($"The Auther : " + Auther);
            Console.WriteLine($"The ID : " + Id);
            Console.WriteLine($"The Publitied Year : " + PublitiYear);
        }
    }
}
