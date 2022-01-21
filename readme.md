# 📝 Notas Curso Fundamentos de TypeScript

- Clase 1: [El lenguaje de programación TypeScript](#El-lenguaje-de-programación-TypeScript)
- Clase 2: [Instalación de herramientas para TypeScript]()
- Clase 3: [Instalación de herramientas en Windows]()
- Clase 4: [Navegación y refactorización](#Navegación-y-refactorización)
- Clase 5: [El compilador de TypeScript](#El-compilador-de-TypeScript)
- Clase 6: [El archivo de configuración de TypeScript](#El-archivo-de-configuración-de-TypeScript)
- Clase 7: [Mi primer proyecto TypeScript](#Mi-primer-proyecto-TypeScript)
- Clase 8: [Tipado en TypeScript](#Tipado-en-TypeScript)
- Clase 9: [Number, Boolean y String](#Number,-Boolean-y-String)
- Clase 10: [Any](#Any)
- Clase 11: [Void y Never](#Void-y-never)
- Clase 12: [Null y Undefined](#Null-y-Undefined)

# El lenguaje de programación TypeScript

### Que es TypeScript

- Es un superconjunto tipado de javascript, que compila a javascript.
- **Lenguaje de programación tipado:** Posee un conjunto de tipos para poder usarlos con las variables, pudiendo personalizarlos o extenderlos.
- **Lenguaje de alto nivel:** Entendible por humanos y posee un alto nivel de abstracción del código máquina.
- **Genera como resultado código JavaScript:** Emite código javascript compatible con browsers y otras herramientas de javascript.
- Código abierto.
- Desarrollo desde cualquier sistema.
- El código puede ejecutarse en cualquier navegador o plataforma que soporte javascript.

### Porque usar TypeScript

- Programación orientada a objetos
- Potenciar tu código JavaScript
- Mayor productividad
- Poderoso sistema de tipos
- Compila a ES5, ES6 y más
- Proyecto muy activo/Open source
- Actualizaciones periódicas
- Comunidad creciente
- Puede prevenir cerca del 15% de bugs
- Puede usar TypeScript para backend**\_\_**

> Links:
>
> - [TypeScript](https://www.typescriptlang.org/)

# Navegación y refactorización

### Typescript en Visual Studio Code

Ejemplo de un proyecto en TypeScript ([REPO](https://github.com/codex-team/editor.js))

El editor Visual Studio Code viene configurado para aprovechar al máximo TypeScript.
Entre las features se encuentran:

- IntelliSense
- Snippets
- JSDocs
- Formateo
- Refactorización
- Arreglos rápidos.

> Links:
>
> - [https://code.visualstudio.com/docs/languages/typescript](https://code.visualstudio.com/docs/languages/typescript)

# El compilador de TypeScript

### Instalación de TypeScript

Con el siguiente comando lo instalaremos de manera global:

```
npm install -g typescript
```

Consultar la versión del compilador de TS:

```
tsc -v
```

Compilar nuestros ficheros .ts

```
tsc your_file.ts
```

Compilar de manera ‘automática’ nuestros ficheros .ts

```
tsc --watch your_file.ts
```

# El archivo de configuración de TypeScript

### Configurar Typescript **tsconfig.json**

- Especifica la raiz de un proyecto TS
- Permite configurar opciones para el compilador

Para crear este archivo en cualquier proyecto:

```
tsc --init
```

El archivo base es este:

```json
{
	"extends": "./config/base"
	"compilerOptions":{
		"target": "es6",
		"module": "commonjs"
		"strict": true,
		"removeComments": true
	},
	"include":[
		"src/**/*.ts"
	],
	"exclude": [
		"node_modules",
		"**/*.test.ts"
	]
}
```

Una vez que este archivo es generado, ejecutamos:

```
tsc // Busa la configuracion dentro del proyecto
tsc --project platzi // Especifica el directorio donde esta la configuracion
tsc file.ts // Omite la configuracion
```

> _**Nota** Extra: El modo estricto de typescript no es el mismo que el modo estricto de ECMASCRIPT, si bien quizás pueden ser un símil pero el strict mode verifica mas allá del modo use strict de javascript ya que es una propiedad solo del proceso de compilación y verificación de typescript la bandera que corresponde dicho setting es --alwaysStrict en la configuración de typescript y renderiza el famoso “use strict”_

.

> Links:
>
> - [Configurando el tsconfig.ts](https://www.typescriptlang.org/tsconfig)

# Mi primer proyecto TypeScript

Si queremos ejecutar archivos de .ts sin transpilar, podemos usar una librería que se llama ts-node

Por ejemplo en el package.json

```
"dev": "ts-node index.ts"
```

O directamente en consola con npx

```
npx ts-node index.ts
```

Su caso de uso común es probar que todo funcione antes de traspilar para ahorrar tiempo, un ejemplo de cuando se quiere monitorear Express usando TS

En el package.json

```
"dev": "nodemon --exec ts-node -- ./server.ts",
```

# Tipado en TypeScript

### Tipado en TypeScript

- **Explicito**: Define una sintaxis para la creación de variables con tipo de dato.

```
nombreVariable: Tipo de dato
```

- **Inferido**: TypeScript tiene la habilidad de deducir el tipo en funcion de un valor.

```
nombreVariable = Tipo de dato
```

### Tipo de datos primitivos

- number
- boolean
- string
- array
- tuple
- enum
- any
- void
- null
- undefined
- never
- object

# Number, Boolean y String

### Tipos de datos

Dentro de los tipos explícitos que maneja TypeScript, tenemos:

1. **Number**: Este tipo de dato incluye valores numéricos, hexadecimales, binarios y octales.

```typescript
// Explícito
let phone: number;
phone = 3315015804;
let hex: number = 0xf00d;
let binary: number = 0b1010;
let octal: number = 0o744;
// Implícito
let phoneNumber = 3315015804;
```

2. **Boolean**: Es el tipo de dato más simple en TypeScript ya que solo acepta dos tipos de valores que son true o false.

```typescript
// Explícito
let isTrue: boolean = true;
// Implícito
let isFalse = false;
```

3. **String**: Es el tipo de dato para trabanar con datos textuales o cadenas, para definir este tipo de dato se puede usar comilla dobles "" o simples ''.

```typescript
// Explícito
let userName: string = "Alejandra";
// Template string
let userInfo: string = `
  User info:
  firstName: ${firstName}
  lastName: ${lastName}
  phone: ${phone}
  isValid: ${isTrue}
`;
// Implícito
let lastName = "Camacho";
```

# Any

### Cuando usar el tipo Any

- Es usado para capturar valores dinámicos
- Los valores pueren cambiar de tipo en el tiempo:
  - APIs externas
  - Librerías de terceros

## Ejemplo Clase:

```typescript
// Tipo explicito
let idUser: any;
idUser = 1; // number
idUser = "1"; // string
console.log("idUser", idUser);

// Tipo Inferido
let otherId;
otherId = 1;
otherId = "1";
// otherId = true;
console.log("otherId", otherId);

let surprise: any = "hello typescript";
// surprise.sayHello(); // Error
const res = surprise.substring(6); // Error
console.log("res", res);
```

# Void y Never

**Tipo Void**: Representa la ausencia de tipo. usado en funciones que no retornan nada. Son funciones que no necesitan de un retorno, por lo que al asignar el tipo void se sobre entiende que estas funciones retornan un undefind o un valor no definido, mas si permiten el uso de este return con este valor, que en el futuro puede ser usado para la terminacion de una funcion de este tipo.

**Tipo Never**: Representa funciones que lanzan excepciones o nunca retornan un valor. En este caso son funciones que nunca retornaran un valor, dentro de TS si intentas retornar un valor en una funcion Never te marcara error, normalmente usada para errores ya que son funciones que no retornan un valor sino que lanzan o arrojan un error o mensaje al ejecutarse, cabe destacar tambien que las variables declaradas como nulas no permiten que se les asigne ningun tipo de dato, caso contrario a los void que permite la asignacion del dato undefind

## Ejemplo Clase:

```typescript
// type void for functions
// Explicit type

function showInfo(user: any): any {
  console.log(`User Info ${user.id} ${user.username} ${user.firstname}`);
  // return 'hola';
}

showInfo({ id: 1, username: "Antúnez Durán", firstname: "Francisco Javier" });

// Inferred type
function showFormattedInfo(user: any) {
  console.log(`User Info,
        id: ${user.id}
        username: ${user.username}
        firstname: ${user.firstname}`);
}

showFormattedInfo({
  id: 1,
  username: "Antúnez Durán",
  firstname: "Francisco Javier",
});

// Type void as variable data type
let unusable: void;
// unusable = null; --> colocar "strict": false en tsconfig.json para poder hacer uso
unusable = undefined;

// Type never
function handleError(code: number, message: string): never {
  // Process your code
  // Generate a message
  throw new Error(`${message}. Code: ${code}`);
}

try {
  console.log("La funcion handleError no devuelve nada bajo esta linea");
  handleError(404, "Not found");
} catch (error) {}

function sumNumbers(limit: number): never {
  let sum = 0;
  while (true) {
    sum++;
  }
  // return sum;
}

sumNumbers(10); // --> Llamada a un bucle infinito no acabaria nunca, typescript no compila, al verlo.
```

# Null y Undefined

Null y Undefined se pueden asumir como subtipos de los otros tipos de datos. Significa que se pueden asignar null y undefied a una variable de tipo string, por ejemplo.

### Opción --strictNullChecks

Solo permite asignar null y undefined a una variable de tipo any o a sus respectivos

Ayua a evitar errores comunes en programación de apps en el ámbito JavaScript

Generará un reporte de los errores que encuentre, hacemos

```
tsc nombreDelArchivo.ts --strictNullChecks
```

## Ejemplo Clase:

```typescript
// Explicita
let nullVariable: null;
nullVariable = null;
// nullVariable = 1; // Error!

let otherVariable = null;
otherVariable = "test";

console.log("nullVariable", nullVariable);
console.log("otherVariable", otherVariable);

// Undefined
let undefinedVariable: undefined = undefined;
// undefinedVariable = 'test'; // Error

let otherUndefined = undefined;
otherUndefined = 1;

console.log("undefinedVariable", undefinedVariable);
console.log("otherUndefined", otherUndefined);

// Null y Undefined: Como subtipos

// --strictNullChecks
let albumName: string;

// albumName = null;
// albumName = undefined;
```
