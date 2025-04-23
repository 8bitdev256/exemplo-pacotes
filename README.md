# exemplo-pacotes
DIO.me: Projeto em Eclipse para exemplificar o uso de pacotes na linguagem Java

## Anotações

### Modificadores de Acesso

 - Em Java, quando existe mais de uma classe dentro do mesmo pacote,
 e em uma dessas classes há um método sem um modificador de acesso (private, protected ou public),
 a visibilidade deste método é considerada a visibilidade default, ou seja, este método estará visível
 para todas as outras classes do mesmo pacote em que a classe que este método foi declarado está.
 
 Exemplo:
 
 ```
 package com.meusistema.service
 
 public class Cliente {
	//Método sem modificador de acesso. Portanto, visibilidade default.
	void salvarCliente() {
		
	}
	
	//Método com modificador de acesso private.
	private void adicionarCliente() {
		
	}
 }
 ```
 
 No código acima, a classe Cliente possui o método `salvarCliente`, que ficará visível para a classe Produto abaixo, pois está no mesmo pacote que a classe Cliente (`package com.meusistema.service`):
  
 ```
 package com.meusistema.service
 
 public class Produto {
	//Método com modificador de acesso private.
	private void salvarCliente() {
		
	}
	
	//Método com modificador de acesso private.
	private void adicionarCliente() {
		
	}
 }
 ```
### Getters e Setters

Podem ser criados:
1 - Manualmente;

2 - No Elipse, através das teclas `Ctrl + Barra de Espaço`, digitando parte do nome antes;

3 - `Botão direito do mouse -> Source -> Generate Getters and Setters...`.

```
public class Student {
	private String name;

	public String getName() {
		return name;
	}

	public void setName(String newValue) {
		name = newValue;
	}
}
```

### Construtores

Em Java, funcionam de maneira parecida com C#. Exemplo:

```
public class Pessoa {
	private String nome;
	private String cpf;

	public Pessoa(String nome, String cpf) {
		this.nome = nome;
		this.cpf = cpf;
	}
}
```
### Enums

Funcionam de forma bem diferente do C#. Exemplo:

```
// Criando o enum EstadoBrasileiro para ser usado em toda a aplicação.
public enum EstadoBrasileiro {
	SAO_PAULO ("SP","São Paulo"),
	RIO_JANEIRO ("RJ", "Rio de Janeiro"),
	PIAUI ("PI", "Piauí"),
	MARANHAO ("MA","Maranhão") ;
	
	private String nome;
	private String sigla;
	
	private EstadoBrasileiro(String sigla, String nome) {
		this.sigla = sigla;
		this.nome = nome;
	}
	public String getSigla() {
		return sigla;
	}
	public String getNome() {
		return nome;
	}
	public String getNomeMaiusculo() {
		return nome.toUpperCase();
	}
	
}
```

Exemplo de classe que utiliza o enum criado acima:

```
// qualquer classe do sistema poderá obter os objetos de EstadoBrasileiro
public class SistemaIbge {
	public static void main(String[] args) {
		//imprimindo os estados existentes no enum
		for(EstadoBrasileiro uf: EstadoBrasileiro.values() ) {
		   System.out.println(uf.getSigla() + "-" + uf.getNomeMaiusculo());
		}
		
		//selecionando um estado a partir das opções disponíveis
		EstadoBrasileiro ufSelecionado = EstadoBrasileiro.PIAUI;
		
		System.out.println("O estado selecionado foi: " + ufSelecionado.getNome());
	}
}
```
