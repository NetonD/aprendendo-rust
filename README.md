# Anotações sobre o básico da programaçao em rust

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
