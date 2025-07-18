
## 📘 `02-metodos.md`

## ✅ O que são métodos?
São ações que um objeto pode executar. Podem ter parâmetros e retornar valores.

### Exemplo com retorno:

```java
public double calcularIMC(double peso, double altura) {
    return peso / (altura * altura);
}
```
###  Exemplo sem retorno:
```java
public void fazerAniversario() {
idade++;
}

```
### Exemplo com retorno e parâmetros
```java

public double calcularIMC(double peso, double altura) {
    return peso / (altura * altura);
}
```
### 🎯 Dicas:

Use nomes verbais: abrirConta(), sacarValor()

Métodos podem acessar atributos internos da classe