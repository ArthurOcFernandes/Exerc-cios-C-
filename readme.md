1. Dada uma lista de números, criar uma consulta LINQ para retornar apenas os elementos únicos da lista.

R:

```c#
List<int> numeros = new List<int> { 1, 2, 3, 2, 4, 5, 3, 6, 7, 8, 9, 1 };

var numerosUnicos = numeros.Distinct();

Console.WriteLine("Números únicos na lista:");
foreach (var numero in numerosUnicos)
{
    Console.Write(numero + " ");
}
```

2. Dadas duas listas de números, criar uma consulta LINQ para retornar uma lista que contenha apenas os números que estão presentes em ambas as listas. 

R:

```c#
List<int> lista1 = new List<int> { 1, 2, 3, 4, 5 };
List<int> lista2 = new List<int> { 3, 4, 5, 6, 7 };

var numerosComuns = lista1.Intersect(lista2);

Console.WriteLine("Números presentes em ambas as listas:");
foreach (var numero in numerosComuns)
{
    Console.Write(numero + " ");
}
```

3. Dada uma lista de livros com título, autor e ano de publicação, criar uma consulta LINQ para retornar uma lista com os títulos dos livros publicados após o ano 2000, ordenados alfabeticamente.

R: 

Classe Livro
```c#
class Livro
{
    public string Titulo { get; set; }
    public string Autor { get; set; }
    public int AnoPublicacao { get; set; }
}
```

```c#
List<Livro> livros = new List<Livro>
{
    new Livro { Titulo = "Aprendendo LINQ", Autor = "João Silva", AnoPublicacao = 2005 },
    new Livro { Titulo = "Programação em C#", Autor = "Ana Oliveira", AnoPublicacao = 2010 },
    new Livro { Titulo = "Algoritmos e Estruturas de Dados", Autor = "Carlos Santos", AnoPublicacao = 1998 },
    new Livro { Titulo = "Introdução à Inteligência Artificial", Autor = "Mariana Costa", AnoPublicacao = 2021 },
    new Livro { Titulo = "Design Patterns", Autor = "Paulo Rocha", AnoPublicacao = 2002 }
};

var titulosLivros = livros
    .Where(l => l.AnoPublicacao > 2000)
    .OrderBy(l => l.Titulo)
    .Select(l => l.Titulo);

Console.WriteLine("Títulos de livros publicados após 2000, ordenados alfabeticamente:");
foreach (var titulo in titulosLivros)
{
    Console.WriteLine(titulo);
}

```

4. Dada uma lista de produtos com nome e preço, criar uma consulta LINQ para calcular o preço médio dos produtos.

R: 

classe Produto:
```c#
class Produto
{
    public string Nome { get; set; }
    public decimal Preco { get; set; }
}
```
main:
```c#
List<Produto> produtos = new List<Produto>
        {
            new Produto { Nome = "Laptop", Preco = 1200 },
            new Produto { Nome = "Smartphone", Preco = 800 },
            new Produto { Nome = "Tablet", Preco = 500 },
            new Produto { Nome = "Câmera", Preco = 300 }
        };

        var precoMedio = produtos.Average(p => p.Preco);

        Console.WriteLine("Preço médio dos produtos: " + precoMedio);
```

5. Dada uma lista de strings, criar uma consulta LINQ para ordenar as palavras por comprimento e retornar apenas aquelas que têm mais de 3 caracteres.

R:

```c#
List<string> palavras = new List<string> { "cachorro", "gato", "elefante", "leão", "cobra" };

var palavrasFiltradas = palavras.Where(p => p.Length > 3).OrderBy(p => p.Length);

Console.WriteLine("Palavras com mais de 3 caracteres, ordenadas por comprimento:");
foreach (var palavra in palavrasFiltradas)
{
    Console.Write(palavra + " ");
}
```

6. Dada uma lista de inteiros, criar uma consulta LINQ para retornar apenas os números pares.

```c#
List<int> numeros = new List<int> { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };

var numerosPares = numeros.Where(x => x % 2 == 0);

Console.WriteLine("Números Pares:");
foreach (var numero in numerosPares)
{
    Console.Write(numero + " ");
}
```