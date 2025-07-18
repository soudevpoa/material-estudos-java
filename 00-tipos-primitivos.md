# 🔹 Tipos Primitivos em Java

Em Java, os **tipos primitivos** são os tipos de dados mais básicos. Eles não são objetos, e por isso são mais rápidos e leves. Servem para representar **valores simples** como números, caracteres e valores lógicos.

---

## 📋 Lista dos tipos primitivos

| Tipo       | Descrição                             | Exemplo           | Tamanho |
|------------|----------------------------------------|-------------------|---------|
| `byte`     | Número inteiro pequeno                 | `byte idade = 20;`         | 8 bits |
| `short`    | Número inteiro de alcance médio        | `short ano = 2024;`        | 16 bits |
| `int`      | Número inteiro padrão                  | `int contador = 1000;`     | 32 bits |
| `long`     | Número inteiro longo                   | `long populacao = 1_000_000L;` | 64 bits |
| `float`    | Número decimal de precisão simples      | `float pi = 3.14f;`        | 32 bits |
| `double`   | Número decimal de precisão dupla        | `double salario = 9500.75;`| 64 bits |
| `char`     | Um único caractere Unicode              | `char letra = 'A';`        | 16 bits |
| `boolean`  | Valor lógico (`true` ou `false`)        | `boolean ativo = true;`    | 1 bit  |

---

## 🔍 Observações importantes

- `int` é o mais usado para números inteiros.
- `double` é o padrão para números decimais — mais preciso que `float`.
- `boolean` é usado em estruturas condicionais (`if`, `while`, etc).
- `char` representa apenas **um caractere** — não serve para strings!

---

## 🧠 Curiosidade: wrapper classes

Cada tipo primitivo tem uma versão em objeto chamada **wrapper class**:

| Primitivo | Wrapper (objeto) |
|-----------|------------------|
| `int`     | `Integer`        |
| `double`  | `Double`         |
| `boolean` | `Boolean`        |

> As wrappers permitem usar métodos e trabalhar com coleções que não aceitam tipos primitivos.

---

## 📌 Dica prática

Sempre que possível, use tipos primitivos pra ganhar performance — especialmente em operações matemáticas e estruturas simples.

---

## ✅ Exercício sugerido

```java
public class TiposPrimitivos {
    public static void main(String[] args) {
        int idade = 28;
        double peso = 72.5;
        boolean inscrito = true;
        char inicial = 'J';

        System.out.println("Idade: " + idade);
        System.out.println("Peso: " + peso);
        System.out.println("Inscrito: " + inscrito);
        System.out.println("Inicial do nome: " + inicial);
    }
}
```