<p align="center">
  <img src="logo.svg" width="200px" align="center" alt="Zod logo" />
  <h1 align="center">Zod</h1>
  <p align="center">利用静态类型推断进行 TypeScript 优先的模式验证
  <br/>
  <a href="https://zod.dev">https://zod.dev</a>
</p>
<br/>
<p align="center">
<a href="https://github.com/colinhacks/zod/actions?query=branch%3Amaster"><img src="https://github.com/colinhacks/zod/actions/workflows/test.yml/badge.svg?event=push&branch=master" alt="Zod CI status" /></a>
<a href="https://twitter.com/colinhacks" rel="nofollow"><img src="https://img.shields.io/badge/created%20by-@colinhacks-4BBAAB.svg" alt="Created by Colin McDonnell"></a>
<a href="https://opensource.org/licenses/MIT" rel="nofollow"><img src="https://img.shields.io/github/license/colinhacks/zod" alt="License"></a>
<a href="https://www.npmjs.com/package/zod" rel="nofollow"><img src="https://img.shields.io/npm/dw/zod.svg" alt="npm"></a>
<a href="https://www.npmjs.com/package/zod" rel="nofollow"><img src="https://img.shields.io/github/stars/colinhacks/zod" alt="stars"></a>
<a href="https://discord.gg/KaSRdyX2vc" rel="nofollow"><img src="https://img.shields.io/discord/893487829802418277?label=Discord&logo=discord&logoColor=white" alt="discord server"></a>
</p>

<div align="center">
  <a href="https://zod.dev">文档</a>
  <span>&nbsp;&nbsp;•&nbsp;&nbsp;</span>
  <a href="https://discord.gg/RcG33DQJdf">Discord</a>
  <span>&nbsp;&nbsp;•&nbsp;&nbsp;</span>
  <a href="https://www.npmjs.com/package/zod">NPM</a>
  <span>&nbsp;&nbsp;•&nbsp;&nbsp;</span>
  <a href="https://github.com/colinhacks/zod/issues/new">讨论</a>
  <span>&nbsp;&nbsp;•&nbsp;&nbsp;</span>
  <a href="https://twitter.com/colinhacks">@colinhacks</a>
  <span>&nbsp;&nbsp;•&nbsp;&nbsp;</span>
  <a href="https://trpc.io">tRPC</a>
  <br />
</div>

<br/>
<br/>

# 內容

- [什么是 Zod](#什么是-zod)
- [生态体系](#生态体系)
- [安装](#安装)
- [基本用法](#基本用法)
- [原始类型](#原始类型)
- [原始类型的强制转换](#原始类型的强制转换)
- [字面量](#字面量)
- [字符串](#字符串)
  - [ISO 日期](#iso-日期)
  - [IP 地址](#ip-地址)
- [Numbers](#numbers)
- [Objects](#objects)
  - [.shape](#shape)
  - [.extend](#extend)
  - [.merge](#merge)
  - [.pick/.omit](#pickomit)
  - [.partial](#partial)
  - [.deepPartial](#deepPartial)
  - [.passthrough](#passthrough)
  - [.strict](#strict)
  - [.strip](#strip)
  - [.catchall](#catchall)
- [Records](#records)
- [Maps](#maps)
- [Sets](#sets)
- [Arrays](#arrays)
  - [.nonempty](#nonempty)
  - [.min/.max/.length](#minmaxlength)
- [Unions](#unions)
- [Optionals](#optionals)
- [Nullables](#nullables)
- [Enums](#enums)
  - [Zod enums](#zod-enums)
  - [Native enums](#native-enums)
- [Tuples](#tuples)
- [Recursive types](#recursive-types)
  - [JSON type](#json-type)
  - [Cyclical data](#cyclical-objects)
- [Promises](#promises)
- [Instanceof](#instanceof)
- [Function schemas](#function-schemas)
- [基础类方法（ZodType）](#基础类方法（ZodType）)
  - [.parse](#parse)
  - [.parseAsync](#parseasync)
  - [.safeParse](#safeparse)
  - [.safeParseAsync](#safeparseasync)
  - [.refine](#refine)
  - [.superRefine](#superRefine)
  - [.transform](#transform)
  - [.default](#default)
  - [.optional](#optional)
  - [.nullable](#nullable)
  - [.nullish](#nullish)
  - [.array](#array)
  - [.or](#or)
  - [.and](#and)
- [类型推断](#type-inference)
- [Errors](#errors)
- [比较](#comparison)
  - [Joi](#joi)
  - [Yup](#yup)
  - [io-ts](#io-ts)
  - [Runtypes](#runtypes)
- [Changelog](#changelog)

# 什么是 Zod

Zod 是一个 TypeScript 优先的模式声明和验证库。我使用术语“模式”来广义地指任何数据类型，从简单的 string 到复杂的嵌套对象。

Zod 围绕尽可能友好的开发体验而设计。其目的是消除重复的类型声明。使用 Zod，你只需声明 _一次_ 验证器，Zod 就会自动推断出静态 TypeScript 类型。将简单类型组合成复杂的数据结构非常容易。

其他一些重要方面:

- 零依赖
- 适用于 Node.js 和所有现代浏览器
- 小巧: 压缩后仅 8kb
- 不可变: 方法（如 `.optional()`） 返回一个新的实例
- 简洁的、可链式调用的接口
- 函数式方法: [解析，不验证](https://lexi-lambda.github.io/blog/2019/11/05/parse-don-t-validate/)
- 也可用于纯 JavaScript！你不必使用 TypeScript。

## 赞助

我们感谢并鼓励任何级别的赞助。Zod 是由[个人开发者](https://twitter.com/colinhacks)维护的。如果你也是个人开发者，可以考虑[一杯咖啡级别](https://github.com/sponsors/colinhacks)。如果你使用 Zod 建立了一个商业产品，可以考虑[领奖台级别](https://github.com/sponsors/colinhacks)。

### 黄金

<table>
  <tr>
    <td align="center">
      <a href="https://astro.build/">
        <img src="https://avatars.githubusercontent.com/u/44914786?s=200&v=4" width="200px;" alt="Astro" />
      </a>
      <br />
      <b>Astro</b>
      <br />
      <a href="https://astro.build">astro.build</a>
      <br />
      <p width="200px">
        Astro is a new kind of static <br/>
        site builder for the modern web. <br/>
        Powerful developer experience meets <br/>
        lightweight output.</p>
    </td>
    <td align="center">
      <a href="https://glow.app/">
        <img src="https://i.imgur.com/R0R43S2.jpg" width="200px;" alt="" />
      </a>
      <br />
      <b>Glow Wallet</b>
      <br />
      <a href="https://glow.app/">glow.app</a>
      <br />
      <p width="200px">Your new favorite
        <br/>
      Solana wallet.</p>
    </td>
  </tr>
  <tr>
    <td align="center">
      <a href="https://deletype.com/">
        <img src="https://avatars0.githubusercontent.com/u/15068039?s=200&v=4" width="200px;" alt="" />
      </a>
      <br />
      <b>Deletype</b>
      <br />
      <a href="https://deletype.com">deletype.com</a>
    </td>
  </tr>
</table>

### 白银

<table>
  <tr>
    <td align="center">
      <a href="https://snaplet.dev">
        <img src="https://avatars.githubusercontent.com/u/69029941?s=200&v=4" width="150px;" alt="" />
      </a>
      <br />
      <b>Snaplet</b>
      <br />
      <a href="https://snaplet.dev">snaplet.dev</a>
    </td>
     <td align="center">
      <a href="https://marcatopartners.com/">
        <img src="https://avatars.githubusercontent.com/u/84106192?s=200&v=4" width="150px;" alt="Marcato Partners" />
      </a>
      <br />
      <b>Marcato Partners</b>
      <br />
      <a href="https://marcatopartners.com/">marcatopartners.com</a>
    </td>
     <td align="center">
      <a href="https://github.com/macandcheese-spaghetticode">
        <img src="https://avatars.githubusercontent.com/u/76997592?v=4" width="150px;" alt="Trip" />
      </a>
      <br />
      <b>Trip</b>
    </td>
  </tr>
  <tr>
    <td align="center">
      <a href="https://seasoned.cc">
        <img src="https://avatars.githubusercontent.com/u/33913103?s=200&v=4" width="150px;" alt="" />
      </a>
      <br />
      <b>Seasoned Software</b>
      <br />
      <a href="https://seasoned.cc">seasoned.cc</a>
    </td>
    <td align="center">
      <a href="https://seasoned.cc">
        <img src="https://avatars.githubusercontent.com/u/67802063?s=200&v=4" width="150px;" alt="" />
      </a>
      <br />
      <b>Interval</b>
      <br />
      <a href="https://interval.com">interval.com</a>
    </td>
  </tr>
</table>

### 青铜

<table>
  <tr>
    <td align="center">
      <a href="https://twitter.com/flybayer">
        <img src="https://avatars2.githubusercontent.com/u/8813276?s=460&u=4ff8beb9a67b173015c4b426a92d89cab960af1b&v=4" width="100px;" alt=""/>
      </a>
      <br />
      <b>Brandon Bayer</b>
      <br/>
      <a href="https://twitter.com/flybayer">@flybayer</a>,
      <span>creator of <a href="https://blitzjs.com">Blitz.js</a></span>
      <br />
    </td>
    <td align="center">
      <a href="https://github.com/brabeji">
        <img src="https://avatars.githubusercontent.com/u/2237954?v=4" width="100px;" alt=""/>
      </a>
      <br />
      <b>Jiří Brabec</b>
      <br/>
      <a href="https://github.com/brabeji">@brabeji</a>
      <br />
    </td>
     <td align="center">
      <a href="https://twitter.com/alexdotjs">
        <img src="https://avatars.githubusercontent.com/u/459267?v=4" width="100px;" alt="" />
      </a>
      <br />
      <b>Alex Johansson</b>
      <br />
      <a href="https://twitter.com/alexdotjs">@alexdotjs</a>
    </td>
  </tr>
  <tr>
    <td align="center">
      <a href="https://adaptable.io/">
        <img src="https://avatars.githubusercontent.com/u/60378268?s=200&v=4" width="100px;" alt=""/>
      </a>
      <br />
      <b>Adaptable</b>
      <br/>
      <a href="https://adaptable.io/">adaptable.io</a>
      <br />
    </td>
    <td align="center">
      <a href="https://www.avanawallet.com/">
        <img src="https://avatars.githubusercontent.com/u/105452197?s=200&v=4" width="100px;" alt="Avana Wallet logo"/>
      </a>
      <br />
      <b>Avana Wallet</b>
      <br/>
      <a href="https://www.avanawallet.com/">avanawallet.com</a><br/>
      <span>Solana non-custodial wallet</span>
      <br />
    </td>
  </tr>
</table>

_要在这里看到你的名字 + Twitter + 网站，请在[Freelancer](https://github.com/sponsors/colinhacks) 或 [Consultancy](https://github.com/sponsors/colinhacks)赞助 Zod。_

# 生态体系

越来越多的工具建立在 Zod 之上，或原生支持 Zod 了！如果你在 Zod 的基础上建立了一个工具或库，请在 [Twitter](https://twitter.com/colinhacks) 或者 [Discussion](https://github.com/colinhacks/zod/discussions) 上告诉我。我会把它添加到下面，并在 Twitter 上发布。

- [`tRPC`](https://github.com/trpc/trpc): 在没有 GraphQL 的情况下建立端到端的类型安全 API 。
- [`react-hook-form`](https://github.com/react-hook-form/resolvers): 使用 React Hook Form 和 Zod 解析器轻松构建类型安全的表单。
- [`ts-to-zod`](https://github.com/fabien0102/ts-to-zod): 将 TypeScript 定义转换成 Zod 模式。
- [`zod-mocking`](https://github.com/dipasqualew/zod-mocking): 从你的 Zod 模式中生成模拟数据。
- [`zod-fast-check`](https://github.com/DavidTimms/zod-fast-check): 从 Zod 模式中生成 `fast-check` 的任意数据。
- [`zod-endpoints`](https://github.com/flock-community/zod-endpoints): 约定优先的严格类型的端点与 Zod。兼容 OpenAPI。
- [`express-zod-api`](https://github.com/RobinTail/express-zod-api): 用 I/O 模式验证和自定义中间件构建基于 Express 的 API 服务
- [`zod-i18n-map`](https://github.com/aiji42/zod-i18n): 有助于翻译 Zod 错误信息。
- [`mobx-zod-form`](https://github.com/MonoidDev/mobx-zod-form): 以数据为中心的表格构建工具，基于 MobX 和 Zod。
- [`zodock`](https://github.com/ItMaga/zodock): 基于 Zod 模式生成模拟数据。

# 安装

### 必要条件

- TypeScript 4.5+!
- 在 `tsconfig.json` 中启用 `strict` 模式。这是所有 TypeScript 项目的最佳实践。

```ts
// tsconfig.json
{
  // ...
  "compilerOptions": {
    // ...
    "strict": true
  }
}
```

### 从 `npm`（Node/Bun）安装

```sh
npm install zod
yarn add zod          # yarn
bun add zod           # bun
pnpm add zod          # pnpm
```

### 从 `deno.land/x`（Deno）安装

和 Node 不同，Demo 依靠一个直接的 URL 导入而非像 npm 这样的包管理器。可以这样导入最新版本的 Zod:

```ts
import { z } from "https://deno.land/x/zod/mod.ts";
```

你也可以指定一个具体的版本：

```ts
import { z } from "https://deno.land/x/zod@v3.16.1/mod.ts";
```

> 文档的剩余部分假定你是直接通过 npm 安装的 `zod` 包。

# 基本用法

创建一个简单的字符串模式

```ts
import { z } from "zod";

// 创建一个字符串模式
const mySchema = z.string();

// 解析
mySchema.parse("tuna"); // => "tuna"
mySchema.parse(12); // => throws ZodError

// “安全”解析（验证失败时不抛出错误）
mySchema.safeParse("tuna"); // => { success: true; data: "tuna" }
mySchema.safeParse(12); // => { success: false; error: ZodError }
```

创建一个对象模式

```ts
import { z } from "zod";

const User = z.object({
  username: z.string(),
});

User.parse({ username: "Ludwig" });

// 提取出推断的类型
type User = z.infer<typeof User>;
// { username: string }
```

## 原始类型

```ts
import { z } from "zod";

// 原始值类型
z.string();
z.number();
z.bigint();
z.boolean();
z.date();
z.symbol();

// 空类型
z.undefined();
z.null();
z.void(); // 接受 undefined

// 任意类型
// 接受任何值
z.any();
z.unknown();

// never 类型
// 不接受任何值
z.never();
```

## 原始类型的强制转换

现在 Zod 还有一种更方便的方法来强制转换原始类型

```ts
const schema = z.coerce.string();
schema.parse("tuna"); // => "tuna"
schema.parse(12); // => "12"
schema.parse(true); // => "true"
```

在解析步骤中，输入将通过 `String()` 函数传递，该函数是 JavaScript 的内置函数，用于将数据强制转换为字符串。注意，返回的模式是一个 `ZodString` 实例，因此可以使用所有字符串模式的方法

```ts
z.coerce.string().email().min(5);
```

所有的原始类型都支持强制转换

```ts
z.coerce.string(); // String(input)
z.coerce.number(); // Number(input)
z.coerce.boolean(); // Boolean(input)
z.coerce.bigint(); // BigInt(input)
z.coerce.date(); // new Date(input)
```

**布尔类型的强制转换**

Zod 的布尔强制转换非常简单！它将值传入 `Boolean(value)` 函数，仅此而已。任何真值都将解析为 `true`，任何假值都将解析为 `false`

```ts
z.coerce.boolean().parse("tuna"); // => true
z.coerce.boolean().parse("true"); // => true
z.coerce.boolean().parse("false"); // => true
z.coerce.boolean().parse(1); // => true
z.coerce.boolean().parse([]); // => true

z.coerce.boolean().parse(0); // => false
z.coerce.boolean().parse(undefined); // => false
z.coerce.boolean().parse(null); // => false
```

## 字面量（literal）

```ts
const tuna = z.literal("tuna");
const twelve = z.literal(12);
const twobig = z.literal(2n); // bigint literal
const tru = z.literal(true);

const terrificSymbol = Symbol("terrific");
const terrific = z.literal(terrificSymbol);

// 检索字面量的值
tuna.value; // "tuna"
```

> 目前在 Zod 中不支持 Date 字面量。如果你有这个功能的用例，请提交一个 Issue。

## 字符串

Zod 包括一些针对字符串的验证。

```ts
// 验证
z.string().max(5);
z.string().min(5);
z.string().length(5);
z.string().email();
z.string().url();
z.string().emoji();
z.string().uuid();
z.string().cuid();
z.string().cuid2();
z.string().ulid();
z.string().duration();
z.string().regex(regex);
z.string().includes(string);
z.string().startsWith(string);
z.string().endsWith(string);
z.string().datetime(); // ISO 8601；默认值为无 UTC 偏移，选项见下文
z.string().ip(); // 默认为 IPv4 和 IPv6，选项见下文

// 转变
z.string().trim(); // 减除空白
z.string().toLowerCase(); // 小写化
z.string().toUpperCase(); // 大写化
```

> 请查看 [validator.js](https://github.com/validatorjs/validator.js)，了解可与 [Refinements](#refine) 结合使用的大量其他有用字符串验证函数。

创建字符串模式时，你可以自定义一些常见的错误信息。

```ts
const name = z.string({
  required_error: "Name is required",
  invalid_type_error: "Name must be a string",
});
```

使用验证方法时，你可以传递一个附加参数，以提供自定义错误信息。

```ts
z.string().min(5, { message: "Must be 5 or more characters long" });
z.string().max(5, { message: "Must be 5 or fewer characters long" });
z.string().length(5, { message: "Must be exactly 5 characters long" });
z.string().email({ message: "Invalid email address" });
z.string().url({ message: "Invalid url" });
z.string().emoji({ message: "Contains non-emoji characters" });
z.string().uuid({ message: "Invalid UUID" });
z.string().includes("tuna", { message: "Must include tuna" });
z.string().startsWith("https://", { message: "Must provide secure URL" });
z.string().endsWith(".com", { message: "Only .com domains allowed" });
z.string().datetime({ message: "Invalid datetime string! Must be UTC." });
z.string().ip({ message: "Invalid IP address" });
```

### ISO 日期

`z.string().datetime()` 方法执行 ISO 8601；默认为无时区偏移和任意的精度。

```ts
const datetime = z.string().datetime();

datetime.parse("2020-01-01T00:00:00Z"); // pass
datetime.parse("2020-01-01T00:00:00.123Z"); // pass
datetime.parse("2020-01-01T00:00:00.123456Z"); // pass (任意精度)
datetime.parse("2020-01-01T00:00:00+02:00"); // fail (不允许偏移)
```

将 `offset` 选项设置为 `true`，可允许时区偏移。

```ts
const datetime = z.string().datetime({ offset: true });

datetime.parse("2020-01-01T00:00:00+02:00"); // pass
datetime.parse("2020-01-01T00:00:00.123+02:00"); // pass (毫秒数可选)
datetime.parse("2020-01-01T00:00:00.123+0200"); // pass (毫秒数可选)
datetime.parse("2020-01-01T00:00:00.123+02"); // pass (只偏移小时)
datetime.parse("2020-01-01T00:00:00Z"); // pass (仍支持 Z)
```

你还可以限制允许的 "精度"。默认情况下，支持任意亚秒精度（但不是必须精确到这一位）。

```ts
const datetime = z.string().datetime({ precision: 3 });

datetime.parse("2020-01-01T00:00:00.123Z"); // pass
datetime.parse("2020-01-01T00:00:00Z"); // fail
datetime.parse("2020-01-01T00:00:00.123456Z"); // fail
```

### IP 地址

默认情况下，`z.string().ip()` 方法会验证 IPv4 和 IPv6。

```ts
const ip = z.string().ip();

ip.parse("192.168.1.1"); // pass
ip.parse("84d5:51a0:9114:1855:4cfa:f2d7:1f12:7003"); // pass
ip.parse("84d5:51a0:9114:1855:4cfa:f2d7:1f12:192.168.1.1"); // pass

ip.parse("256.1.1.1"); // fail
ip.parse("84d5:51a0:9114:gggg:4cfa:f2d7:1f12:7003"); // fail
```

你也可以指定仅接受 IPv4 或 IPv6。

```ts
const ipv4 = z.string().ip({ version: "v4" });
ipv4.parse("84d5:51a0:9114:1855:4cfa:f2d7:1f12:7003"); // fail

const ipv6 = z.string().ip({ version: "v6" });
ipv6.parse("192.168.1.1"); // fail
```

## Numbers

在创建数字模式时，你可以自定义错误信息。

```ts
const age = z.number({
  required_error: "Age is required",
  invalid_type_error: "Age must be a number",
});
```

Zod 包括一些特定的数字验证。

```ts
z.number().gt(5);
z.number().gte(5); // alias .min(5)
z.number().lt(5);
z.number().lte(5); // alias .max(5)

z.number().int(); // value must be an integer

z.number().positive(); //     > 0
z.number().nonnegative(); //  >= 0
z.number().negative(); //     < 0
z.number().nonpositive(); //  <= 0

z.number().multipleOf(5); // Evenly divisible by 5. Alias .step(5)

z.number().finite(); // value must be finite, not Infinity or -Infinity
z.number().safe(); // value must be between Number.MIN_SAFE_INTEGER and Number.MAX_SAFE_INTEGER
```

你可以选择传入第二个参数来提供一个自定义的错误信息。

```ts
z.number().max(5, { message: "this👏is👏too👏big" });
```

## Dates

```ts
z.date().safeParse(new Date()); // success: true

z.date({
  required_error: "Please select a date and time",
  invalid_type_error: "That's not a date!",
});

z.date().min(new Date("1900-01-01"), { message: "Too old" });
z.date().max(new Date(), { message: "Too young!" });
```

## Objects

```ts
// 默认情况下，所有属性都是必需的
const Dog = z.object({
  name: z.string(),
  age: z.number(),
});

// 像这样提取推断出的类型
type Dog = z.infer<typeof Dog>;

// 等价于：
type Dog = {
  name: string;
  age: number;
};
```

### `.shape`

使用 `.shape` 来访问特定键的模式。

```ts
Dog.shape.name; // => string schema
Dog.shape.age; // => number schema
```

### `.extend`

你可以用 `.extend` 方法在对象模式中添加额外的字段。

```ts
const DogWithBreed = Dog.extend({
  breed: z.string(),
});
```

你可以使用 `.extend` 来覆盖字段！要小心使用这种方式！

### `.merge`

相当于 `A.extend(B.shape)`。

```ts
const BaseTeacher = z.object({ students: z.array(z.string()) });
const HasID = z.object({ id: z.string() });

const Teacher = BaseTeacher.merge(HasID);
type Teacher = z.infer<typeof Teacher>; // => { students: string[], id: string }
```

> 如果两个模式共享 keys，那么 B 的属性将覆盖 A 的属性。返回的模式也继承了“unknownKeys 密钥”策略（strip/strict/passthrough+）和 B 的全面模式。

### `.pick/.omit`

受 TypeScript 内置的 `Pick` 和 `Omit` 工具类型的启发，所有 Zod 对象模式都有 `.pick` 和 `.omit` 方法，可以返回一个修改后的模式。比如这个 Recipe 模式：

```ts
const Recipe = z.object({
  id: z.string(),
  name: z.string(),
  ingredients: z.array(z.string()),
});
```

要想只保留某些 Key，使用 `.pick`。

```ts
const JustTheName = Recipe.pick({ name: true });
type JustTheName = z.infer<typeof JustTheName>;
// => { name: string }
```

要删除某些 Key，请使用 `.omit`。

```ts
const NoIDRecipe = Recipe.omit({ id: true });

type NoIDRecipe = z.infer<typeof NoIDRecipe>;
// => { name: string, ingredients: string[] }
```

### `.partial`

受 TypeScript 内置的 `Partial` 工具类型的启发，`.partial` 方法可以把模式的所有属性变成可选的。

比如我们有这样一个模式：

```ts
const user = z.object({
  username: z.string(),
});
// { username: string }
```

我们可以创建一个 `Partial` 版本：

```ts
const partialUser = user.partial();
// { username?: string | undefined }
```

### `.deepPartial`

`.partial` 是浅层的——嵌套的对象的属性不会变成可选的。它有一个“深层”版本：

```ts
const user = z.object({
  username: z.string(),
  location: z.object({
    latitude: z.number(),
    longitude: z.number(),
  }),
});

const deepPartialUser = user.deepPartial();

/*
{
  username?: string | undefined,
  location?: {
    latitude?: number | undefined;
    longitude?: number | undefined;
  } | undefined
}
*/
```

> 重要的限制：`.deepPartial` 只在对象模式的直接层次中按预期工作。嵌套的对象模式不能是可选的，不能是空的，不能包含细化，不能包含转换，等等……

#### 未知的 keys

默认情况下，Zod 对象的模式在解析过程中会剥离出未声明的 keys。

```ts
const person = z.object({
  name: z.string(),
});

person.parse({
  name: "bob dylan",
  extraKey: 61,
});
// => { name: "bob dylan" }
// extraKey 已经被剥离
```

### `.passthrough`

如果你不想剥离未知的 keys，可以使用 `.passthrough()`。

```ts
person.passthrough().parse({
  name: "bob dylan",
  extraKey: 61,
});
// => { name: "bob dylan", extraKey: 61 }
```

### `.strict`

你可以用 `.strict()` 来 _禁止_ 未知的 keys。如果输入中存在任何未知的 keys，Zod 将抛出一个错误。

```ts
const person = z
  .object({
    name: z.string(),
  })
  .strict();

person.parse({
  name: "bob dylan",
  extraKey: 61,
});
// => throws ZodError
```

### `.strip`

你可以使用 `.strip` 方法将一个对象模式重置为默认行为（剥离未识别的 keys）。

### `.catchall`

你可以将一个“catchall”模式传递给一个对象模式。所有未知的 keys 都将用它进行验证。

```ts
const person = z
  .object({
    name: z.string(),
  })
  .catchall(z.number());

person.parse({
  name: "bob dylan",
  validExtraKey: 61, // 运行良好
});

person.parse({
  name: "bob dylan",
  validExtraKey: false, // 未能成功
});
// => throws ZodError
```

使用 `.catchall()` 后无需再使用 `.passthrough()`，`.strip()`，或`.strict()`，因为现在所有的键都被视为“已知”。

## Arrays

```ts
const stringArray = z.array(z.string());

// 相当于
const stringArray = z.string().array();
```

要小心使用 `.array()` 方法。它返回一个新的 `ZodArray` 实例。这意味着你调用方法的 _顺序_ 很重要。比如：

```ts
z.string().optional().array(); // (string | undefined)[]
z.string().array().optional(); // string[] | undefined
```

### `.nonempty`

如果你想确保一个数组至少包含一个元素，使用 `.nonempty()`。

```ts
const nonEmptyStrings = z.string().array().nonempty();
// 现在推断的类型是
// [string, ...string[]]

nonEmptyStrings.parse([]); // throws: "Array cannot be empty"
nonEmptyStrings.parse(["Ariana Grande"]); // passes
```

### `.min/.max/.length`

```ts
z.string().array().min(5); // 必须包含 5 个或更多元素
z.string().array().max(5); // 必须包含 5 个或更少元素
z.string().array().length(5); // 必须正好包含 5 个元素
```

与 `.nonempty()` 不同，这些方法不会改变推断的类型。

## Unions

Zod 包括一个内置的 `z.union` 方法，用于合成 `OR` 类型。

```ts
const stringOrNumber = z.union([z.string(), z.number()]);

stringOrNumber.parse("foo"); // 通过
stringOrNumber.parse(14); // 通过
```

Zod 将按照每个“选项”的顺序验证输入，并返回第一个成功验证的值。

为了方便，你也可以使用 `.or` 方法。

```ts
const stringOrNumber = z.string().or(z.number());
```

## Optionals

你可以用`z.optional()`使任何模式成为可选。

```ts
const schema = z.optional(z.string());

schema.parse(undefined); // => returns undefined
type A = z.infer<typeof schema>; // string | undefined
```

你可以用 `.optional()` 方法使一个模式成为可选的。

```ts
const user = z.object({
  username: z.string().optional(),
});
type C = z.infer<typeof user>; // { username?: string | undefined };
```

#### `.unwrap`

```ts
const stringSchema = z.string();
const optionalString = stringSchema.optional();
optionalString.unwrap() === stringSchema; // true
```

## Nullables

类似地，你可以这样创建 nullable 类型：

```ts
const nullableString = z.nullable(z.string());
nullableString.parse("asdf"); // => "asdf"
nullableString.parse(null); // => null
```

你可以用 `nullable` 方法把一个模式变成 nullable：

```ts
const E = z.string().nullable(); // equivalent to D
type E = z.infer<typeof E>; // string | null
```

#### `.unwrap`

```ts
const stringSchema = z.string();
const nullableString = stringSchema.nullable();
nullableString.unwrap() === stringSchema; // true
```

## Records

Record 模式用于验证像 `{ [k: string]: number }` 这样的类型。

如果你想根据某种模式验证一个对象的 _value_ ，但不关心 keys，使用 `Record`。

```ts
const NumberCache = z.record(z.number());

type NumberCache = z.infer<typeof NumberCache>;
// => { [k: string]: number }
```

这在按 ID 存储或缓存条目上很有用。

```ts
const userSchema = z.object({ name: z.string() });
const userStoreSchema = z.record(userSchema);

type UserStore = z.infer<typeof userStoreSchema>;
// => type UserStore = { [ x: string ]: { name: string } }

const userStore: UserStore = {};

userStore["77d2586b-9e8e-4ecf-8b21-ea7e0530eadd"] = {
  name: "Carlotta",
}; // passes

userStore["77d2586b-9e8e-4ecf-8b21-ea7e0530eadd"] = {
  whatever: "Ice cream sundae",
}; // TypeError
```

#### 关于 numbers 键的说明

你可能期望`z.record()`接受两个参数，一个是 key，一个是 value。毕竟 TypeScript 的内置 Record 类型是这样的：`Record<KeyType, ValueType>`。否则，怎么在 Zod 中表示 TypeScript 类型`Record<number, any>`？

事实证明，TypeScript 在 `[k: number]` 上的行为比较反直觉：

```ts
const testMap: { [k: number]: string } = {
  1: "one",
};

for (const key in testMap) {
  console.log(`${key}: ${typeof key}`);
}
// prints: `1: string`
```

如你所见，JavaScript 会自动将所有对象 key 转换为字符串。

由于 Zod 试图补全静态类型和运行时类型之间的差距，提供一种创建带有数字键的记录模式的方法是没有意义的，因为在 JavaScript 运行时中“数字键”是不存在的。

## Maps

```ts
const stringNumberMap = z.map(z.string(), z.number());

type StringNumberMap = z.infer<typeof stringNumberMap>;
// type StringNumber = Map<string, number>
```

## Sets

```ts
const numberSet = z.set(z.number());
type numberSet = z.infer<typeof numberSet>;
// Set<number>
```

## Enums

在 Zod 中，有两种方法来定义枚举。

### Zod enums

你必须将数值数组直接传入 `z.enum()` 。像下面这样做是不行的：

```ts
const fish = ["Salmon", "Tuna", "Trout"];
const FishEnum = z.enum(fish);
```

在这种情况下，Zod 无法推断出各个枚举元素；相反，推断出的类型将是 `string` 而不是 `'Salmon'|'Tuna'|'Trout'`。

另一种可行的方式是使用 `as const`，这样 Zod 就可以推断出正确的类型。

```ts
const VALUES = ["Salmon", "Tuna", "Trout"] as const;
const FishEnum = z.enum(VALUES);
```

**自动补全**

为了获得 Zod 枚举的自动补全，请使用模式的 `.enum` 属性:

```ts
FishEnum.enum.Salmon; // => 自动补全

FishEnum.enum;
/*
=> {
  Salmon: "Salmon",
  Tuna: "Tuna",
  Trout: "Trout",
}
*/
```

你也可以用 `.options` 属性检索选项列表，作为一个元组：

```ts
FishEnum.options; // ["Salmon", "Tuna", "Trout"]);
```

### Native enums

Zod 枚举是定义和验证枚举的推荐方法。但是如果你需要对第三方库的枚举进行验证（或者你不想重写你现有的枚举），你可以使用`z.nativeEnum()`。

**数字枚举**

```ts
enum Fruits {
  Apple,
  Banana,
}

const FruitEnum = z.nativeEnum(Fruits);
type FruitEnum = z.infer<typeof FruitEnum>; // Fruits

FruitEnum.parse(Fruits.Apple); // 通过
FruitEnum.parse(Fruits.Banana); // 通过
FruitEnum.parse(0); // 通过
FruitEnum.parse(1); // 通过
FruitEnum.parse(3); // 未通过
```

**String enums**

```ts
enum Fruits {
  Apple = "apple",
  Banana = "banana",
  Cantaloupe, // 你可以混合使用数字和字符串的枚举
}

const FruitEnum = z.nativeEnum(Fruits);
type FruitEnum = z.infer<typeof FruitEnum>; // Fruits

FruitEnum.parse(Fruits.Apple); // 通过
FruitEnum.parse(Fruits.Cantaloupe); // 通过
FruitEnum.parse("apple"); // 通过
FruitEnum.parse("banana"); // 通过
FruitEnum.parse(0); // 通过
FruitEnum.parse("Cantaloupe"); // 未通过
```

**常量枚举**

`.nativeEnum()` 函数也适用于 `as const` 对象。⚠️ `as const` 需要 TypeScript 3.4+!

```ts
const Fruits = {
  Apple: "apple",
  Banana: "banana",
  Cantaloupe: 3,
} as const;

const FruitEnum = z.nativeEnum(Fruits);
type FruitEnum = z.infer<typeof FruitEnum>; // "apple" | "banana" | 3

FruitEnum.parse("apple"); // passes
FruitEnum.parse("banana"); // passes
FruitEnum.parse(3); // passes
FruitEnum.parse("Cantaloupe"); // fails
```

## Intersections

交叉类型对于创建 `logical AND` 类型很有用。这在两个取两个对象类型的交集时很有用。

```ts
const Person = z.object({
  name: z.string(),
});

const Employee = z.object({
  role: z.string(),
});

const EmployedPerson = z.intersection(Person, Employee);

// equivalent to:
const EmployedPerson = Person.and(Employee);
```

虽然一般情况下，建议使用 `A.merge(B)` 来合并两个对象，但是 `.merge` 方法会返回一个新的 `ZodObject` 实例，而 `A.and(B)` 返回一个不太有用的 `ZodIntersection` 实例，它缺乏像 `pick` 和 `omit` 这样的常用对象方法。

```ts
const a = z.union([z.number(), z.string()]);
const b = z.union([z.number(), z.boolean()]);
const c = z.intersection(a, b);

type c = z.infer<typeof c>; // => number
```

## Tuples

与数组不同，tuples 有固定数量的元素，每个元素可以有不同的类型。

```ts
const athleteSchema = z.tuple([
  z.string(), // name
  z.number(), // jersey number
  z.object({
    pointsScored: z.number(),
  }), // statistics
]);

type Athlete = z.infer<typeof athleteSchema>;
// type Athlete = [string, number, { pointsScored: number }]
```

## Recursive types

你可以在 Zod 中定义一个递归模式，但由于 TypeScript 的限制，它们的类型不能被静态推断。相反，你需要手动定义类型，并将其作为“类型提示”提供给 Zod。

```ts
interface Category {
  name: string;
  subcategories: Category[];
}

// cast to z.ZodSchema<Category>
const Category: z.ZodSchema<Category> = z.lazy(() =>
  z.object({
    name: z.string(),
    subcategories: z.array(Category),
  })
);

Category.parse({
  name: "People",
  subcategories: [
    {
      name: "Politicians",
      subcategories: [{ name: "Presidents", subcategories: [] }],
    },
  ],
}); // 通过
```

不幸的是，这段代码重复得有点多，因为你声明了两次类型：一次在 `interface` 中，另一次在 Zod 模式中。

````ts
// define all the non-recursive stuff here
const BaseCategory = z.object({
  name: z.string(),
  tags: z.array(z.string()),
  itemCount: z.number(),
});

// create an interface that extends the base schema
interface Category extends z.infer<typeof BaseCategory> {
  subcategories: Category[];
}

// merge the base schema with
// a new Zod schema containing relations
const Category: z.ZodSchema<Category> = BaseCategory.merge(
  z.object({
    subcategories: z.lazy(() => z.array(Category)),
  })
);
``` -->

#### JSON type

如果你想验证任何 JSON 值，你可以使用下面的片段。

```ts
const literalSchema = z.union([z.string(), z.number(), z.boolean(), z.null()]);
type Literal = z.infer<typeof literalSchema>;
type Json = Literal | { [key: string]: Json } | Json[];
const jsonSchema: z.ZodSchema<Json> = z.lazy(() =>
  z.union([literalSchema, z.array(jsonSchema), z.record(jsonSchema)])
);

jsonSchema.parse(data);
````

感谢 [ggoodman](https://github.com/ggoodman) 的建议。

#### Cyclical objects

虽然支持递归模式，但是将一个循环数据传入 Zod 会导致无限循环。

## Promises

```ts
const numberPromise = z.promise(z.number());
```

“Parsing”的工作方式与 promise 模式有点不同。验证分两部分进行：

1. Zod 同步检查输入是否是 `Promise` 的实例（即一个具有 `.then` 和 `.catch` 方法的对象）。
2. Zod 使用 `.then` 在现有的 `Promise` 上附加一个额外的验证步骤。你必须在返回的 `Promise` 上使用 `.catch` 来处理验证失败的问题。

```ts
numberPromise.parse("tuna");
// ZodError: Non-Promise type: string

numberPromise.parse(Promise.resolve("tuna"));
// => Promise<number>

const test = async () => {
  await numberPromise.parse(Promise.resolve("tuna"));
  // ZodError: Non-number type: string

  await numberPromise.parse(Promise.resolve(3.14));
  // => 3.14
};
```

## Instanceof

你可以使用 `z.instanceof` 来检查输入是否是一个类的实例。这在验证从第三方库中导出的类的输入时很有用。

```ts
class Test {
  name: string;
}

const TestSchema = z.instanceof(Test);

const blob: any = "whatever";
TestSchema.parse(new Test()); // passes
TestSchema.parse(blob); // throws
```

## Function schemas

Zod 还允许你定义“函数模式”。这可以让验证一个函数的输入和输出变得很容易，不会使验证代码和“业务逻辑”混到一起。

你可以用`z.function(args, returnType)`创建一个函数模式。

```ts
const myFunction = z.function();

type myFunction = z.infer<typeof myFunction>;
// => ()=>unknown
```

**定义输入和输出**

```ts
const myFunction = z
  .function()
  .args(z.string(), z.number()) // 接受任意数量的参数
  .returns(z.boolean());
type myFunction = z.infer<typeof myFunction>;
// => (arg0: string, arg1: number)=>boolean
```

**提取输入和输出模式**

你可以提取一个函数模式的参数和返回类型。

```ts
myFunction.parameters();
// => ZodTuple<[ZodString, ZodNumber]>

myFunction.returnType();
// => ZodBoolean
```

> 如果你的函数没有返回任何东西，你可以使用特殊的 `z.void()` 选项。这将让 Zod 正确地推断出无效返回的函数的类型。（无效返回的函数实际上可以返回 `undefined` 或 `null`）

函数模式有一个 `.implement()` 方法，它接受一个函数并返回一个自动验证其输入和输出的新函数。

```ts
const trimmedLength = z
  .function()
  .args(z.string()) // accepts an arbitrary number of arguments
  .returns(z.number())
  .implement((x) => {
    // TypeScript knows x is a string!
    return x.trim().length;
  });

trimmedLength("sandwich"); // => 8
trimmedLength(" asdf "); // => 4
```

如果你只关心验证输入，那就好了：

```ts
const myFunction = z
  .function()
  .args(z.string())
  .implement((arg) => {
    return [arg.length]; //
  });
myFunction; // (arg: string)=>number[]
```

# 基础类方法（ZodType）

所有的 Zod 模式都包含一些方法。

### `.parse`

`.parse(data:unknown): T`

给定任何 Zod 模式，你可以调用 `.parse` 方法来检查 `data` 是否有效。如果是的话，就会返回一个带有完整类型信息的值。否则，会抛出一个错误。

> IMPORTANT: 在 Zod 2 和 Zod 1.11+ 中，`.parse` 返回的值是你传入的变量的 _deep clone_ 。这在 zod@1.4 和更早的版本中也是如此。

```ts
const stringSchema = z.string();
stringSchema.parse("fish"); // => returns "fish"
stringSchema.parse(12); // throws Error('Non-string type: number');
```

### `.parseAsync`

`.parseAsync(data:unknown): Promise<T>`

如果你使用异步的 [refinements](#refine) 或 [transforms](#transform)（详见后文），你需要使用`.parseAsync`。

```ts
const stringSchema = z.string().refine(async (val) => val.length > 20);
const value = await stringSchema.parseAsync("hello"); // => hello
```

### `.safeParse`

`.safeParse(data:unknown): { success: true; data: T; } | { success: false; error: ZodError; }`

如果你不希望 Zod 在验证失败时抛出错误，请使用 `.safeParse`。该方法返回一个包含成功解析的数据的对象，或者一个包含验证问题详细信息的 ZodError 实例。

```ts
stringSchema.safeParse(12);
// => { success: false; error: ZodError }

stringSchema.safeParse("billie");
// => { success: true; data: 'billie' }
```

返回一个 _discriminated union_，你可以非常方便地处理错误:

```ts
const result = stringSchema.safeParse("billie");
if (!result.success) {
  // handle error then return
  result.error;
} else {
  // do something
  result.data;
}
```

### `.safeParseAsync`

> Alias: `.spa`

异步版本的 `safeParse`。

```ts
await stringSchema.safeParseAsync("billie");
```

为方便起见，它有一个别名 `.spa`。

```ts
await stringSchema.spa("billie");
```

### `.refine`

`.refine(validator: (data:T)=>any, params?: RefineParams)`

Zod 允许你通过 _refinements_ 提供自定义验证逻辑。（关于创建多个问题和自定义错误代码等高级功能，见 [`.superRefine`](#superrefine)）

Zod 被设计为尽可能地配合 TypeScript。但有许多所谓的“细化类型”，你可能希望检查不能在 TypeScript 的类型系统中表示。比如：检查一个数字是否是一个整数，或者一个字符串是否是一个有效的电子邮件地址。

比如，你可以用 `.refine` 对任何 Zod 模式定义一个自定义验证：

```ts
const myString = z.string().refine((val) => val.length <= 255, {
  message: "String can't be more than 255 characters",
});
```

> ⚠️ 细化函数不应该抛出错误。相反，它们应该返回一个虚假的值来表示失败。

#### Arguments

如你所见，`.refine` 需要两个参数。

1. 第一个是验证函数。这个函数接受一个输入（类型为 `T`——模式的推断类型）并返回 `any`。任何真实的值都会通过验证。（在 zod@1.6.2 之前，验证函数必须返回一个布尔值）
2. 第二个参数接受一些选项。你可以用它来定制某些错误处理行为。

```ts
type RefineParams = {
  // 覆盖错误信息
  message?: string;

  // 附加到错误路径中
  path?: (string | number)[];

  // params 对象，你可以用它来定制消息
  // 在错误 map 中
  params?: object;
};
```

对于高级情况，第二个参数也可以是一个返回 `RefineParams` 的函数

```ts
z.string().refine(
  (val) => val.length > 10,
  (val) => ({ message: `${val} is not more than 10 characters` })
);
```

#### Customize error path

```ts
const passwordForm = z
  .object({
    password: z.string(),
    confirm: z.string(),
  })
  .refine((data) => data.password === data.confirm, {
    message: "Passwords don't match",
    path: ["confirm"], // path of error
  })
  .parse({ password: "asdf", confirm: "qwer" });
```

因为你提供了一个“路径”参数，产生的错误将是：

```ts
ZodError {
  issues: [{
    "code": "custom",
    "path": [ "confirm" ],
    "message": "Passwords don't match"
  }]
}
```

#### Asynchronous refinements

细化也可以是异步的。

```ts
const userId = z.string().refine(async (id) => {
  // verify that ID exists in database
  return true;
});
```

> ⚠️ 如果你使用异步细化，必须使用 `.parseAsync` 方法来解析数据！否则 Zod 会抛出一个错误。

#### Relationship to transforms

变换（transforms）和细化（refinements）可以交错进行:

```ts
z.string()
  .transform((val) => val.length)
  .refine((val) => val > 25);
```

```ts
const allForms = z.object({ passwordForm }).parse({
  passwordForm: {
    password: "asdf",
    confirm: "qwer",
  },
});
```

would result in

````

ZodError {
  issues: [{
    "code": "custom",
    "path": [ "passwordForm", "confirm" ],
    "message": "Passwords don't match"
  }]
}
``` -->

### `.superRefine`

`.refine` 方法实际上是在一个更通用的（也更麻烦）的 `superRefine` 方法的语法糖。下面是一个例子:

```ts
const Strings = z.array(z.string()).superRefine((val, ctx) => {
  if (val.length > 3) {
    ctx.addIssue({
      code: z.ZodIssueCode.too_big,
      maximum: 3,
      type: "array",
      inclusive: true,
      message: "Too many items 😡",
    });
  }

  if (val.length !== new Set(val).size) {
    ctx.addIssue({
      code: z.ZodIssueCode.custom,
      message: `No duplicated allowed.`,
    });
  }
});
````

你可以随心所欲地添加问题（issues）。如果`ctx.addIssue`在函数的执行过程中没有被调用，则验证通过。

通常情况下，细化总是创建具有 `ZodIssueCode.custom` 错误代码的问题，但通过 `superRefine` 你可以创建任何代码的任何问题。每个问题代码在[错误处理指南](ERROR_HANDLING.md)中都有详细描述。

### `.transform`

要在解析后转换数据，请使用 `transform` 方法。

```ts
const stringToNumber = z.string().transform((val) => myString.length);
stringToNumber.parse("string"); // => 6
```

> ⚠️ 转化函数不应该抛出错误。请确保在使用 `transform` 之前使用 `refine` 方法，以确保输入可以被转化器解析。

#### Chaining order

注意，上面的 `stringToNumber` 是 `ZodEffects` 子类的一个实例。它不是 `ZodString` 的实例。如果你想使用 `ZodString` 的内置方法（比如 `.email()`），你必须在进行任何转换 _之前_ 使用这些方法。

```ts
const emailToDomain = z
  .string()
  .email()
  .transform((val) => val.split("@")[1]);

emailToDomain.parse("colinhacks@example.com"); // => example.com
```

#### Relationship to refinements

转换和细化可以交错进行。

```ts
z.string()
  .transform((val) => val.length)
  .refine((val) => val > 25);
```

#### Async transformations

转换也可以是异步的。

```ts
const IdToUser = z
  .string()
  .uuid()
  .transform(async (id) => {
    return await getUserById(id);
  });
```

> ⚠️ 如果你的模式包含异步变换器，你必须使用 `.parseAsync()` 或 `.safeParseAsync()` 来解析数据。否则，Zod 会抛出一个错误。

### `.default`

你可以使用转换器来实现 Zod 中“默认值”的概念。

```ts
const stringWithDefault = z.string().default("tuna");

stringWithDefault.parse(undefined); // => "tuna"
```

你可以选择在 `.default` 中传递一个函数，当需要生成默认值时，该函数将被重新执行。

```ts
const numberWithRandomDefault = z.number().default(Math.random);

numberWithRandomDefault.parse(undefined); // => 0.4413456736055323
numberWithRandomDefault.parse(undefined); // => 0.1871840107401901
numberWithRandomDefault.parse(undefined); // => 0.7223408162401552
```

### `.optional`

一个语法糖，返回一个模式的可选版本。

```ts
const optionalString = z.string().optional(); // string | undefined

// equivalent to
z.optional(z.string());
```

### `.nullable`

一个语法糖，返回一个模式的 `nullable` 版本。

```ts
const nullableString = z.string().nullable(); // string | null

// equivalent to
z.nullable(z.string());
```

### `.nullish`

一个语法糖，用于返回模式的 nullish 版本。nullish 模式同时接受 `undefined` 和 `null`。[阅读更多关于 nullish 的概念](https://www.typescriptlang.org/docs/handbook/release-notes/typescript-3-7.html#nullish-coalescing).

```ts
const nullishString = z.string().nullish(); // string | null | undefined

// equivalent to
z.string().nullable().optional();
```

### `.array`

一个语法糖，为给定类型返回一个数组模式。

```ts
const nullableString = z.string().array(); // string[]

// equivalent to
z.array(z.string());
```

### `.or`

一个语法糖，用于创建联合类型。

```ts
z.string().or(z.number()); // string | number

// equivalent to
z.union([z.string(), z.number()]);
```

### `.and`

一个语法糖，用于创建交叉类型。

```ts
z.object({ name: z.string() }).and(z.object({ age: z.number() })); // { name: string } & { age: number }

// equivalent to
z.intersection(z.object({ name: z.string() }), z.object({ age: z.number() }));
```

# Type inference

你可以用 `z.infer<typeof mySchema>` 提取任何模式的 TypeScript 类型。

```ts
const A = z.string();
type A = z.infer<typeof A>; // string

const u: A = 12; // TypeError
const u: A = "asdf"; // compiles
```

#### What about transforms?

在现实中，每个 Zod 模式实际上都与**两种**类型相关：一个输入和一个输出。对于大多数模式（比如 `z.string()`），这两个类型是相同的。但是通过转换，这两个类型可以不一样。比如，`z.string().transform(val => val.length)` 的输入为 `string`，输出为 `number`。

你可以这样提取输入和输出类型：

```ts
const stringToNumber = z.string().transform((val) => val.length);

// ⚠️ Important: z.infer 提取输出类型
type input = z.input<stringToNumber>; // string
type output = z.output<stringToNumber>; // number

// equivalent to z.output!
type inferred = z.infer<stringToNumber>; // number
```

# Errors

Zod 提供了一个名为 `ZodError` 的错误子类。ZodErrors 包含一个 `issues` 数组，包含关于验证错误的详细信息。

```ts
const data = z
  .object({
    name: z.string(),
  })
  .safeParse({ name: 12 });

if (!data.success) {
  data.error.issues;
  /* [
      {
        "code": "invalid_type",
        "expected": "string",
        "received": "number",
        "path": [ "name" ],
        "message": "Expected string, received number"
      }
  ] */
}
```

#### Error formatting

你可以使用 `.format()` 方法将这个错误转换为一个嵌套对象。

```ts
data.error.format();
/* {
  name: { _errors: [ 'Expected string, received number' ] }
} */
```

关于可能的错误和自定义错误信息的方法，请阅读 [ERROR_HANDLING.md](ERROR_HANDLING.md)。

# Comparison

还有一些其他广泛使用的验证库，但它们都有一定的设计局限性，开发者体验不理想。

#### Joi

[https://github.com/hapijs/joi](https://github.com/hapijs/joi)

不支持静态类型推导 😕

#### Yup

[https://github.com/jquense/yup](https://github.com/jquense/yup)

Yup 是一个全功能的库，最初用 Vanilla JS 实现，后来又用 TypeScript 重写。

不同点：

- 支持铸造和转换
- 对象的所有字段默认是可选的
- 缺少方法：`partial`、`deepPartial`
- 缺少 promise 模式
- 缺少 function 模式
- 缺少联合和交叉模式

#### io-ts

[https://github.com/gcanti/io-ts](https://github.com/gcanti/io-ts)

io-ts 是 gcanti 的一个优秀库。io-ts 的 API 极大地启发了 Zod 的设计。

根据我们的经验，在许多情况下，io-ts 优先考虑功能编程的纯净性，而不是开发者的经验。这是一个有效的、令人钦佩的设计目标，但它使 io-ts 特别难集成到一个现有的程序化或面向对象的代码库中。比如，在 io-ts 中定义一个有可选属性的对象需要这样：

```ts
import * as t from "io-ts";

const A = t.type({
  foo: t.string,
});

const B = t.partial({
  bar: t.number,
});

const C = t.intersection([A, B]);

type C = t.TypeOf<typeof C>;
// returns { foo: string; bar?: number | undefined }
```

你必须在不同的对象验证器中定义必需的和可选的道具，通过 `t.partial`（它将所有属性标记为可选）传递选项，然后用 `t.intersection` 组合它们。

而在 Zod 中：

```ts
const C = z.object({
  foo: z.string(),
  bar: z.number().optional(),
});

type C = z.infer<typeof C>;
// returns { foo: string; bar?: number | undefined }
```

这种更具声明性的 API 使模式定义更加简明。

io-ts 也需要使用 gcanti 的函数式编程库 fp-ts 来解析结果和处理错误。对于希望严格保持代码库功能的开发者来说，这是另一个极好的资源。但是，依赖 fp-ts 必然带来大量的知识开销；开发人员必须熟悉函数式编程的概念和 fp-ts 的命名，才能用好这个库。

- 支持具有序列化和反序列化转换功能的编解码器
- 支持 branded types
- 支持高级函数式编程、高级类型、兼容 fp-ts
- 缺少的方法:(pick, omit, partial, deepPartial, merge, extend)
- 缺少具有正确类型的非空数组（`[T, ...T[]]）。
- 缺少 promise 模式
- 缺少 function 模式

#### Runtypes

[https://github.com/pelotom/runtypes](https://github.com/pelotom/runtypes)

Runtypes 有良好的类型推理支持，但对象类型屏蔽的选项有限（没有 `.pick`、`.omit`、`.extend` 等）。不支持 `Record`（它的 `Record` 等同于 Zod 的 `object`）。他们确实支持 branded 和 readonly 类型，而 Zod 不支持。

- 支持“模式匹配”：分布在联合类型上的计算属性
- 支持只读类型
- 缺少方法：`deepPartial`、`merge`
- 缺少具有适当类型的非空数组（`[T, ...T[]]`）。
- 缺少 promise 模式
- 缺少自定义错误功能

#### Ow

[https://github.com/sindresorhus/ow](https://github.com/sindresorhus/ow)

Ow 专注于函数输入验证。它是一个使复杂的断言语句容易表达的库，但它不能解析未知类型的数据。他们支持更多的类型；Zod 与 TypeScript 的类型系统几乎是一对一的映射，而 Ow 可以让你验证几个高度特定的类型（比如`int32Array`，见其的 README 中的完整列表）。

如果你想验证函数输入，请在 Zod 中使用函数模式！这是一个更简单的方法，让你可以复用一个函数类型声明，而不需要在每个函数的开头复制粘贴一堆 Ow Assertions。此外，Zod 还可以让你验证你的返回类型，所以你可以确保不会有任何意外的数据传递到下游。

# Changelog

[CHANGELOG.md](CHANGELOG.md)
