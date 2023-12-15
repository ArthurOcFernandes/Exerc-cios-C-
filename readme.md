1. Criar uma hierarquia de classes representando formas geométricas, como Quadrado, Círculo e Triângulo. Utilize herança para criar uma classe base chamada FormaGeometrica, que contenha métodos para calcular a área e o perímetro de uma forma.

R:

```c#
abstract class FormaGeometrica
{
    public abstract double CalcularArea();
    public abstract double CalcularPerimetro();
}

class Quadrado : FormaGeometrica
{
    public double Lado { get; set; }

    public override double CalcularArea()
    {
        return Lado * Lado;
    }

    public override double CalcularPerimetro()
    {
        return 4 * Lado;
    }
}

class Circulo : FormaGeometrica
{
    public double Raio { get; set; }

    public override double CalcularArea()
    {
        return Math.PI * Raio * Raio;
    }

    public override double CalcularPerimetro()
    {
        return 2 * Math.PI * Raio;
    }
}

class Triangulo : FormaGeometrica
{
    public double Base { get; set; }
    public double Altura { get; set; }

    public override double CalcularArea()
    {
        return 0.5 * Base * Altura;
    }

    public override double CalcularPerimetro()
    {
        // Considerando um triângulo genérico
        return Base + Altura + Math.Sqrt(Base * Base + Altura * Altura);
    }
}

```

2. Crie uma hierarquia de classes representando funcionários de uma empresa. Utilize herança para criar classes como Gerente, Programador e Analista. Cada classe deve ter propriedades específicas, além das propriedades comuns a todos os funcionários, como Nome e Salário.

R: 

```c#

class Funcionario
{
    public string Nome { get; set; }
    public double Salario { get; set; }
}

class Gerente : Funcionario
{
    public string Setor { get; set; }
}

class Programador : Funcionario
{
    public string LinguagemDeProgramacao { get; set; }
}

class Analista : Funcionario
{
    public string AreaDeAtuacao { get; set; }
}

```

3. Criar uma hierarquia de classes representando contas bancárias, como ContaCorrente e ContaPoupanca. Utilize herança e o conceito de métodos virtuais para implementar um método CalcularSaldo que retorne o saldo atual da conta.

R:

```c#

class ContaBancaria
{
    protected double Saldo { get; set; }

    public virtual void Depositar(double valor)
    {
        Saldo += valor;
    }

    public virtual void Sacar(double valor)
    {
        Saldo -= valor;
    }

    public virtual double CalcularSaldo()
    {
        return Saldo;
    }
}

class ContaCorrente : ContaBancaria
{
    private double TaxaManutencao { get; set; }

    public override void Sacar(double valor)
    {
        base.Sacar(valor + TaxaManutencao);
    }
}

class ContaPoupanca : ContaBancaria
{
    private double TaxaRendimento { get; set; }

    public override double CalcularSaldo()
    {
        return base.CalcularSaldo() * (1 + TaxaRendimento);
    }
}

```

4. Criar uma hierarquia de classes representando animais, como Mamifero, Ave e Peixe. Utilize herança e o conceito de métodos virtuais para implementar um método EmitirSom que represente o som característico de cada tipo de animal.

R:

```c#

class Animal
{
    public virtual string EmitirSom()
    {
        return "Som genérico de animal";
    }
}

class Mamifero : Animal
{
    public override string EmitirSom()
    {
        return "Som de mamífero";
    }
}

class Ave : Animal
{
    public override string EmitirSom()
    {
        return "Som de ave";
    }
}

class Peixe : Animal
{
    public override string EmitirSom()
    {
        return "Som de peixe";
    }
}


```

5. Criar uma hierarquia de classes representando produtos eletrônicos, como Smartphone, Tablet e Laptop. Utilize herança e o conceito de métodos virtuais para implementar um método ExibirInformacoes que retorne informações específicas de cada produto.

R:

```c#

class ProdutoEletronico
{
    public string Modelo { get; set; }
    public double Preco { get; set; }

    public virtual string ExibirInformacoes()
    {
        return $"Modelo: {Modelo}, Preço: {Preco:C}";
    }
}

class Smartphone : ProdutoEletronico
{
    public string SistemaOperacional { get; set; }

    public override string ExibirInformacoes()
    {
        return $"{base.ExibirInformacoes()}, SO: {SistemaOperacional}";
    }
}

class Tablet : ProdutoEletronico
{
    public string TipoTela { get; set; }

    public override string ExibirInformacoes()
    {
        return $"{base.ExibirInformacoes()}, Tela: {TipoTela}";
    }
}

class Laptop : ProdutoEletronico
{
    public string Processador { get; set; }

    public override string ExibirInformacoes()
    {
        return $"{base.ExibirInformacoes()}, Processador: {Processador}";
    }
}


```