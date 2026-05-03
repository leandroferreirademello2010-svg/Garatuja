# Garatuja do Leandro

##Diferência entre JavaScript, TypeScript e Java

###JavaScript (JS)
JavaScript é uma linguagem dinâmica e interpretada, criada originalmente para rodar nos navegadores. Hoje também executa no servidor via Node.js. Suas principais características são:

Tipagem fraca e dinâmica — variáveis não têm tipo fixo e podem mudar em tempo de execução
Interpretada — o código é executado diretamente, sem compilação prévia
Multiparadigma — suporta programação funcional, orientada a objetos e procedural
Ecossistema enorme — npm com milhões de pacotes disponíveis

É ideal para desenvolvimento web front-end, scripts rápidos e aplicações onde a flexibilidade é mais importante que a rigidez estrutural.

###TypeScript (TS)
TypeScript é um superset do JavaScript desenvolvido pela Microsoft. Todo código JS válido é também TS válido, mas o TS adiciona uma camada fundamental: a tipagem estática opcional. Suas características:

Tipagem estática — você declara os tipos das variáveis, parâmetros e retornos de função
Compilado para JavaScript — o código TS é transpilado para JS antes de ser executado
Detecção de erros em tempo de desenvolvimento — o compilador aponta problemas antes de rodar o código
Melhor suporte a IDEs — autocompletar e refatoração muito mais precisos

É a escolha dominante em projetos JavaScript de médio a grande porte, pois traz segurança sem abandonar o ecossistema JS.

###Java
Java é uma linguagem totalmente diferente das anteriores — robusta, fortemente tipada e compilada para bytecode que roda na JVM (Java Virtual Machine). Suas características:

Tipagem forte e estática — obrigatória, sem opção
Orientada a objetos — tudo gira em torno de classes e objetos
Compilada para bytecode — o código é compilado e depois interpretado pela JVM, permitindo portabilidade entre sistemas operacionais
Verbosa e estruturada — exige mais código, mas oferece mais controle e previsibilidade
Muito usada em back-end corporativo, aplicações Android, sistemas bancários e de grande escala


## O que é POO?
POO é uma forma de programar inspirada no mundo real.Em vez de escrever uma lista de instruções soltas, você organiza o código em "coisas" — cada coisa tem suas próprias características e ações.
Um Carro, por exemplo, tem características (cor, marca, velocidade) e ações (acelerar, frear). No código, você cria essa "receita" uma vez e pode fabricar quantos carros quiser a partir dela.
A grande vantagem é que o código fica organizado, reutilizável e fácil de manter — se precisar mudar algo no Carro, muda em um só lugar e todos os objetos se beneficiam.

## Classe e Objeto:

### Classe é um molde. Objeto é o que você cria a partir dele.

Pense em uma classe como a planta de uma casa: ela define quantos quartos, portas e janelas existem. O objeto é a casa construída a partir dessa planta, você pode construir várias casas diferentes usando a mesma planta.

#### Atributo:
O atributo é o valor do objeto/classe. Cada objeto tem os mesmos atributos, mas com valores diferentes;

Exemplo de objeto e classe:

```typescript
// Classe que representa um quadrilátero com dois lados
class Quadrilatero {
  lado1: number;
  lado2: number;

  // Retorna a área do quadrilátero (lado1 × lado2)
  calcularArea(): number {
    return this.lado1 * this.lado2;
  }

  // Retorna o perímetro do quadrilátero (soma de todos os lados)
  calcularPerimetro(): number {
    return 2 * (this.lado1 + this.lado2);
  }

  // Verifica se o quadrilátero é um quadrado (lado1 igual ao lado2)
  eQuadrado(): boolean {
    return this.lado1 === this.lado2;
  }
}

// Cria o objeto q1 e define seus lados como 5 e 10 (retângulo)
const q1 = new Quadrilatero();
q1.lado1 = 5;
q1.lado2 = 10;

// Cria o objeto q2 e define seus lados como 7 e 7 (quadrado)
const q2 = new Quadrilatero();
q2.lado1 = 7;
q2.lado2 = 7;

console.log(q1.calcularArea());  // Exibe a área do quadrado
console.log(q1.eQuadrado());     // Exibe false (5 ≠ 10)
console.log(q2.calcularArea());  // Exibe 49  (7 × 7)
console.log(q2.eQuadrado());     // Exibe true  (7 = 7)
```
Nesse exemplo, os objetos q1 e q2 pertencem à mesma classe, mas possuem estados diferentes. Isso evidencia que cada objeto é um processo único.

## Método Construtor:

O construtor é o método que roda automaticamente quando você cria um objeto. Ele serve para já definir os valores iniciais daquele objeto no momento em que ele nasce.

Exemplo:
```typescript
class Pessoa {
  nome: string;
  idade: number;

// Inicializa os atributos do objeto no momento em que ele é criado.
  constructor(paramNome: string, paramIdade: number) {
    this.nome = paramNome;
    this.idade = paramIdade;
  }
}

const pessoa1 = new Pessoa("Alice", 30);
console.log(pessoa1.nome);
console.log(pessoa1.idade);

```

## Herança:

Herança é quando uma classe filha herda as características e ações de uma classe pai. Você escreve o que é comum uma vez na classe pai, e as filhas aproveitam tudo isso automaticamente.

Exemplo:
```typescript
class Quadrado extends Quadrilatero {
  constructor(paramLado: number) {
    super(paramLado, paramLado);
  }

  eQuadrado(): boolean {
    return true;
  }
}


```
A subclasse Quadrado herda atributos e métodos de Quadrilatero, mas redefine comportamento específico quando necessário.

## Encapsulamento: 

O encapsulamento protege o estado interno da classe, controlando acesso por modificadores (public, private, protected).


### Public: Acessível de qualquer lugar.

### Private: Acessível apenas na classe.

### Protected: Acessível na classe e em subclasses.

Exemplo de Encapsulamento:
```typescript
class Quadrilatero {
 // "private" impede que lado1 seja acessado ou modificado fora desta classe
  private lado1: number;
 // "private" impede que lado1 seja acessado ou modificado fora desta classe
  private lado2: number;

  constructor(paramLado1: number, paramLado2: number) {
    this.lado1 = paramLado1;
    this.lado2 = paramLado2;
  }

  calcularArea(): number {
    return this.lado1 * this.lado2;
  }

  calcularPerimetro(): number {
    return 2 * (this.lado1 + this.lado2);
  }

  eQuadrado(): boolean {
    return this.lado1 === this.lado2;
  }
}


```
Com private, o TypeScript impede acesso externo direto e reforça consistência do objeto.

## Getters e Setters:


Getters e setters permitem leitura e escrita controladas de atributos privados.

### Getter retorna valor.

### Setter altera valor com validação.

Exemplo:
```typescript
class Quadrilatero {
  private lado1: number;
  private lado2: number;

  constructor(paramLado1: number, paramLado2: number) {
    this.setLado1(paramLado1);
    this.setLado2(paramLado2);
  }

// Retorna o valor atual do lado1
  getLado1(): number {
    return this.lado1;
  }

// Retorna o valor atual do lado2
  getLado2(): number {
    return this.lado2;
  }

// Define um novo valor para lado1, garantindo que seja maior que zero
  setLado1(novoLado1: number): void {
    if (novoLado1 <= 0) throw new Error("lado1 deve ser maior que zero.");
    this.lado1 = novoLado1;
  }

// Define um novo valor para lado2, garantindo que seja maior que zero
  setLado2(novoLado2: number): void {
    if (novoLado2 <= 0) throw new Error("lado2 deve ser maior que zero.");
    this.lado2 = novoLado2;
  }

  calcularArea(): number {
    return this.lado1 * this.lado2;
  }
}

```
## Métodos e atributos estáticos:

### Atributo estático: 
É um atributo que pertence à classe, não ao objeto. Ou seja, todos os objetos compartilham o mesmo valor, se um mudar, muda para todos.

### Método:
O método é uma função que  fica dentro de uma classe e pertence ao objeto.

Exemplo:
```typescript
class Quadrado {
  private _lado: number;

  constructor(paramLado: number) {
    this.lado = paramLado;
  }

  get lado(): number {
    return this._lado;
  }

  set lado(novoLado: number) {
    if (novoLado <= 0) throw new Error("lado deve ser maior que zero.");
    this._lado = novoLado;
  }

  get area(): number {
    return this.lado * this.lado;
  }

  static maiorArea(q1: Quadrado, q2: Quadrado, ..qn: Quadrado[]): Quadrado {
    let maior = q1;
    const quadrados = [q1, q2, ...n];
    for (const q of quadrados) {
      if (q.area > maior.area) {
        maior = q;
      }
    }
    return maior;
  }
}
