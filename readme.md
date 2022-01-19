# 📝 Notas Curso Fundamentos de TypeScript

- Clase 1: [El lenguaje de programación TypeScript](#El-lenguaje-de-programación-TypeScript)
- Clase 2: [Instalación de herramientas para TypeScript]()
- Clase 3: [Instalación de herramientas en Windows]()
- Clase 4: [Navegación y refactorización](#Navegación-y-refactorización)
- Clase 5: [El compilador de TypeScript](#El-compilador-de-TypeScript)
- Clase 6: [El archivo de configuración de TypeScript](#El-archivo-de-configuración-de-TypeScript)
- Clase 7: [Mi primer proyecto TypeScript](#Mi-primer-proyecto-TypeScript)

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
