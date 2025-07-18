## 🔹 Classes e Objetos em Java

### ✅ O que é uma classe?
Uma classe é um modelo que define os atributos (dados) e métodos (ações) de um tipo de objeto.
Ela representa um conceito abstrato no seu código.
```java
public class Pessoa {
    String nome;
    int idade;

    public void apresentar() {
        System.out.println("Olá, sou " + nome + " e tenho " + idade + " anos.");
    }
}
```
### ✅ O que é um objeto?

Um objeto é uma instância da classe — ou seja, um produto construído a partir do molde.

```bash
Pessoa pessoa1 = new Pessoa();
pessoa1.nome = "Jonathan";
pessoa1.idade = 28;
pessoa1.apresentar();
```
### 🎯 Aprendizado aplicado:

Modelagem de entidades reais

Uso de new para instanciar objetos