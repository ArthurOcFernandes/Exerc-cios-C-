1. Modelar e desserializar a classe Filme, que pode ser encontrada no [endpoint disponibilizado](https://raw.githubusercontent.com/ArthurOcFernandes/Exerc-cios-C-/curso-4-aula-2/Jsons/TopMovies.json)

R: 
Classe Filme:
```c#
using System.Text.Json.Serialization;
namespace Filmes;

internal class Filme
{
    [JsonPropertyName("title")]
    public string? Titulo { get; set; }
    [JsonPropertyName("year")]
    public string? Ano {  get; set; }
    [JsonPropertyName("crew")]
    public string? Elenco { get; set; }
    [JsonPropertyName("imDbRating")]
    public string? Nota { get; set; }
    public string FichaTecnica => $"\n\nTitulo: {Titulo} ({Ano}) - Nota: {Nota}\nElenco: [{Elenco}]\n\n";
}
```
Program.cs:
```c#
using Filmes;

using System.Text.Json;

using (HttpClient client = new HttpClient())
{
    try
    {
        string resposta = await client.GetStringAsync("https://raw.githubusercontent.com/ArthurOcFernandes/Exerc-cios-C-/curso-4-aula-2/Jsons/TopMovies.json");
       
        var filmes = JsonSerializer.Deserialize<List<Filme>>(resposta);
        foreach(var filme in filmes)
        {
            Console.WriteLine(filme.FichaTecnica);
        }
    }
    catch (Exception ex)
    {
        Console.WriteLine($"Temos um problema: {ex.Message}");
    }
}
```

2. Modelar e desserializar a classe Pais, que pode ser encontrada no [endpoint disponibilizado](https://raw.githubusercontent.com/ArthurOcFernandes/Exerc-cios-C-/curso-4-aula-2/Jsons/Paises.json)

R: 

Classe Pais:
```c#

namespace Paises;
using System.Text.Json.Serialization;
internal class Pais
{
    [JsonPropertyName("nome")]
    public string? Nome { get; set; }
    [JsonPropertyName("capital")]
    public string? Capital { get; set; }
    [JsonPropertyName("populacao")]
    public int? Populacao { get; set; }
    [JsonPropertyName("continente")]
    public string? Continente { get; set; }
    [JsonPropertyName("idioma")]
    public string? Idioma { get; set; }
    public string Informacoes => $"Pais: {Nome} - Capital: {Capital} - Populacao: {Populacao}";

}
```
Program.cs:

```c#
using Paises;
using System.Text.Json;

using (HttpClient client = new HttpClient())
{
    try
    {
        string resposta = await client.GetStringAsync("https://raw.githubusercontent.com/ArthurOcFernandes/Exerc-cios-C-/curso-4-aula-2/Jsons/Paises.json");
        //Console.WriteLine(resposta);
        var paises = JsonSerializer.Deserialize<List<Pais>>(resposta);
        foreach (var pais in paises)
        {
            Console.WriteLine(pais.Informacoes);
        }
    }
    catch (Exception ex)
    {
        Console.WriteLine($"Temos um problema: {ex.Message}");
    }
}
```



3. Modelar e desserializar a classe Carro, que pode ser encontrada no [endpoint disponibilizado](https://raw.githubusercontent.com/ArthurOcFernandes/Exerc-cios-C-/curso-4-aula-2/Jsons/Carros.json)

R:
Classe Carro:
```c#
using System.Text.Json.Serialization;

namespace Carros;

internal class Carro
{
    [JsonPropertyName("marca")]
    public string? Marca {  get; set; }
    [JsonPropertyName("modelo")]
    public string? Modelo { get; set;}
    [JsonPropertyName("ano")]
    public int? Ano { get; set; }
    [JsonPropertyName("tipo")]
    public string? Tipo { get; set; }

    public string Informacoes => $"Carro {Marca} {Modelo} {Ano} {Tipo}";

}
```
Program.cs:
```c#
using Carros;

using System.Text.Json;

using (HttpClient client = new HttpClient())
{
    try
    {
        string resposta = await client.GetStringAsync("https://github.com/ArthurOcFernandes/Exerc-cios-C-/raw/curso-4-aula-2/Jsons/Carros.json");
       
        var carros = JsonSerializer.Deserialize<List<Carro>>(resposta);
        foreach(var carro in carros)
        {
            Console.WriteLine(carro.Informacoes);
        }
    }
    catch (Exception ex)
    {
        Console.WriteLine($"Temos um problema: {ex.Message}");
    }
}
```

4. Modelar e desserializar a classe Livro, que pode ser encontrada no [endpoint disponibilizado](https://raw.githubusercontent.com/ArthurOcFernandes/Exerc-cios-C-/curso-4-aula-2/Jsons/Livros.json)

R:
classe Livro:
```c#
using System.Text.Json.Serialization;

namespace Livros;

internal class Livro
{

    [JsonPropertyName("titulo")]
    public string? Titulo { get; set; }
    [JsonPropertyName("autor")]
    public string? Autor {  get; set; }
    [JsonPropertyName("ano_publicacao")]
    public int? Ano { get; set; }
    [JsonPropertyName("genero")]
    public string? Genero { get; set; }

    public string FichaTecnica => $"Titulo: {Titulo}\nAutor: {Autor}\nAno: {Ano}\nGenero: {Genero}\n\n";
}
```
Program.cs:
```c#
using Livros;

using System.Text.Json;

using (HttpClient client = new HttpClient())
{
    try
    {
        string resposta = await client.GetStringAsync("https://github.com/ArthurOcFernandes/Exerc-cios-C-/raw/curso-4-aula-2/Jsons/Livros.json");
       
        var livros = JsonSerializer.Deserialize<List<Livro>>(resposta);
        foreach(var livro in livros)
        {
            Console.WriteLine(livro.FichaTecnica);
        }
    }
    catch (Exception ex)
    {
        Console.WriteLine($"Temos um problema: {ex.Message}");
    }
}
```