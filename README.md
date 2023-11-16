# Soluções em POO

Obs: todas essas soluções foram feitas no curso e pelo autor do curso.

![Untitled](Soluc%CC%A7o%CC%83es%20em%20POO%20cf0f99d587a44aceaa6f4b1d7d7a0e07/Untitled.png)

Aqui foi realizado um solução sem POO

```csharp
using System;
using System.Globalization;

internal class Program {
    private static void Main(string[] args) {

        double xA, xB, xC, yA, yB, yC;

        Console.WriteLine( "Entre com as medidas do triangulo X:");
        xA = double.Parse(Console.ReadLine(),CultureInfo.InvariantCulture);
        xB = double.Parse(Console.ReadLine(),CultureInfo.InvariantCulture);
        xC = double.Parse(Console.ReadLine(),CultureInfo.InvariantCulture);
        Console.WriteLine("Entre com as medidas do triangulo Y:");
        yA = double.Parse(Console.ReadLine(),CultureInfo.InvariantCulture);
        yB = double.Parse(Console.ReadLine(),CultureInfo.InvariantCulture);
        yC = double.Parse(Console.ReadLine(),CultureInfo.InvariantCulture);

        double p = (xA+xB+xC)/2.0;
        double areaX = Math.Sqrt(p*(p - xA) * (p - xB) * (p - xC));

         p = (yA+yB+yC)/2.0;
        double areaY = Math.Sqrt(p*(p - yA) * (p - yB) * (p - yC));

        Console.WriteLine("Área de X = "+ areaX.ToString("F4",CultureInfo.InvariantCulture));
        Console.WriteLine("Área de Y = "+ areaY.ToString("F4", CultureInfo.InvariantCulture));

        if (areaY>areaX) {
            Console.WriteLine("Maior área : Y");
        }
        else {
            Console.WriteLine("Maior área : X");
        }
    }
}
```

Agora a solução de calculo de um triangulo com POO.

codigo principal:

```csharp
using PrimeiroProjeto;
using System;
using System.Globalization;

internal class Program {
    private static void Main(string[] args) {

        Triangulo x, y;

        x = new Triangulo();
        y = new Triangulo();

        Console.WriteLine( "Entre com as medidas do triangulo X:");
        x.A = double.Parse(Console.ReadLine(),CultureInfo.InvariantCulture);
        x.B = double.Parse(Console.ReadLine(),CultureInfo.InvariantCulture);
        x.C = double.Parse(Console.ReadLine(),CultureInfo.InvariantCulture);
        Console.WriteLine("Entre com as medidas do triangulo Y:");
        y.A = double.Parse(Console.ReadLine(),CultureInfo.InvariantCulture);
        y.B = double.Parse(Console.ReadLine(),CultureInfo.InvariantCulture);
        y.C = double.Parse(Console.ReadLine(),CultureInfo.InvariantCulture);

        double areaX = x.Area();

        double areaY = y.Area();

        Console.WriteLine("Área de X = "+ areaX.ToString("F4",CultureInfo.InvariantCulture));
        Console.WriteLine("Área de Y = "+ areaY.ToString("F4", CultureInfo.InvariantCulture));

        if (areaY>areaX) {
            Console.WriteLine("Maior área : Y");
        }
        else {
            Console.WriteLine("Maior área : X");
        }
    }
}
```

Classe:

```csharp
using System;

namespace PrimeiroProjeto {
    internal class Triangulo {

        public double A;    // nome de atributo sempre com a letra maiuscula
        public double B;
        public double C;

        public double Area() { // criação de metodo com função
            double p = (A+B+C)/2.0;

            return  Math.Sqrt(p*(p-A)*(p-B)*(p-C));
            
        }
    }
}
```

![Untitled](Soluc%CC%A7o%CC%83es%20em%20POO%20cf0f99d587a44aceaa6f4b1d7d7a0e07/Untitled%201.png)

Codigo principal:

```csharp
using PrimeiroProjeto;
using System;
using System.Globalization;

internal class Program {
    private static void Main(string[] args) {

        Produto p = new Produto();

        Console.WriteLine("Entre os dados do produto:");
        Console.Write("Nome:");
        p.Nome = Console.ReadLine();
        Console.Write("Preço: ");
        p.Preco = double.Parse(Console.ReadLine(),CultureInfo.InvariantCulture);
        Console.Write("Quantidade no estoque: ");
        p.Quantidade = int.Parse(Console.ReadLine(), CultureInfo.InvariantCulture);

        Console.WriteLine();
        Console.WriteLine("Dados do produto: " + p);

        Console.WriteLine();
        Console.Write("Digite o numero de produtos a ser adicionada no estoque: ");
        int qte = int.Parse(Console.ReadLine());
        p.AdicionarProdutos(qte);

        Console.WriteLine();
        Console.WriteLine("Dados atualizados: " + p);

        Console.WriteLine();
        Console.Write("Digite o numero de produtos a ser removidos no estoque: ");
         qte = int.Parse(Console.ReadLine());
        p.RemoverProdutos(qte);

        Console.WriteLine();
        Console.WriteLine("Dados atualizados: " + p);
    }
}
```

Classe:

```csharp
using System;
using System.Globalization;

namespace PrimeiroProjeto {
    internal class Produto {

        public String Nome;
        public double Preco;
        public int Quantidade;

        public double ValorTotalEmEstoque() {
            return Preco * Quantidade;
        }

        public void AdicionarProdutos(int quantidade) {
            Quantidade += quantidade;
        }

        public void RemoverProdutos(int quantidade) {
            Quantidade -= quantidade;
        }

        public override string ToString() {
            return Nome +
                    ", $ "+
                    Preco.ToString("F2", CultureInfo.InvariantCulture) +
                    ", "+
                    Quantidade +
                    " unidades, Total: $ "+
                    ValorTotalEmEstoque().ToString("F2", CultureInfo.InvariantCulture);
        }
    }
}
```
