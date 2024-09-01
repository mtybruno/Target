
# Desafio da Target Sistemas para a vaga em Estágio de Desenvolvimento

*Segue a baixo as questões propostas no desafio tecnico para a vaga de estagio, os codigos foram escritos em C#.*

### Questão 1

```csharp
int INDICE = 13, SOMA = 0, K = 0;
while (K < INDICE)
{
    K = K + 1;
    SOMA = SOMA + K;
}
Console.WriteLine(SOMA);
```

Nesta questão o código faz a soma de 1 a 13.

K = 0 e SOMA = 0, a cada iteração **K** é aumentado em 1 e o valor de **K** é adicionado a **SOMA**, então o loop continua até que **K** seja igual a 13, no final o valor total de **SOMA** é 91


### Questão 2

```csharp
using System;

class IsItFibonnaci
{
    static bool IsFibonacci(int numero)
    {
        int a = 0, b = 1;
        while (b <= numero)
        {
            if (b == numero)
            {
                return true;
            }
            int temp = a;
            a = b;
            b = temp + b;
        }
        return false;
    }

    static void Main()
    {
        Console.Write("Digite um numero: ");
        int numero = int.Parse(Console.ReadLine());

        if (IsFibonacci(numero))
        {
            Console.WriteLine($"O numero {numero} pertence a sequencia de Fibonacci.");
        }
        else
        {
            Console.WriteLine($"O numero {numero} não pertence a sequencia de fibonacci.");
        }
    }
}
```

Nesta questão o codigo verifica se o número digitado pertence ou não a sequencia fibonnaci *(sequencia em que cada numero a partir do terceiro é a soma dos dois antecessores.)* e retorna de acordo. 

[Aqui](https://github.com/mtybruno/Target_references/blob/main/Fibonnaci.md) segue uma versão com um loop while que pergunta se o usuario quer verificar outro número e lida com input de caracteres inválidos.

### Questão 3 

```csharp
using System;
using System.Linq;
using Newtonsoft.Json.Linq;

class Program
{
    static void Main()
    {
        string json = @"
        {
            'faturamento': [0, 22174.1664, 24537.6698, 26139.6134, 0, 0, 0, 26742.6612, 0, 0, 42889.2258, 46251.174, 11191.4722, 0, 0, 0, 0, 18335.6852, 0, 4350.6977, 0, 13327.1025, 0, 0, 12404.8796, 0, 0, 43829.1667, 0, 0]
        }";

        var faturamento = JArray.Parse(JObject.Parse(json)["faturamento"].ToString())
                            .Select(f => (double)f)
                            .Where(f => f > 0)
                            .ToList();

        double menorFaturamento = faturamento.Min();
        double maiorFaturamento = faturamento.Max();
        double mediaMensal = faturamento.Average();
        int AcimaMedia = faturamento.Count(f => f > mediaMensal);

        Console.WriteLine($"Menor faturamento: R${menorFaturamento:F2}");
        Console.WriteLine($"Maior faturamento: R${maiorFaturamento:F2}");
        Console.WriteLine($"faturamento acima da média: {AcimaMedia}");
    }
}
```

A questão 3 pede um programa para processar dados de faturamento diário de uma distribuidora, que podem estar em JSON ou XML. O programa deve calcular e retornar o menor e maior valor de faturamento do mês, além do número de dias com faturamento superior à média mensal, ignorando dias sem faturamento. Primeiro, os dados são lidos e filtrados para incluir apenas dias com faturamento. Em seguida, calcula-se o menor, maior valor e a média dos faturamentos, e conta-se os dias com faturamento acima da média. [Faturamento em Json](https://github.com/mtybruno/Target_references/blob/main/faturamento.md)


### Questão 4

```csharp
namespace CalculoFaturamento
{
    class Faturamento
    {
        static void Main()
        {
            // Valores dos faturamentos
            double sp = 67836.43;
            double rj = 36678.66;
            double mg = 29229.88;
            double es = 27165.48;
            double outros = 19849.53;

            //Total
            double faturamentoTotal = sp + rj + mg + es + outros;

            //Percentual de cada estado
            double percentualSP = (sp / faturamentoTotal) * 100;
            double percentualRJ = (rj / faturamentoTotal) * 100;
            double percentualMG = (mg / faturamentoTotal) * 100;
            double percentualES = (es / faturamentoTotal) * 100;
            double percentualOutros = (outros / faturamentoTotal) * 100;

            Console.WriteLine("Percentual de faturamento total:");
            Console.WriteLine($"SP: {percentualSP:F2}%");
            Console.WriteLine($"RJ: {percentualRJ:F2}%");
            Console.WriteLine($"MG: {percentualMG:F2}%");
            Console.WriteLine($"ES: {percentualES:F2}%");
            Console.WriteLine($"outros: {percentualOutros:F2}%");
        }
    }
}
```
Nesta questão o codigo calcula e exibe o percentual de participação de cada estado no faturamento total da distribuidora.O calculo é feito dividindo o faturamento de cada estado pelo faturamento total e multiplicando por 100 para obter a porcentagem.

### Questão 5

```csharp
namespace DesafioTarget
{
    class StringConverter
    {
        static void Main()
        {

            Console.Write("Digite uma palavra ou frase: ");
            string entrada = Console.ReadLine();

            // converter os inputs em arrays
            char[] caracteres = entrada.ToCharArray();

            // inverte os caracteres
            int inicio = 0;
            int fim = caracteres.Length - 1;

            while (inicio < fim)
            {
                // troca os caracteres
                char temp = caracteres[inicio];
                caracteres[inicio] = caracteres[fim];
                caracteres[fim] = temp;

                // move os indices para o centro
                inicio++;
                fim--;
            }

            // cconverte o array de volta para uma string
            string inverte = new string(caracteres);

            // exibe a string invertida
            Console.WriteLine($"String invertida: {inverte}");
        }
    }
}
```
Na questão 5, o programa inverte os caracteres de uma string fornecida pelo user. o codigo então converte a string em um array de caracteres, troca os elementos do início com os do fim, e então retorna o array para exibir a string invertida.











