1. Criar um programa que permita ao usuário inserir o nome do aluno e suas notas, e em seguida calcule e exiba a média das notas.

```
Dictionary<string, List<double>> notasAlunos = new Dictionary<string, List<double>>();

// Adicione notas para alguns alunos
notasAlunos["João"] = new List<double> { 8.5, 9.0, 7.5 };
notasAlunos["Maria"] = new List<double> { 7.0, 8.0, 6.5 };

foreach (var aluno in notasAlunos)
{
    double soma = 0;
    for(int i = 0; i < aluno.Value.Count ; i++){
        soma += aluno.Value[i];
    }
    double media = soma / aluno.Value.Count;
    Console.WriteLine($"Média de {aluno.Key}: {media}");
}
```


2. 2. Criar um programa que gerencie o estoque de uma loja. Utilize um dicionário para armazenar produtos e suas quantidades em estoque e mostre, a partir do nome de um produto, sua quantidade em estoque. 

```
Dictionary<string, int> estoque = new Dictionary<string, int>
{
    { "camisetas", 50 },
    { "calças", 30 },
    { "tênis", 20 },
    // Adicione mais produtos conforme necessário
};

string produto = "camisetas";

if (estoque.ContainsKey(produto))
{
    Console.WriteLine($"Quantidade em estoque de {produto}: {estoque[produto]} unidades.");
}
else
{
    Console.WriteLine("Produto não encontrado no estoque.");
}
```

3. Crie um programa que implemente um quiz simples de perguntas e respostas. Utilize um dicionário para armazenar as perguntas e as respostas corretas.

```
Dictionary<string, string> perguntasERespostas = new Dictionary<string, string>
{
    { "Qual é a capital do Brasil?", "Brasília" },
    { "Quanto é 7 vezes 8?", "56" },
    { "Quem escreveu 'Romeu e Julieta'?", "William Shakespeare" },
    // Adicione mais perguntas e respostas conforme necessário
};

int pontuacao = 0;

foreach (var pergunta in perguntasERespostas)
{
    Console.WriteLine(pergunta.Key);
    Console.Write("Sua resposta: ");
    string respostaUsuario = Console.ReadLine();

    if (respostaUsuario.ToLower() == pergunta.Value.ToLower())
    {
        Console.WriteLine("Correto!\n");
        pontuacao++;
    }
    else
    {
        Console.WriteLine($"Incorreto. A resposta correta é: {pergunta.Value}\n");
    }
}

Console.WriteLine($"Pontuação final: {pontuacao} de {perguntasERespostas.Count}");

```

4. Criar um programa que simule um sistema de login utilizando um dicionário para armazenar nomes de usuário e senhas.

```
Dictionary<string, string> usuarios = new Dictionary<string, string>
{
    { "user1", "senha123" },
    { "user2", "abc456" },
    // Adicione mais usuários conforme necessário
};

string nomeUsuario = "user1";
string senha = "senha123";

if (usuarios.ContainsKey(nomeUsuario) && usuarios[nomeUsuario] == senha)
    Console.WriteLine("Login bem-sucedido!");
else
    Console.WriteLine("Nome de usuário ou senha incorretos.");
```
