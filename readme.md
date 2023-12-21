1. Escrever um programa que faça uam requisição para a API de games **CheapShark** e mostre na tela a lista de promoções cadastrada na ferramenta (Você pode utilizar o endpoint: https://www.cheapshark.com/api/1.0/deals).

R:

```c#
using (HttpClient client = new HttpClient())
{
    string resposta = await client.GetStringAsync("https://www.cheapshark.com/api/1.0/deals");
    Console.WriteLine(resposta);
}
```

2. Escrever um programa que solicite dois números `a` e `b` lidos do teclado e realize a divisão de `a` por `b`. Caso essa operação não seja possível, mostrar uma mensagem no console  que deixe claro o erro ocorrido.

R:

```c#
try
{
    Console.Write("Digite o numerador: ");
    int numerador = int.Parse(Console.ReadLine());

    Console.Write("Digite o denominador: ");
    int denominador = int.Parse(Console.ReadLine());

    int resultado = numerador / denominador;
    Console.WriteLine($"Resultado: {resultado}");
}
catch (DivideByZeroException ex)
{
    Console.WriteLine($"Erro: na matemática não é permitida a divisão por 0.");
}

```

3. Declarar uma lista de inteiros e tente acessar um elemento em um índice inexistente. Tratar a exceção apropriada.

R:

```c#
try
{
    List<int> numeros = new List<int> { 1, 2, 3 };
    Console.WriteLine($"Elemento no índice 5: {numeros[5]}");
}
catch (ArgumentOutOfRangeException ex)
{
    Console.WriteLine($"Erro: {ex.Message}");
}

```

4. Criar uma classe simples com um método e chame esse método em um objeto nulo. Tratar a exceção de método em objeto nulo.


R: 

```c#
try
{
    MinhaClasse objetoNulo = null;
    objetoNulo.Meumetodo();
}
catch (NullReferenceException ex)
{
    Console.WriteLine($"Erro: {ex.Message}");
}

```