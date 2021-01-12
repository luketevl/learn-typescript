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
  - unknown (parecido com o any), diferenca que pode ser definido depois.

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

# Generics
- Funcao pode ser definida seu tipo no momento que eh chamado.
- Simbolos representao algo de algum **tipo**
 - **S** => State
 - **T** => Type
 - **K** => Key
 - **V** => Value
 - **E** => Element
- Limitar os tipos deve usar **extends**
- Colocar um tipo padrao deve usar o **=**
 ```js
 function useState<S extends number | string = string>() {
  let state: S
 }
 
 useState<String>('a');
 ```

# Mutations
## Readonly
- **Readonly**
```js
 type Todo = {
  title?: string;
  completed?: boolean
 }
 
 const todo: Readonly<Todo> = {
  title: "a",
  completed: true
 }
 function updateTodo(todo: Todo, fieldsToUpdate: Todo) {
  return { ...todo, ...fieldsToUpdate }
 }
 
 const todo2: Todo = updateTodo(todo, { completed: false });
 
```
## Partial
- Deixa propriedades opcionais em um determinado momento.
 - **Partial**
```js
 type Todo = {
  title: string;
  completed: boolean
 }
 
 const todo: Readonly<Todo> = {
  title: "a",
  completed: true
 }
 function updateTodo(todo: Todo, fieldsToUpdate: Partial<Todo>) {
  return { ...todo, ...fieldsToUpdate }
 }
 
 
 const todo2: Todo = updateTodo(todo, { completed: false });
```

## Pick
- Pega apenas as propriedades que forem escolhidas.
 - **Pick**
```js
 type Todo = {
  title: string;
  completed: boolean
 }
 
 type TodoPreview = Pick<Todo, "title" | "description">  
```


## Omit
- Esconde apenas as propriedades que forem escolhidas.
 - **Pick**
```js
 type Todo = {
  title: string;
  completed: boolean
 }
 
 type TodoPreview = Omit<Todo, "description">  
```



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
- **NAO** tem como definir **tuplas** na **interface**
- **Interface** permite **multiplas** declaracoes e une eles.
 
```js
interface JQuery {
 a: string;
}
interface JQuery {
 b: string;
}
const $: JQuery = {
 a: "bla",
 b: "foo"
}
```
