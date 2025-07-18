
---

## 📘 `05-polimorfismo.md`

## ✅ O que é polimorfismo?

Capacidade de um objeto assumir diferentes formas ou comportamentos.

### Exemplo com sobrescrita:

```java
public class Gato extends Animal {
    @Override
    public void emitirSom() {
        System.out.println("Miau");
    }
}

Animal a = new Gato();
a.emitirSom(); // Executa "Miau" graças ao polimorfismo

```
### ✅ Quando usar?

Ao tratar objetos diferentes de forma uniforme

Para implementar interfaces flexíveis
