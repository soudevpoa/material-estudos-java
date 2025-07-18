# 🔹 Herança em Java

## ✅ O que é herança?
Permite que uma classe herde atributos e métodos de outra.

### Exemplos:

```java
public class Animal {
    public void emitirSom() {
        System.out.println("Som genérico");
    }
}
```
```java

public class Cachorro extends Animal {
    public void abanarRabo() {
        System.out.println("Cachorro feliz!");
    }
}
```
### Reuso em ação

```java
Cachorro c = new Cachorro();
c.emitirSom(); // Herdado de Animal
c.abanarRabo(); // Específico de Cachorro

```