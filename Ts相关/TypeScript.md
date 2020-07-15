# 1. Start

__tsconfig.json__ 配置文件

```json
{
  "compilerOptions": {
    "target": "es5",                            // 指定 ECMAScript 目标版本: 'ES5'
    "module": "commonjs",                       // 指定使用模块:'commonjs','amd','system','umd'or'es2015'
    "moduleResolution": "node",                 // 选择模块解析策略
    "experimentalDecorators": true,             // 启用实验性的ES装饰器
    "allowSyntheticDefaultImports": true,       // 允许从没有设置默认导出的模块中默认导入。
    "sourceMap": true,                          // 把 ts 文件编译成 js 文件的时候，同时生成对应的 map 文件
    "strict": true,                             // 启用所有严格类型检查选项
    "noImplicitAny": true,                      // 在表达式和声明上有隐含的 any类型时报错
    "alwaysStrict": true,                       // 以严格模式检查模块，并在每个文件里加入'use strict'
    "declaration": true,                        // 生成相应的.d.ts文件
    "removeComments": true,                     // 删除编译后的所有的注释
    "noImplicitReturns": true,                  // 不是函数的所有返回路径都有返回值时报错
    "importHelpers": true,                      // 从 tslib 导入辅助工具函数
    "lib": ["es6", "dom"],                      // 指定要包含在编译中的库文件
    "typeRoots": ["node_modules/@types"],
    "outDir": "./dist",
    "rootDir": "./src"
  },
  "include": [                                  // 需要编译的ts文件一个*表示文件匹配**表示忽略文件的深度问题
    "./src/**/*.ts"
  ],
  "exclude": [
    "node_modules",
    "dist",
    "**/*.test.ts",
  ]
}
```



# 2. 基础内容

## 2.1 Typescript 的原始类型

TypeScript的原始类型包括: boolean、number、string、void、undefined、null、symbol、bigint。

### 布尔类型

我们用 `boolean` 来表示布尔类型，注意开头是小写的，如果你在Typescript文件中写成 `Boolean` 那代表是 JavaScript 中的布尔对象，这是新手常犯的错误。

```typescript
const isLoading: boolean = false
```

### 数字

JavaScript中的二进制、十进制、十六进制等数都可以用 `number` 类型表示。

```typescript
const decLiteral: number = 6
const hexLiteral: number = 0xf00d
const binaryLiteral: number = 0b1010
const octalLiteral: number = 0o744
```

### 字符串

```typescript
const book: string = '深入浅出 Typescript'
```

### 空值

表示没有任何类型，当一个函数没有返回值时，你通常会见到其返回值类型是 void：

```typescript
function warnUser(): void {
    alert("This is my warning message");
}
```

实际上只有`null`和`undefined`可以赋给`void`:

```typescript
const a: void = undefined
```

### Null 和 Undefined

TypeScript 里，undefined 和 null 两者各自有自己的类型分别叫做 undefined 和 null，和void相似，它们的本身的类型用处不是很大：

```typescript
let a: undefined = undefined
let b: null = null
```

默认情况下 null 和 undefined 是所有类型的子类型。

但是在正式项目中一般都是开启 `--strictNullChecks` 检测的，即 null 和 undefined 只能赋值给 any 和它们各自（例外是 undefined 是也可以分配给void）。

### Symbol

**注意**：我们在使用 `Symbol` 的时候，必须在`tsconfig.json`添加 `es6` 的编译辅助库：

```json
{
		"lib": ["es6", "dom"]   // 指定要包含在编译中的库文件
}
```

Symbol 是在ES2015之后成为新的原始类型,它通过 `Symbol` 构造函数创建:

```
const sym1 = Symbol('key1');
const sym2 = Symbol('key2');
```

而且 Symbol 的值是唯一不变的：

```
Symbol('key1') === Symbol('key1') // false
```

### BigInt

**注意**：我们在使用 `BigInt` 的时候，必须添加 `ESNext` 的编译辅助库

```json
{
		"lib": ["es6", "dom", "ESNext"]   // 指定要包含在编译中的库文件
}
```

- 在 JavaScript 中采用双精度浮点数,这导致精度有限，比如 `Number.MAX_SAFE_INTEGER` 给出了可以安全递增的最大可能整数，即`2**53-1`

- 我们需要用 `BigInt(number)` 把 Number 转化为 `BigInt`,同时如果类型是 `BigInt` ,那么数字后面需要加 `n`

```typescript
const num1: BigInt = BigInt(123)
const num2: BigInt = 123n

declare let foo: number;
declare let bar: bigint;

foo = bar; // error: Type 'bigint' is not assignable to type 'number'.
bar = foo; // error: Type 'number' is not assignable to type 'bigint'.
```

### 总结

总结一下 TypeScript 中的原始类型：

- 布尔类型：`boolean`
- 数字类型：`number`
- 字符串类型：`string`
- 空值：`void`
- Null 和 Undefined：`null` 和 `undefined`
- Symbol 类型：`symbol`
- BigInt 大数整数类型：`bigint`



## 2.2 Typescript 中其他常见类型

















# 3. 基础实战























# 4. 进阶内容





















# 5. 定制TS























# 6. 工程化

























# 7. End



















