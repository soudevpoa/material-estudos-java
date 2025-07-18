# 🧩 Tipos Especiais de Classes em Java

Este capítulo apresenta os principais tipos de classes utilizadas em Java para controlar estrutura, herança e comportamento. Também inclui os modificadores mais comuns que afetam visibilidade e instanciamento.

---

## ✅ Visão geral dos tipos de classe

```markdown
| Tipo de classe      | Palavra-chave        | Propósito principal                                 |
|---------------------|----------------------|-----------------------------------------------------|
| Padrão (concreta)   | *(sem modificador)*  | Classe comum; pode ser instanciada e herdada        |
| Abstrata            | `abstract`           | Modelo base; exige implementação pelas subclasses   |
| Final               | `final`              | Classe selada; não pode ser estendida               |
| Selada              | `sealed`             | Herança limitada a classes autorizadas              |
| Não-selada          | `non-sealed`         | Herança liberada após selamento                     |
| Registro            | `record`             | Classe imutável de dados com sintaxe compacta       |
| Enumeração          | `enum`               | Conjunto fixo de constantes                         |
| Interna/Aninhada    | `static`, `private`  | Classe definida dentro de outra classe              |
| Genérica            | `<T>`                | Classe flexível que trabalha com tipos variados     |
| Anônima             | *(sem nome)*         | Classe inline usada para interface ou extensão leve |
```
## 🔧 Modificadores aplicáveis às classes

Os modificadores alteram o comportamento, acesso e restrições de herança de uma classe.

| Modificador     | Aplicável a classe? | Descrição                                          |
|-----------------|----------------------|----------------------------------------------------|
| `public`        | ✅                   | Visível em todo o projeto                          |
| `private`       | ❌ (exceto internas) | Visível apenas dentro da classe que a contém       |
| `protected`     | ❌ (exceto internas) | Visível no mesmo pacote ou subclasses              |
| *(sem nada)*    | ✅                   | Visível somente dentro do mesmo pacote             |
| `abstract`      | ✅                   | Classe que serve como base; não pode ser instanciada|
| `final`         | ✅                   | Bloqueia herança; não pode ser estendida           |
| `sealed`        | ✅ (Java 17+)        | Herança limitada a classes especificadas           |
| `non-sealed`    | ✅                   | Reabre herança dentro de hierarquias seladas       |
| `static`        | ✅ (internas)        | Classe que pertence à classe externa, não a instâncias |

## 🧠 Exemplos por tipo
🔹 Classe abstrata
```java
public abstract class Animal {
    public abstract void emitirSom();

    public void respirar() {
        System.out.println("Respirando...");
    }
}

```
🔹 Classe final
```java
public final class Utils {
    public static void limparCache() { ... }
}
```
🔹 Classe sealed com subclasses específicas
```java
public sealed class Veiculo permits Carro, Moto {
    public void mover() {
        System.out.println("Veículo em movimento");
    }
}
```
🔹 Subclasse non-sealed (herança liberada)

```java
public non-sealed class Moto extends Veiculo {
    public void acelerar() { ... }
}

public class Scooter extends Moto {
    // Herdando de Moto porque é non-sealed
}
```
🔹 Record — classe de dados imutável
```java
public record Produto(String nome, double preco) { }
```
🔹 Enum — conjunto fixo de valores
```java
public enum Prioridade {
    BAIXA, MEDIA, ALTA
}
```
🔹 Classe interna private
```java
public class Usuario {
    private class Credencial {
        String email;
        String senha;
    }
}
```
## 📘 Boas práticas com modificadores de classe

| Cenário                         | Modificador recomendado     |
|----------------------------------|-----------------------------|
| Reutilização genérica            | `abstract`                 |
| Segurança ou lógica sensível     | `final`, `private`         |
| Organização de herança seletiva | `sealed` + `permits`       |
| Flexibilidade e extensão livre  | `non-sealed`               |
| Transporte de dados              | `record`                   |
| Grupo fixo de valores            | `enum`                     |
| Compartilhamento interno         | `private static` (nested)  |

## 🧪 Desafio de aplicação

Monte uma estrutura com os seguintes tipos de classe:

abstract class Forma, com método calcularArea()

sealed class Geometrica extends Forma, autorizando Quadrado e Circulo

final class Quadrado, com lado

non-sealed class Circulo, que permite herança

record class HistoricoForma(String nome, double area) para guardar logs

enum TipoForma { QUADRADO, CIRCULO }