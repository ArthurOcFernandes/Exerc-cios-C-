1. Criar um programa que permite ao usuário inserir informações de uma pessoa (nome, idade, e e-mail), serializa essas informações em formato JSON e salva em um arquivo.

R:

```c#
using System;
using System.IO;
using System.Text.Json;

class Pessoa
{
    public string Nome { get; set; }
    public int Idade { get; set; }
    public string Email { get; set; }
}

class Program
{
    static void Main()
    {
        // Criar uma instância de Pessoa e obter informações do usuário
        Pessoa pessoa = new Pessoa();
        Console.Write("Digite o nome: ");
        pessoa.Nome = Console.ReadLine();
        Console.Write("Digite a idade: ");
        pessoa.Idade = int.Parse(Console.ReadLine());
        Console.Write("Digite o e-mail: ");
        pessoa.Email = Console.ReadLine();

        // Serializar a pessoa em JSON
        string jsonString = JsonSerializer.Serialize(pessoa);

        // Nome do arquivo para salvar
        string fileName = "pessoa.json";

        // Escrever JSON no arquivo
        File.WriteAllText(fileName, jsonString);

        Console.WriteLine($"Os dados foram salvos em {fileName}");
    }
}
```

2. Criar um programa que lê um arquivo JSON contendo informações de uma pessoa, desserializa essas informações e exibe na tela.

R: 

```c#
using System;
using System.IO;
using System.Text.Json;

class Pessoa
{
    public string Nome { get; set; }
    public int Idade { get; set; }
    public string Email { get; set; }
}

class Program
{
    static void Main()
    {
        // Nome do arquivo para ler
        string fileName = "pessoa.json";

        // Verificar se o arquivo existe
        if (File.Exists(fileName))
        {
            // Ler conteúdo do arquivo JSON
            string jsonString = File.ReadAllText(fileName);

            // Desserializar JSON para objeto Pessoa
            Pessoa pessoa = JsonSerializer.Deserialize<Pessoa>(jsonString);

            // Exibir informações da pessoa
            Console.WriteLine($"Nome: {pessoa.Nome}");
            Console.WriteLine($"Idade: {pessoa.Idade}");
            Console.WriteLine($"E-mail: {pessoa.Email}");
        }
        else
        {
            Console.WriteLine($"O arquivo {fileName} não existe.");
        }
    }
}
```

3. Criar um programa que permite ao usuário inserir informações de várias pessoas, armazena essas informações em uma lista, serializa a lista em formato JSON e salva em um arquivo.

R:

```c#
using System;
using System.Collections.Generic;
using System.IO;
using System.Text.Json;

class Pessoa
{
    public string Nome { get; set; }
    public int Idade { get; set; }
    public string Email { get; set; }
}

class Program
{
    static void Main()
    {
        // Criar uma lista de pessoas
        List<Pessoa> pessoas = new List<Pessoa>();

        // Permitir ao usuário inserir informações de várias pessoas
        while (true)
        {
            Pessoa pessoa = new Pessoa();
            Console.Write("Digite o nome (ou 'sair' para encerrar): ");
            string nome = Console.ReadLine();

            if (nome.ToLower() == "sair")
                break;

            pessoa.Nome = nome;

            Console.Write("Digite a idade: ");
            pessoa.Idade = int.Parse(Console.ReadLine());

            Console.Write("Digite o e-mail: ");
            pessoa.Email = Console.ReadLine();

            // Adicionar pessoa à lista
            pessoas.Add(pessoa);
        }

        // Serializar a lista em JSON
        string jsonString = JsonSerializer.Serialize(pessoas);

        // Nome do arquivo para salvar
        string fileName = "pessoas.json";

        // Escrever JSON no arquivo
        File.WriteAllText(fileName, jsonString);

        Console.WriteLine($"Os dados foram salvos em {fileName}");
    }
}
```

4. Criar um programa que lê um arquivo JSON contendo informações de várias pessoas, desserializa essas informações em uma lista e exibe na tela.

R:

```C#
using System;
using System.Collections.Generic;
using System.IO;
using System.Text.Json;

class Pessoa
{
    public string Nome { get; set; }
    public int Idade { get; set; }
    public string Email { get; set; }
}

class Program
{
    static void Main()
    {
        // Nome do arquivo para ler
        string fileName = "pessoas.json";

        // Verificar se o arquivo existe
        if (File.Exists(fileName))
        {
            // Ler conteúdo do arquivo JSON
            string jsonString = File.ReadAllText(fileName);

            // Desserializar JSON para lista de pessoas
            List<Pessoa> pessoas = JsonSerializer.Deserialize<List<Pessoa>>(jsonString);

            // Exibir informações das pessoas
            Console.WriteLine("Informações das Pessoas:");

            foreach (Pessoa pessoa in pessoas)
            {
                Console.WriteLine($"Nome: {pessoa.Nome}, Idade: {pessoa.Idade}, E-mail: {pessoa.Email}");
            }
        }
        else
        {
            Console.WriteLine($"O arquivo {fileName} não existe.");
        }
    }
}
```

5. Criar um programa que lê um arquivo JSON contendo informações de várias pessoas, permite ao usuário inserir uma idade e exibe as pessoas com aquela idade.

R: 

```c#
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text.Json;

class Pessoa
{
    public string Nome { get; set; }
    public int Idade { get; set; }
    public string Email { get; set; }
}

class Program
{
    static void Main()
    {
        // Nome do arquivo para ler
        string fileName = "pessoas.json";

        // Verificar se o arquivo existe
        if (File.Exists(fileName))
        {
            // Ler conteúdo do arquivo JSON
            string jsonString = File.ReadAllText(fileName);

            // Desserializar JSON para lista de pessoas
            List<Pessoa> pessoas = JsonSerializer.Deserialize<List<Pessoa>>(jsonString);

            // Permitir ao usuário inserir uma idade
            Console.Write("Digite a idade para buscar pessoas: ");
            int idadeParaBuscar = int.Parse(Console.ReadLine());

            // Filtrar pessoas com a idade especificada
            List<Pessoa> pessoasComIdade = pessoas.Where(p => p.Idade == idadeParaBuscar).ToList();

            if (pessoasComIdade.Any())
            {
                // Exibir informações das pessoas com a idade especificada
                Console.WriteLine($"Pessoas com {idadeParaBuscar} anos:");

                foreach (Pessoa pessoa in pessoasComIdade)
                {
                    Console.WriteLine($"Nome: {pessoa.Nome}, E-mail: {pessoa.Email}");
                }
            }
            else
            {
                Console.WriteLine($"Nenhuma pessoa encontrada com {idadeParaBuscar} anos.");
            }
        }
        else
        {
            Console.WriteLine($"O arquivo {fileName} não existe.");
        }
    }
}

```