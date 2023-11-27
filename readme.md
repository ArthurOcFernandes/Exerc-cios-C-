1. Criar uma classe que representa uma conta bancária, com um número indicador, titular, saldo e senha.

```
class Conta{
    public string titular;
    public int idConta;
    public float saldo;
    public int senha;
}
```

2. Criar um objeto do tipo Conta, adicionar dados e mostrar as informações **titular** e **saldo** no console, utilizando interpolação de strings.

```
Conta conta = new Conta();
conta.titular = "Gui Lima";
conta.id = 1;
conta.saldo = 20.00;
conta.senha = 1234;

Console.WriteLine("INFORMAÇÕES DA CONTA:");
Console.WriteLine($"Titular: {conta.titular}"); 
Console.WriteLine($"Saldo atual: {conta.saldo}");
```

3. Desenvolver um método da classe Conta que exibe suas informações.

```
public void exibirInformacoes(){
    Console.WriteLine("INFORMAÇÕES DA CONTA:");
    Console.WriteLine($"Titular: {this.titular}"); 
    Console.WriteLine($"Saldo atual: {this.saldo}");
}
```

4. Desenvolver uma classe que modele um carro, e que contenha os métodos **acelerar**, **frear** e **buzinar**

```
class Carro
{
    public string fabricante;
    public string modelo;
    public int ano;
    public int quantidadePortas;
    public int velocidade = 0;

    public void exibirInformacoes(){
        Console.WriteLine($"Informações do carro: {this.fabricante} {this.modelo}, {this.quantidadePortas} portas, {this.ano}");
    }
    
    public void acelerar(){
        Console.WriteLine("Acelerando...");
        if(velocidade < 100){
            velocidade = velocidade + 5;
        }
    }

    public void frear(){
        Console.WriteLine("Freando...");
        if(velocidade > 0){
            velocidade = velocidade - 5;
        }
    }

    public void buzinar(){
        Console.WriteLine("Bi Bi");
    }
}

```

