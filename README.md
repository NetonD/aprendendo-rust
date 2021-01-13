# Anotações sobre o básico da programaçao em rust
#TODO: acentuar as palavras.
## Variáveis e constantes.

Em rust uma `variável` pode ser declarada usando a palavra chave `let` seguida de letras e numeros
como em qualquer linguagem c-like. Por padrão as `variáveis` não são realmente variaveis, ou seja,
seu valor nao pode ser modificado explicitamente. Isso ocorre para evitar problemas de concorrência e 
assim diminuir bugs.

> Declaração de uma variável:

```rust
fn main() {
	let minha_variavel = 10;
	
	minha_variavel = 11; //NÃO É PERMITIDO AQUI!!
}
```

Para permitir uma reatribuição de valor a aquela variável basta usar a palavra chave `mut` na declaração
da variável.

> Variável realmente variável

```rust
fn main(){
	let mut outra_variavel = 20;
	outra_variavel = 10; //AGORA SIM, AQUI É PERMITIDO
}
```

Além de `let` e `let mut` existe também as constantes que são declaradas usando a palavra chave `const`. Uma constante
deve ser atribuida através de uma expressão avaliada em tempo de compilação, ou seja, não é possivel atribuir um valor 
de uma variável a uma constante. Constantes também seguem um padrão de nomenclatura: LETRAS_MAIUSCULA separadas por `_`.

> Exemplo de constante:

```rust
fn main(){
	const MINHA_CONSTANTE = 3.14;
} 
```

## Escopo, blocos etc

### Bloco
Um bloco pode ser definido dentro de um par de parenteses e por si só representar um escopo.

```rust
{
	BLOCO 1
	{
		BLOCO 2
		{
			BLOCO 3
		}
	}
	{
		BLOCO 2.1
	} 
} 
```

O escopo de um bloco só é visivel de baixo pra cima, ou seja, o `BLOCO 1` nao tem acesso às variáveis do `BLOCO 2`, `BLOCO 3` nem do `BLOCO 2.1`. Porém, o `BLOCO 3` tem acesso às variavés do `BLOCO 2` e do `BLOCO 1`. Além disso os blocos não tem acesso aos
escopos dos blocos vizinhos, ex. o `BLOCO 2` nao tem acesso ao `BLOCO 2.1`.

> Um bloco é um escopo e permite `shadowing`.

### Shadowing

Dada essa hierarquia de blocos o shadowing é quando uma variavel de um escopo mais profunto tem a mesma definiçao ( ou nome) que uma variável ja declarada, nesse caso a variavel usada será a do escopo mais profundo e nada acontecerá com a variavel previamente declarada.
Também ocorre o shadowing quando se redeclara uma variável, seja com `let`, ou `let mut`, a delcaraçao anterior vai ser ignorada.

```rust
{
	let b = 15;
	let mut b = 20; //SHADOWING da variavel b;
	let a = 10;
	{
		let a = 20; //SHADOWING da variavel a
		print!("{}", a); // vai mostrar 20 
	}
}

```
