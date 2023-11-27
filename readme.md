1. Escrever uma função que leia dois números de ponto flutuante a e b do teclado e exibir no console o resultado de suas quatro operações básicas (adição, subtração, divisão e multiplicação), utilizando interpolação de strings.

R:

```
void ExibirQuatroOperacoes(){

    float a = float(Console.Read());
    float b = float(Console.Read());

    float soma = a + b;
    float subtracao = a - b;
    float divisao = a / b;
    float multiplicacao = a * b;

    Console.WriteLine($"a + b = {soma}")
    Console.WriteLine($"a - b = {subtracao}")
    Console.WriteLine($"a / b = {divisao}")
    Console.WriteLine($"a * b = {multiplicacao}")
}
```

2. Criar uma lista de bandas vazia e adicionar suas bandas prediletas em seguida.

```
List<string> bandas = new List<String>();

bandas.add("The Beatles");
bandas.add("Pink Floyd");
bandas.add("U2");
bandas.add("Ira!");

```

3. Utilizar a estrutura 'for' para mostrar todas as suas bandas preferidas, listadas na lista do exercício anterior, no console.

```

for(int i = 0; i < bandas.Count; i++){
    Console.WriteLine(bandas[i]);
}

```

4. Criar um programa que calcula a soma de todos os elementos inteiros em uma lista.

```

List<int> numeros = new List<int> { 1, 2, 3, 4, 5 };
int soma = 0;

foreach (int numero in numeros)
{
    soma += numero;
}

Console.WriteLine($"A soma dos elementos da lista é: {soma}");

```

5. Criar um programa que calcula a média dos elementos de ponto flutuante em uma lista.


```
List<double> numeros = new List<double> { 1.5, 2.5, 3.5, 4.5, 5.5 };
double soma = 0;

foreach (double numero in numeros)
{
    soma += numero;
}

double media = soma / numeros.Count;
Console.WriteLine($"A média dos elementos da lista é: {media}");
```

6. Desenvolver um programa que exibe a tabuada de um número fornecido pelo usuário.


```
Console.Write("Digite um número para ver a tabuada: ");
int numero = int.Parse(Console.ReadLine());

Console.WriteLine($"Tabuada do {numero}:");

for (int i = 1; i <= 10; i++)
{
    int resultado = numero * i;
    Console.WriteLine($"{numero} x {i} = {resultado}");
}

```

7. Desenvolver uma calculadora simples que realiza as quatro operações básicas, a partir de dois números fornecidos pelo usuário, e a operação que deve ser feita.

```

Console.Write("Digite o primeiro número: ");
double numero1 = double.Parse(Console.ReadLine());

Console.Write("Digite o segundo número: ");
double numero2 = double.Parse(Console.ReadLine());

Console.Write("Digite a operação (+, -, *, /): ");
char operacao = char.Parse(Console.ReadLine());

double resultado = 0;

switch (operacao)
{
    case '+':
        resultado = numero1 + numero2;
        break;
    case '-':
        resultado = numero1 - numero2;
        break;
    case '*':
        resultado = numero1 * numero2;
        break;
    case '/':
        resultado = numero1 / numero2;
        break;
    default:
        Console.WriteLine("Operação inválida.");
        return;
}

Console.WriteLine($"Resultado da operação: {resultado}");
```