# 📦 `record` em Java — Classes de Dados Imutáveis

---

## ✅ O que é um `record`?

Um `record` é uma forma compacta de declarar classes que **armazenam dados**. Ele automaticamente cria:
- Construtor
- Getters
- `equals()`, `hashCode()` e `toString()`

Tudo isso com uma única linha de código!

---

## 🔍 Sintaxe básica

```java
public record Pessoa(String nome, int idade) { }
```
Esse record equivale a uma classe que teria:

Atributos nome e idade

Construtor Pessoa(String nome, int idade)

Métodos nome(), idade(), toString(), etc.

Imutabilidade — os atributos não podem ser alterados

## 🧪 Exemplo de uso

```java
Pessoa p = new Pessoa("Jonathan", 28);
System.out.println(p.nome()); // "Jonathan"
System.out.println(p);        // Pessoa[nome=Jonathan, idade=28]
```

## 💡 Vantagens do record

| Benefício        | Descrição                                     |
|------------------|-----------------------------------------------|
| `sintaxe limpa`  | Elimina repetição                             |
| `imutável`       | Os atributos são final e não podem mudar      |
| `ideal para DTO` | Perfeito para transportar dados entre camadas |

## ✏️ Adicionando lógica interna
Você pode adicionar métodos, validações e inicialização personalizada:
```java
public record Produto(String nome, double preco) {
    public Produto {
        if (preco < 0) {
            throw new IllegalArgumentException("Preço não pode ser negativo!");
        }
    }

    public String descricao() {
        return nome + " por R$" + preco;
    }
}
```
## 🚫 Limitações do record
Não pode herdar de outra classe

Sempre final — não pode ser estendido

Não pode ter campos mutáveis

Não é indicado pra lógica complexa — apenas pra representação de dados

## 🤓 Comparando com classe tradicional

```java
// Classe tradicional
public class Livro {
    private final String titulo;
    private final String autor;

    public Livro(String titulo, String autor) {
        this.titulo = titulo;
        this.autor = autor;
    }

    public String getTitulo() { return titulo; }
    public String getAutor() { return autor; }

    // + equals(), hashCode(), toString()
}

// Record equivalente
public record Livro(String titulo, String autor) { }

```
Menos código. Mesma funcionalidade.

## 🧪 Mini desafio
Crie um record chamado Endereco com os campos rua, cidade, estado e cep. Adicione um método chamado formatado() que retorna o endereço completo como string.