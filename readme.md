1. Modelar uma classe `Conta`, que tenha como atributos uma classe `Titular`, além de informações da conta, como agência, número da conta, saldo e limite, bem como um método que devolva as informações da conta de forma detalhada.

R:

```c#
class Titular
{
    public string Nome {get; set;}
    public string Cpf {get; set;}
    public string Endereco {get; set;}
}

class Conta
{
    public Titular Titular {get; set;}
    public int Agencia {get; set;}
    public int NumeroDaConta {get; set;}
    public double Saldo {get; set;}
    public double Limite {get; set;}

    public string Informacoes => $"Conta nº {this.NumeroDaConta}, Agência {this.Agencia}, Titular: {this.Titular.Nome} - Saldo: {this.Saldo}";
}
```

2. Instanciar um objeto do tipo Conta e um do tipo Titular e mostrar as informações de Titular, a partir da Conta.

R:

```c#
Titular t = new();
Conta c = new();

t.Nome = "George Harrison";
t.Cpf = "000.000.000-00";
t.Endereco = "Rua dos Besouros - Liverpool";

c.Titular = t;
c.Agencia = 1;
c.NumeroDaConta = 2234;
c.Saldo = 10000000.0;
c.Limite = 100000.0;

Console.WriteLine("Informações do Titular: ");
Console.WriteLine($"Nome: {c.Titular.Nome}");
Console.WriteLine($"CPF: {c.Titular.Cpf}");
Console.WriteLine($"Endereco: {c.Titular.Endereco}");

```

3. Desenvolver uma classe que represente um estoque de produtos, e que tenha as funcionalidades de adicionar novos produtos, e exibir todos os produtos no estoque.

R:

```c#
class Produto
{
    private double preco;
    private int estoque;
    public string Nome {get; set;}
    public string Marca {get; set;}
    public double Preco {
        get => preco; 
        set
        {
            if(value > 0)
                preco = value;
            else
                preco = 10;
        }
    }
    
    public int Estoque {
        get => estoque; 
        set 
        {
            if(value > 0)
                estoque = value;
            else
                estoque = 0;

        }
    }

    public string Descricao => $"{this.Nome} {this.Marca} - {this.Preco} - Quantidade: {this.Estoque}";

}


class EstoqueDeProdutos
{
    private List<Produto> Produtos {get; set;} = new List<Produto>();

    public void AdicionarProduto(Produto produto)
    {
        Produtos.Add((produto));
        Console.WriteLine($"Produto {produto.Nome} adicionado ao estoque");
    }

    public void ExibirProdutos()
    {
        if(Produtos.Count == 0)
        {
            Console.WriteLine("Estoque vazio. Nenhum produto disponível");
        }else
        {
            Console.WriteLine("Lista de produtos no estoque:");
            foreach(var produto in Produtos){
                Console.WriteLine(produto.Descricao);
            }
        }
    }
}
```

4. Modelar o sistema de uma escola. Crie classes para Aluno, Professor e Disciplina. A classe Aluno deve ter informações como nome, idade e notas. A classe Professor deve ter informações sobre nome e disciplinas lecionadas. A classe Disciplina deve armazenar o nome da disciplina e a lista de alunos matriculados.

R: 

```c#
class Aluno
{
    public string Nome { get; set; }
    public int Idade { get; set; }
    public List<double> Notas { get; set; } = new List<double>();
}

class Professor
{
    public string Nome { get; set; }
    public List<string> DisciplinasLecionadas { get; set; } = new List<string>();
}

class Disciplina
{
    public string NomeDisciplina { get; set; }
    public List<Aluno> AlunosMatriculados { get; set; } = new List<Aluno>();
}
```

5. Modelar um sistema para um restaurante com classes como Restaurante, Mesa, Pedido e Cardapio. A classe Restaurante deve ter mesas que podem ser reservadas e um cardápio com itens que podem ser pedidos. Os pedidos podem estar associados a uma mesa.

R: 

```c#
class ProdutoRestaurante
{
    public string Nome { get; set; }
    public decimal Preco { get; set; }
}

class Mesa
{
    public int Numero { get; set; }
    public List<Pedido> Pedidos { get; set; } = new List<Pedido>();
}

class Pedido
{
    public ProdutoRestaurante Produto { get; set; }
    public int Quantidade { get; set; }
}

class Cardapio
{
    public List<ProdutoRestaurante> Itens { get; set; } = new List<ProdutoRestaurante>();
}

class Restaurante
{
    public List<Mesa> Mesas { get; set; } = new List<Mesa>();
    public Cardapio Cardapio { get; set; } = new Cardapio();
}

```
