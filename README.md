# Garatuja do Leandro

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

class Quadrilatero {
  lado1: number;
  lado2: number;

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

const q1 = new Quadrilatero();
q1.lado1 = 5;
q1.lado2 = 10;

const q2 = new Quadrilatero();
q2.lado1 = 7;
q2.lado2 = 7;

console.log(q1.calcularArea());
console.log(q1.eQuadrado());

console.log(q2.calcularArea());
console.log(q2.eQuadrado()); 

Nesse exemplo, os objetos q1 e q2 pertencem à mesma classe, mas possuem estados diferentes. Isso evidencia que cada objeto é um processo único.

## Método Construtor:

O construtor é o método que roda automaticamente quando você cria um objeto. Ele serve para já definir os valores iniciais daquele objeto no momento em que ele nasce.

Exemplo:

class Pessoa {
  nome: string;
  idade: number;

  constructor(paramNome: string, paramIdade: number) {
    this.nome = paramNome;
    this.idade = paramIdade;
  }
}

const pessoa1 = new Pessoa("Alice", 30);
console.log(pessoa1.nome);
console.log(pessoa1.idade);

No exemplo quando você escreve new Pessoa("Alice", 30), o constructor dispara sozinho e já configura o objeto com os valores passados. Ele é mais prático porque ao invés de você chamar a classe e definir os valores em determinada variável, como no exemplo da classe e objeto, onde teve que puxar a variável específica da classe e definir o valor dela por fora, no constructor o valor é definido dentro classe ficando mais organizado e automático.

## Herança:

Herança é quando uma classe filha herda as características e ações de uma classe pai. Você escreve o que é comum uma vez na classe pai, e as filhas aproveitam tudo isso automaticamente.

Exemplo:

class Quadrado extends Quadrilatero {
  constructor(paramLado: number) {
    super(paramLado, paramLado);
  }

  eQuadrado(): boolean {
    return true;
  }
}

A subclasse Quadrado herda atributos e métodos de Quadrilatero, mas redefine comportamento específico quando necessário.

## Encapsulamento: 

O encapsulamento protege o estado interno da classe, controlando acesso por modificadores (public, private, protected).


#### Public: Acessível de qualquer lugar. Acesso é dentro e fora da classe.

#### Private: Acessível apenas na classe. Acesso apenas dentro da classe.

#### Protected: Acessível na classe e em subclasses. Acesso em classe e subclasses.

Exemplo de Encapsulamento:

class Quadrilatero {
  private lado1: number;
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

Com private, o TypeScript impede acesso externo direto e reforça consistência do objeto.

## Getters e Setters:


Getters e setters permitem leitura e escrita controladas de atributos privados.

#### Getter retorna valor.

####S etter altera valor com validação.

Exemplo:

class Quadrilatero {
  private lado1: number;
  private lado2: number;

  constructor(paramLado1: number, paramLado2: number) {
    this.setLado1(paramLado1);
    this.setLado2(paramLado2);
  }

  getLado1(): number {
    return this.lado1;
  }

  getLado2(): number {
    return this.lado2;
  }

  setLado1(novoLado1: number): void {
    if (novoLado1 <= 0) throw new Error("lado1 deve ser maior que zero.");
    this.lado1 = novoLado1;
  }

  setLado2(novoLado2: number): void {
    if (novoLado2 <= 0) throw new Error("lado2 deve ser maior que zero.");
    this.lado2 = novoLado2;
  }

  calcularArea(): number {
    return this.lado1 * this.lado2;
  }
}

## Métodos e atributos estáticos:

### Atributo estático: 
É um atributo que pertence à classe, não ao objeto. Ou seja, todos os objetos compartilham o mesmo valor, se um mudar, muda para todos.

### Método:
O método é uma função que  fica dentro de uma classe e pertence ao objeto.

Exemplo:

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
