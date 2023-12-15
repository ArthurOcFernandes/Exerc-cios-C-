1. Modelar um Pet Shop com classes como Pet, Dono, Consulta e médico.

R:

```c#
public class Pet
{
    public string Nome { get; set; }
    public int Idade { get; set; }
    public string Especie { get; set; }

    public Pet(string nome, int idade, string especie)
    {
        Nome = nome;
        Idade = idade;
        Especie = especie;
    }
}


public class Dono
{
    public string Nome { get; set; }
    public string Contato { get; set; }

    public Dono(string nome, string contato)
    {
        Nome = nome;
        Contato = contato;
    }
}

public class Medico
{
    public string Nome { get; set; }
    public string Especialidade { get; set; }

    public Medico(string nome, string especialidade)
    {
        Nome = nome;
        Especialidade = especialidade;
    }
}

public class Consulta
{
    public Pet Animal { get; set; }
    public Dono DonoAnimal { get; set; }
    public Medico Veterinario { get; set; }
    public string DataConsulta { get; set; }

    public Consulta(Pet animal, Dono dono, Medico veterinario, string dataConsulta)
    {
        Animal = animal;
        DonoAnimal = dono;
        Veterinario = veterinario;
        DataConsulta = dataConsulta;
    }
}

```

2. Modelar o funcionamento de uma oficina automobilistica.

R:

```c#

public class Veiculo
{
    public string Marca { get; set; }
    public string Modelo { get; set; }
    public int Ano { get; set; }
    public string Placa { get; set; }

    public Veiculo(string marca, string modelo, int ano, string placa)
    {
        Marca = marca;
        Modelo = modelo;
        Ano = ano;
        Placa = placa;
    }
}

public class Cliente
{
    public string Nome { get; set; }
    public string Contato { get; set; }

    public Cliente(string nome, string contato)
    {
        Nome = nome;
        Contato = contato;
    }
}


public class Mecanico
{
    public string Nome { get; set; }
    public string Especialidade { get; set; }

    public Mecanico(string nome, string especialidade)
    {
        Nome = nome;
        Especialidade = especialidade;
    }
}


public class Oficina
{
    private List<Veiculo> veiculosNaOficina;

    public Oficina()
    {
        veiculosNaOficina = new List<Veiculo>();
    }

    public void AgendarServico(Veiculo veiculo, Cliente cliente, Mecanico mecanico, string dataAgendamento)
    {
        veiculosNaOficina.Add(veiculo);

        // Lógica para agendar o serviço (pode ser expandida conforme necessário)
        Console.WriteLine($"Serviço agendado para {veiculo.Placa} em {dataAgendamento} com o mecânico {mecanico.Nome}.");
    }

    public void RealizarServico(Veiculo veiculo, Mecanico mecanico)
    {
        if (veiculosNaOficina.Contains(veiculo))
        {
           
            Console.WriteLine($"Serviço realizado em {veiculo.Placa} pelo mecânico {mecanico.Nome}.");
            veiculosNaOficina.Remove(veiculo);
        }
        else
        {
            Console.WriteLine($"O veículo {veiculo.Placa} não está na oficina para realizar o serviço.");
        }
    }
}

```

3. Criar um programa `Program.cs` e simular o funcionamento do programa.

R:

```c#
class Program
{
    static void Main()
    {
        // Criar instâncias de Veiculo, Cliente, Mecanico e Oficina
        Veiculo meuCarro = new Veiculo("Chevrolet", "Cruze", 2020, "ABC1234");
        Cliente cliente = new Cliente("Carlos", "987654321");
        Mecanico mecanico = new Mecanico("Mário", "Mecânica Geral");
        Oficina oficina = new Oficina();

        // Agendar e realizar um serviço na oficina
        oficina.AgendarServico(meuCarro, cliente, mecanico, "2023-12-18");
        oficina.RealizarServico(meuCarro, mecanico);
    }
}
```


4. Escrever um programa que funcione como uma calculadora, que pode realizar as 4 operações básicas, além de calcular raiz quadrada e potências. O usuario deve entrar com dois números e um simbolo que represente a operação a ser feita. 

R:

```c#
public class Calculadora
{
    public static double Calcular(double numero1, double numero2, char operacao)
    {
        double resultado = 0;

        switch (operacao)
        {
            case '+':
                resultado = Somar(numero1, numero2);
                break;
            case '-':
                resultado = Subtrair(numero1, numero2);
                break;
            case '*':
                resultado = Multiplicar(numero1, numero2);
                break;
            case '/':
                resultado = Dividir(numero1, numero2);
                break;
            case '^':
                resultado = Potencia(numero1, numero2);
                break;
            case 'r':
                resultado = RaizQuadrada(numero1);
                break;
            default:
                Console.WriteLine("Operação inválida.");
                break;
        }

        return resultado;
    }

    private static double Somar(double a, double b)
    {
        return a + b;
    }

    private static double Subtrair(double a, double b)
    {
        return a - b;
    }

    private static double Multiplicar(double a, double b)
    {
        return a * b;
    }

    private static double Dividir(double a, double b)
    {
        if (b != 0)
            return a / b;
        else
        {
            Console.WriteLine("Erro: Divisão por zero.");
            return 0;
        }
    }

    private static double Potencia(double a, double b)
    {
        return Math.Pow(a, b);
    }

    private static double RaizQuadrada(double a)
    {
        return Math.Sqrt(a);
    }
}

```