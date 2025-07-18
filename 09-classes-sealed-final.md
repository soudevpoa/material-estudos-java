# 🛡️ Classes `sealed`, `non-sealed` e `final` em Java

Esses modificadores foram criados para **limitar ou controlar a herança entre classes**, especialmente em projetos grandes que precisam evitar extensões indesejadas ou imprevisíveis.

---

## 🔹 `final`: proíbe herança

Uma classe marcada como `final` **não pode ser estendida**.

```java
public final class Utilidades {
    public static void limparDados() { ... }
}
```
Nenhuma classe pode fazer extends Utilidades. Isso garante segurança total.

## sealed: permite herança seletiva (Java 17+)

Classes sealed só podem ser estendidas por classes explicitamente permitidas.
```java
public sealed class Forma permits Circulo, Retangulo {
    public abstract double calcularArea();
}

```
Somente Circulo e Retangulo podem estender Forma. Outras classes serão recusadas na compilação.

## Subclasses obrigam declaração

| Tipo de extensão       | Palavra-chave usada |
|------------------------|---------------------|
| Permitir novas extensões | `non-sealed`       |
| Não permitir extensão    | `final`            |
| Continuar selando        | `sealed`           |


Uma classe que herda de uma sealed precisa se identificar:

## Exemplo completo

```java
public sealed class Forma permits Circulo, Retangulo { ... }

public final class Circulo extends Forma { ... }

public non-sealed class Retangulo extends Forma { ... }

```
Circulo: não pode ser herdado mais

Retangulo: pode ser herdado por outras classes

Ambas seguem as permissões definidas pela classe Forma

## ✅ Quando usar cada modificador?

| Modificador   | Quando aplicar                                                |
|---------------|---------------------------------------------------------------|
| `final`       | Quando quer proibir herança completamente                    |
| `sealed`      | Quando quer limitar herança a um grupo específico de classes |
| `non-sealed`  | Quando quer liberar herança em uma hierarquia selada         |

## 📌 Requisitos para sealed
Introduzido no Java 17

Todas as classes permitidas devem estar no mesmo módulo ou pacote

Cada classe permitida deve declarar se é sealed, non-sealed ou final

## 🧪 Mini desafio
Crie uma classe Veiculo como sealed, que pode ser estendida por Carro e Moto. Depois, defina Carro como final e Moto como non-sealed.
