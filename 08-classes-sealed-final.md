# 🛡️ Controle de Herança: `final`, `sealed`, `non-sealed` (Java 17+)

Este capítulo apresenta técnicas para controlar o uso e extensão das classes em Java, usando os modificadores `final`, `sealed` e `non-sealed`.

---

## ✅ O que é `final`?

Uma classe marcada como `final` **não pode ser estendida**.
O modificador `final` é usado para **impedir modificações ou heranças**, 
dependendo do contexto.

```java
public final class Utilidades {
    public static void limparDados() { ... }
}
```
Nenhuma classe pode fazer extends Utilidades. Isso garante segurança total.

| Aplicação       | Efeito                                               |
|-----------------|------------------------------------------------------|
| Em variáveis    | Não pode ser alterada após inicialização             |
| Em métodos      | Não pode ser sobrescrito por subclasses              |
| Em classes      | Não pode ser estendida por nenhuma outra classe      |

## 🔐 Método final:

```java
public class Conta {
    public final void encerrar() {
        System.out.println("Encerrada");
    }
}

```
## ❌ Tentativa de sobrescrever:
```java
public class ContaEspecial extends Conta {
    @Override
    public void encerrar() {} // ❌ Erro: método é final!
}
```
## ⛔ Classe final:
```java
public final class Util {
    public static void limpar() { ... }
}
```
## sealed: permite herança seletiva (Java 17+)

Classes sealed só podem ser estendidas por classes explicitamente permitidas.
```java
public sealed class Veiculo permits Carro, Moto {
    public void mover() {
        System.out.println("Veículo em movimento");
    }
}
```
Herança é limitada às classes listadas no permits

Evita que classes desconhecidas se aproveitem da lógica base

## Subclasses obrigam declaração

| Modificador   | O que faz                                                            | Quem pode estender?                       |
|---------------|----------------------------------------------------------------------|-------------------------------------------|
| `final`       | Impede completamente que a classe seja estendida                    | ❌ Ninguém                                 |
| `sealed`      | Permite extensão **apenas** por classes definidas com `permits`     | ✅ Apenas classes autorizadas              |
| `non-sealed`  | Reabre a herança dentro de uma hierarquia selada 

Uma classe que herda de uma sealed precisa se identificar:

## 🔓 non-sealed — reabre herança numa hierarquia selada

```java
public non-sealed class Moto extends Veiculo {
    // Pode ser estendida livremente
}
```
📌 Usado quando:

Quer permitir expansão futura

A classe herda de sealed, mas quer quebrar a restrição

## Exemplo completo

```java
public sealed class Forma permits Circulo, Retangulo {
    public abstract double calcularArea();
}

public final class Circulo extends Forma {
    @Override
    public double calcularArea() {
        return 3.14 * 2 * 2;
    }
}

public non-sealed class Retangulo extends Forma {
    @Override
    public double calcularArea() {
        return 4 * 5;
    }
}

public class Quadrado extends Retangulo {
    // Herança permitida, pois Retangulo é non-sealed
}

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

## 🤓 Comparando com a vida real
| Modificador   | Quando aplicar                                 |
|---------------|------------------------------------------------|
| `final`       | Documento bloqueado:ninguém pode editar        |
| `sealed`      | Clube privado: só quem tá na lista pode entrar |
| `non-sealed`  | Porta aberta: qualquer um pode entrar          |

 
## 🧪 Mini desafio
Crie uma classe Veiculo como sealed, que pode ser estendida por Carro e Moto. Depois, defina Carro como final e Moto como non-sealed.

---

## 🧪 🚀 Exercício desafiador: “Controle de Frota”

**Objetivo:** Criar uma hierarquia de veículos controlada usando `final`, `sealed` e `non-sealed`.
---

### 🎯 Regras do exercício

1. Crie a classe **`Veiculo`** como `sealed`.
2. Permita que apenas **`Carro`** e **`Moto`** herdem `Veiculo`.
3. Faça `Carro` ser `final` — ninguém deve conseguir estendê-lo.
4. Faça `Moto` ser `non-sealed` — poderá ter subclasses.
5. Crie a classe `Scooter` que herda `Moto`.
6. Adicione método `mover()` em `Veiculo` e sobrescreva em `Scooter`.

---

### 💡 Dica de estrutura esperada

```java
public sealed class Veiculo permits Carro, Moto {
    public void mover() {
        System.out.println("Veículo em movimento");
    }
}

public final class Carro extends Veiculo {
    // Não pode ser estendido
}

public non-sealed class Moto extends Veiculo {
    // Pode ser estendida
}

public class Scooter extends Moto {
    @Override
    public void mover() {
        System.out.println("Scooter deslizando...");
    }
}
```
✅ Desafio adicional
Crie variáveis final para placa e chassi nos veículos

Implemente métodos final como verificarStatus() que não podem ser sobrescritos