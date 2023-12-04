1. Criar uma classe que representa um filme, com dados como seu titulo, duração e elenco. Após isso, colocá-la no namespace **Alura.Filmes**. 

R:

```c#
namespace Alura.Filmes
{
    class Filme
    {
        private List<string> Elenco { get; set; }
        public string Titulo { get; set; }
        public int Duracao { get; set; }

        public Filme(string titulo, int duracao, List<string>? elenco)
        {
            if (elenco == null)
            {
                Elenco = new List<string>();
            }
            else
            {
                Elenco = elenco;
            }
            
            Titulo = titulo;
            Duracao = duracao;
        }

        public void AdicionarElenco(string ator)
        {
            Elenco.Add(ator);
            Console.WriteLine($"{ator} adicionado/a ao elenco.");
        }

        public void ListarElenco()
        {
            if (Elenco.Count == 0)
            {
                Console.WriteLine("Elenco vazio.");
            }
            else
            {
                Console.WriteLine("Elenco... ");
                foreach (var ator in Elenco)
                {
                    Console.WriteLine(ator);
                }
            }
        }
    }
}
```

2. Criar um programa `Program.cs`, instanciar seus 5 filmes favoritos, guardá-los em uma lista e mostrar as suas informações no console.

```c#
using Alura.Filmes;

Filme filme = new Filme("Um sonho de liberdade", 142, new List<string>() {"Tim Robbins", "Morgan Freeman" });
Filme filme2 = new Filme("O poderoso chefão", 175, new List<string>() { "Marlon Brando", "Al Pacino", "Talia Shire"});
Filme filme3 = new Filme("Batman - O Cavaleiro das Trevas", 152, new List<string>() {"Christian Bale", "Heath Ledger", "Maggie Gyleenhaal" });
Filme filme4 = new Filme("Senhor dos Anéis - O Retorno do Rei", 201, new List<string>() {"Elijah Wood", "Ian McKellen", "Viggo Mortensen" });
Filme filme5 = new Filme("Green Book - O Guia", 130, new List<String>() { "Viggo Mortensen", "Mahershala Ali" });

List<Filme> meusFilmesFavoritos =  new List<Filme>();
meusFilmesFavoritos.Add(filme);
meusFilmesFavoritos.Add(filme2);
meusFilmesFavoritos.Add(filme3);
meusFilmesFavoritos.Add(filme4);
meusFilmesFavoritos.Add(filme5);

foreach(Filme f in meusFilmesFavoritos)
{
    Console.WriteLine($"Filme: {f.Titulo}");
    Console.WriteLine($"Duracao: {f.Duracao}");
    f.ListarElenco();
    Console.WriteLine();
}
```

3. Criar uma classe `Artista`, que representa uma pessoa que atua em filmes, no namespace `Alura.Filmes`. A classe deve conter atributos como o nome, idade e uma lista de filmes onde o artista atuou.

```c#
namespace Alura.Filmes
{
   
    public class Artista
    {
        public string Nome { get; set; }
        public int Idade { get; set; }
        public List<Filme> FilmesAtuados { get; set; }
        public int QuantidadeDeFilmes => FilmesAtuados.Count
       
        public Artista(string nome, int idade)
        {
            Nome = nome;
            Idade = idade;
            FilmesAtuados = new List<Filme>(); 
        }


        public void AdicionarFilme(string filme)
        {
            FilmesAtuados.Add(filme);
        }

        public void MostrarFilmesAtuados(){

            if(this.FilmesAtuados.Count == 0){
                Console.WriteLine($"Nenhum filme encontrado na base para {this.Nome}");
                return;
            }

            Console.WriteLine($"Filmes de {this.Nome}...");
            foreach(var filme in FilmesAtuados){
                Console.WriteLine($"Filme: {filme.Titulo}");
            }
        }
    }
}
```

4. Modificar as classes `Artista` e `Filme` do namespace `Alura.Filmes` para que elas sejam consistentes uma com a outra, ou seja, sempre que for adicionado um artista a um filme, terá de ser adicionado também o filme à lista de filmes do artista.

```c#

class Filme
{
    public List<Artista> Elenco { get; set; }
    public string Titulo { get; set; }
    public int Duracao { get; set; }

    public Filme(string titulo, int duracao, List<Artista> elenco)
    {
        if (elenco == null)
        {
            Elenco = new List<Artista>();
        }
        else
        {
            Elenco = elenco;
            foreach (var artista in Elenco)
            {
                artista.AdicionarFilme(this);
            }
        }

        Titulo = titulo;
        Duracao = duracao;
    }

    public void AdicionarElenco(Artista artista)
    {
        Elenco.Add(artista);
        if (!artista.FilmesAtuados.Contains(this))
        {
            artista.AdicionarFilme(this);
        }
        Console.WriteLine($"{artista} adicionado/a ao elenco.");
    }

    public void ListarElenco()
    {
        if (Elenco.Count == 0)
        {
            Console.WriteLine("Elenco vazio.");
        }
        else
        {
            Console.WriteLine("Elenco... ");
            foreach (var artista in Elenco)
            {
                Console.WriteLine(artista.Nome);
            }
        }
    }
}

class Artista
{
    public string Nome { get; set; }
    public int Idade { get; set; }
    public List<Filme> FilmesAtuados { get; set; }
    public int QuantidadeDeFilmes => FilmesAtuados.Count;


    public Artista(string nome, int idade)
    {
        Nome = nome;
        Idade = idade;
        FilmesAtuados = new List<Filme>();
    }

    public void AdicionarFilme(Filme filme)
    {
        FilmesAtuados.Add(filme);
        if(!filme.Elenco.Contains(this)) filme.AdicionarElenco(this);
    }


    public void MostrarFilmesAtuados()
    {

        if (this.FilmesAtuados.Count == 0)
        {
            Console.WriteLine($"Nenhum filme encontrado na base para {this.Nome}");
            return;
        }

        Console.WriteLine($"Filmes de {this.Nome}...");
        foreach (var filme in FilmesAtuados)
        {
            Console.WriteLine($"Filme: {filme.Titulo}");
        }
    }
}

```