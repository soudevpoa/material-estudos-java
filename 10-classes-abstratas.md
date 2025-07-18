# 🧱 Classes Abstratas em Java — Moldes para subclasses

---

## ✅ O que é uma classe abstrata?

Uma **classe abstrata** é uma classe que **não pode ser instanciada diretamente**. Ela serve como **modelo base** para outras classes e pode conter:

- Métodos concretos (com implementação)
- Métodos abstratos (sem corpo, a serem implementados nas subclasses)

---

## 🛠️ Sintaxe básica

```java
public abstract class Animal {
    public abstract void emitirSom(); // método abstrato

    public void respirar() {          // método concreto
        System.out.println("Respirando...");
    }
}
```
## 🔍 Regras importantes

| Regras                                   | Explicação                               |
|------------------------------------------|------------------------------------------|
| Não pode ser instanciada diretamente     | `new Animal()` ❌                        |
| Pode ter métodos com ou sem corpo        | Com ou sem `{}`                          |
| Subclasses devem implementar métodos     | Obrigatório usar `@Override`             |
| Pode ter atributos, construtores, lógica | É uma classe normal — mas abstrata       |

## 🧪 Exemplo prático

```java
public abstract class Forma {
    public abstract double calcularArea();
}

public class Retangulo extends Forma {
    private double largura;
    private double altura;

    public Retangulo(double largura, double altura) {
        this.largura = largura;
        this.altura = altura;
    }

    @Override
    public double calcularArea() {
        return largura * altura;
    }
}

public class Main {
    public static void main(String[] args) {
        Forma f = new Retangulo(5, 3);
        System.out.println(f.calcularArea()); // Saída: 15.0
    }
}

```
## 🤔 Por que usar classes abstratas?
| Motivo                       | Benefício                                       |
|------------------------------|--------------------------------------------------|
| Modelar comportamento genérico | Reutilização por diversas subclasses            |
| Forçar implementação          | Garante que cada filho implemente seus métodos |
| Combinar com polimorfismo     | Chamar métodos abstratos dinamicamente          |
| Criar base para hierarquia    | Facilita manutenção e extensão de código        |

## 🚫 Diferença entre abstract e interface
| Item               | `abstract` class                | `interface`                      |
|--------------------|---------------------------------|----------------------------------|
| Pode ter atributos | ✅ Sim                          | ✅ Sim (desde Java 8+)          |
| Métodos com corpo  | ✅ Sim                          | ✅ Sim (`default` ou `static`)  |
| Herança múltipla   | ❌ Não (só uma superclasse)     | ✅ Sim (múltiplas interfaces)   |
| Instanciável       | ❌ Não                          | ❌ Não                           |

## 🧪 Mini desafio
Crie uma classe abstrata chamada Funcionario, com o método abstrato calcularSalario(). 

Depois, crie duas subclasses: Desenvolvedor e Estagiario, cada uma com regras diferentes para o cálculo do salário.
