# ⚙️ Construtores em Java

---

## ✅ O que é um construtor?

Um construtor é um método especial de uma classe que é executado **automaticamente** quando um objeto é criado com `new`. Ele serve para **inicializar atributos** e preparar o objeto para uso.

---

## 🛠️ Sintaxe básica

```java
public class Pessoa {
    String nome;
    int idade;

    // Construtor com parâmetros
    public Pessoa(String nome, int idade) {
        this.nome = nome;
        this.idade = idade;
    }
}

```
O construtor tem o mesmo nome da classe e não tem tipo de retorno (nem void).
### 🧪 Criando objeto da classe acima com o construtor

```java
Pessoa p = new Pessoa("Jonathan", 28);
```
O objeto p já nasce com os atributos preenchidos.

## 🔁 Sobrecarga de construtores
É possível criar vários construtores com diferentes assinaturas:

```java
public class Produto {
    String nome;
    double preco;

    // Construtor padrão
    public Produto() {
        this.nome = "Genérico";
        this.preco = 0.0;
    }

    // Construtor com parâmetros
    public Produto(String nome, double preco) {
        this.nome = nome;
        this.preco = preco;
    }
}

```
## 🧠 Por que usar sobrecarga?

Permite flexibilidade na criação dos objetos

Permite valores padrão ou opcionais

Evita duplicação de código

## 🔂 Chamando um construtor dentro de outro
```java 
public Produto(String nome) {
    this(nome, 0.0); // Chama o outro construtor com preco = 0.0
}
```
O this() chama outro construtor da mesma classe.

## ✅ Boas práticas

Sempre defina ao menos um construtor personalizado quando sua classe tem atributos obrigatórios

Use sobrecarga para oferecer múltiplas formas de instanciar o objeto

Use validação dentro do construtor se necessário

## 🧪 Mini desafio

Crie uma classe Usuario com os atributos nome, email e ativo. 

Implemente dois construtores: um que define todos os atributos, e outro que só define o nome e o email, deixando ativo como true por padrão.