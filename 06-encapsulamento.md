# 🔐 Encapsulamento e Modificadores de Acesso em Java

---

## ✅ O que é encapsulamento?

Encapsulamento é o princípio que consiste em **ocultar os detalhes internos de uma classe** e **proteger seus dados** de acessos indevidos. Ele ajuda a garantir que o estado de um objeto só seja alterado de formas controladas e seguras.

---

## 🔍 Benefícios

- Evita que atributos sejam acessados ou modificados diretamente
- Protege regras internas da classe
- Facilita manutenção e validações
- Garante consistência dos dados

---

## 🔧 Modificadores de acesso

| Modificador | Visível para...                     | Aplicável a           |
|-------------|--------------------------------------|------------------------|
| `public`    | Todas as classes                     | Classes, métodos, atributos |
| `private`   | Somente dentro da própria classe     | Métodos, atributos          |
| `protected` | Mesma classe, subclasses e pacote    | Métodos, atributos          |
| *(sem nada)*| Somente dentro do mesmo pacote       | Classes, métodos, atributos |


---
## 🧱 Tipos de classes e seus modificadores

### ✅ 1. Classes públicas (public)

```java
public class Pessoa { ... }

```
Visíveis de qualquer lugar do projeto — inclusive de outros pacotes.

Usadas principalmente em classes que são ponto de entrada (main), ou que vão ser reutilizadas por outras partes do sistema.

📌 Regra especial: Se você tiver uma classe public, o nome do arquivo Java deve ser igual ao nome da classe.

### 🔒 2. Classes com modificador padrão (package-private)
```java
class Endereco { ... }

```
Visíveis somente dentro do mesmo pacote.

Não se coloca nenhum modificador: nem public, nem private.

Muito útil para classes de suporte, utilitárias ou internas.

### 🚫 3. Classes private ou protected?

Só são permitidas em classes aninhadas (classes dentro de outras).

Uma classe de nível superior nunca pode ser private ou protected.

Exemplo válido com classe interna:

```java
public class Pessoa {
    private class Documento {
        // Só acessível dentro de Pessoa
    }
}

```
### Uso de protected em herança

```java 
public class ItemBiblioteca {
    protected String titulo;
    protected boolean emprestado;

    public void emprestar() { emprestado = true; }
}

public class Livro extends ItemBiblioteca {
    public void exibirTitulo() {
        System.out.println(titulo); // funciona graças ao protected
    }
}

```

### Classe interna privada

```java
public class Usuario {
    private class Credenciais {
        String senha;
        String email;
    }
}

```
A classe Credenciais só existe dentro de Usuario, protegendo informações sensíveis.

## 💡 Recomendações

Use private como padrão em atributos.

Exponha dados com getters/setters validados.

Use protected para atributos que subclasses devem acessar.

Evite public em atributos ou classes internas — privilegie encapsulamento.

## 🤔 Quando usar public então?

## 🧪 Exemplo sem encapsulamento

```java
public class Conta {
    public double saldo;
}

Conta c = new Conta();
c.saldo = -500; // ❌ saldo negativo não deveria ser permitido
```

## 🧪 Exemplo Com encapsulamento + validação
```java
public class Conta {
    private double saldo;

    public void depositar(double valor) {
        if (valor > 0) {
            saldo += valor;
        }
    }

    public void sacar(double valor) {
        if (valor <= saldo) {
            saldo -= valor;
        }
    }

    public double getSaldo() {
        return saldo;
    }
}
```
Aqui:

saldo virou private

Só pode ser alterado por métodos que fazem validações

O método getSaldo() é um getter para acesso externo

## 📘 Getters e Setters
Chamamos de "getter" e "setter" os métodos usados para ler e alterar atributos privados:
```java
public class Pessoa {
    private String nome;

    public String getNome() {
        return nome;
    }

    public void setNome(String novoNome) {
        nome = novoNome;
    }
}
```
## Dica: 
No IntelliJ, você pode gerar automaticamente esses métodos com Alt + Insert → Getter and Setter.

## 🧠 Boas práticas

Nunca deixe atributos sensíveis como public

Valide dados nos métodos set antes de aplicar mudanças

Use private como padrão; exponha só o necessário

## 🧪 Mini desafio 1

Crie uma classe Produto com os atributos nome, preco e quantidade, todos privados. Implemente métodos para alterar e exibir os dados, validando que o preço e a quantidade nunca sejam negativos.

## 🧪 Mini desafio 2

Crie uma classe Veiculo com os atributos marca, ano e velocidade. Todos devem ser privados, e métodos públicos devem permitir acelerar e reduzir a velocidade com limites. Adicione uma subclasse Carro que consegue acessar a marca por meio de um atributo protected.