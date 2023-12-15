1. Criar uma interface chamada IForma que declare métodos para calcular a área e o perímetro de uma forma geométrica. Implemente esta interface em duas classes: Circulo e Retangulo.

R:

```c#

public interface IForma
{
    double CalcularArea();
    double CalcularPerimetro();
}

public class Circulo : IForma
{
    public double Raio { get; set; }

    public double CalcularArea()
    {
        return Math.PI * Math.Pow(Raio, 2);
    }

    public double CalcularPerimetro()
    {
        return 2 * Math.PI * Raio;
    }
}

public class Retangulo : IForma
{
    public double Comprimento { get; set; }
    public double Largura { get; set; }

    public double CalcularArea()
    {
        return Comprimento * Largura;
    }

    public double CalcularPerimetro()
    {
        return 2 * (Comprimento + Largura);
    }
}


```

2. Criar duas interfaces adicionais, IPilotavel e IVoavel. Implemente essas interfaces na classe Veiculo.

R: 

```c#
public interface IPilotavel
{
    void Pilotar();
}

public interface IVoavel
{
    void Voar();
}

public class Veiculo : IPilotavel, IVoavel
{
    public void Pilotar()
    {
        Console.WriteLine("Veículo está pilotando");
    }

    public void Voar()
    {
        Console.WriteLine("Veículo está voando");
    }
}

```

3. Criar uma interface chamada IPagavel com um método CalcularPagamento. Implemente essa interface em duas classes, Produto e Servico. O método CalcularPagamento deve retornar o valor total a ser pago, levando em consideração a quantidade para produtos e a taxa horária para serviços.

R:

```c#

public interface IPagavel
{
    decimal CalcularPagamento();
}

public class Produto : IPagavel
{
    public string Nome { get; set; }
    public decimal PrecoUnitario { get; set; }
    public int Quantidade { get; set; }

    public decimal CalcularPagamento()
    {
        return PrecoUnitario * Quantidade;
    }
}

public class Servico : IPagavel
{
    public string Nome { get; set; }
    public decimal TaxaHoraria { get; set; }
    public int HorasTrabalhadas { get; set; }

    public decimal CalcularPagamento()
    {
        return TaxaHoraria * HorasTrabalhadas;
    }
}


```

4. Criar uma interface chamada INotificavel com um método EnviarNotificacao. Implemente essa interface em duas classes, Email e SMS. O método EnviarNotificacao deve exibir mensagens diferentes para cada tipo de notificação.

```c#
public interface INotificavel
{
    void EnviarNotificacao();
}

public class Email : INotificavel
{
    public string EnderecoEmail { get; set; }

    public void EnviarNotificacao()
    {
        Console.WriteLine($"Enviando e-mail para {EnderecoEmail}: Notificação importante!");
    }
}

public class SMS : INotificavel
{
    public string NumeroTelefone { get; set; }

    public void EnviarNotificacao()
    {
        Console.WriteLine($"Enviando SMS para {NumeroTelefone}: Notificação importante!");
    }
}

```

5. Criar uma interface chamada IArmazenavel com métodos Salvar e Recuperar. Implemente essa interface em duas classes, Arquivo e BancoDeDados. Os métodos Salvar e Recuperar devem exibir mensagens simulando a ação de salvar e recuperar dados.

R: 

```c#
public interface IArmazenavel
{
    void Salvar();
    void Recuperar();
}

public class Arquivo : IArmazenavel
{
    public string NomeArquivo { get; set; }

    public void Salvar()
    {
        Console.WriteLine($"Salvando dados no arquivo {NomeArquivo}.");
    }

    public void Recuperar()
    {
        Console.WriteLine($"Recuperando dados do arquivo {NomeArquivo}.");
    }
}

public class BancoDeDados : IArmazenavel
{
    public string NomeBanco { get; set; }

    public void Salvar()
    {
        Console.WriteLine($"Salvando dados no banco de dados {NomeBanco}.");
    }

    public void Recuperar()
    {
        Console.WriteLine($"Recuperando dados do banco de dados {NomeBanco}.");
    }
}
```