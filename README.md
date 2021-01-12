# Links
- https://www.typescriptlang.org/
- https://www.youtube.com/watch?v=mRixno_uE2o&list=PLlAbYrWSYTiPanrzauGa7vMuve7_vnXG_&ab_channel=WillianJustenCursos

# Sobre
> Superset do JavaScript. Possuindo novas features(tipagem estatica).

# Vantagens
- Pode funcionar como um documentacao
- Evitar retornos inesperados
```js
const sum = (a,b) => a + b
// success
sum(1, 2) // 3
// bad
sum('1', '2') // 12 
``` 
# Desvantagens
 - Precisa ser compilado
 - Aprendizagem inicial e boas praticas
 - Erros nem sem claros e longos
 
 # Exemplos
 ```js
 
 ```
 
 # Configuracao
 - Cria arquivo de configuracao inicial
 ```shell
 tsc -- init
 ```
 
 # Tipos
 - Primitivos
  - boolean
    - true | false
  - string
    - 'foo', "foo", `foo`
  - number
    - xff0, 10, 99.99, 00001
  - array
    - number[], string[], Array<number>
- Novos
  - tuple
    - [number, string]
  - enum
    - enum Colors { white = '#FFF', black = '#000'  }
  - any
    - let coisa: any; coisa = 1; coisa = 'oi' 
  - void (vazio)
   - function logger(): void { console.log(3) }
  - null | undefined
  - never (nunca vai retornar)
    - throw new Error("error") 
    - function logger(): never { throw new Error("error")  }
  - object (qualquer coisa que nao eh tipo primitivo)
    - let cart: object

# Type Inference
> Nao precisa dizer o tipo da variavel, ao passar o valor o typescript ja infere o seu tipo.
```js
 let x = '3'
 window.addEventListener("click", e => {
  console.log(e.target);
 })
 ```
# Type Aliases e Union
- Define dois tipos para uma variavel
  - **union** = Tem que usar o pipe **|**
    
```js
 function logDetails(uid: number | string, item: string){
  console.log(`Product ${uid}`)
  }
  logDetails(123, 'Sapato'); 
 ```
- Reutilizar tipos
- Criar valores padroes
  - **aliases**
```js
 type Uid = number | string
 type Platform = "Windows" | "Linux" | "Mac OS"
 function renderPlataform(plataform: Plataform){
  return plataform;
 }
 // bad
 renderPlataform("android");
 
 // success
 renderPlataform("Mac OS"); 
```
### Type Aliases com Intersection
- Deve usar o **&**
```js
 type AccountInfo = {
  id: number;
  name: string;
  email?: string
 }
 type CharInfo = {
  nickname: string;
  level: number
}

// Intersection
type PlayerInfo = AccountInfo & CharInfo
```

# Classes

# Observacoes
- Prametro **opcional**
  - Use o **?**

```js
 type AccountInfo = {
  id: number;
  name: string;
  email?: string
 }
```
