# Jest ハンズオン勉強会

## 前提

このハンズオンではある程度コマンドなどの知識がある方が対象です

なるべくJestに触れてもらうために他知識の説明を排除しています

- nodeが入っていること `node -v`
- codeSandboxが扱えること


**やること**

## condeSandbox環境を作る

[static site Template](https://codesandbox.io/s/static-90oxm);

(静的サイトの方も触れれるようにstatic siteにしています)

## download

`/Users/moritakenji/Downloads/jest-for-static-site`

## cdで移動

`cd ~/Downloads/jest-for-static-site`

適時変えてください

## npm install

`npm install`

## 実行

`node_modules/.bin/jest`

※本来はpackage.json scriptsに含めるのですが説明省きたいため簡単にしています

## 実行結果

```bash
 FAIL  ./index.test.js
  ● Test suite failed to run

    Your test suite must contain at least one test.

      at node_modules/@jest/core/build/TestScheduler.js:242:24

Test Suites: 1 failed, 1 total
Tests:       0 total
Snapshots:   0 total
Time:        0.964s
Ran all test suites.
```

テストケースがないことを指摘されています

## VSCodeで開く

 `code .`
 か
 該当フォルダをVSCodeで開く

 ref: [codeでの開き方](https://github.com/kenmori/handsonFrontend/blob/master/git/work/README.md#5-%E3%82%B3%E3%83%9E%E3%83%B3%E3%83%89%E3%81%A7vscode%E7%AB%8B%E3%81%A1%E4%B8%8A%E3%81%92%E3%81%A6%E3%81%BF%E3%82%88%E3%81%86%E9%A3%9B%E3%81%B0%E3%81%97%E3%81%A6%E3%82%82%E3%81%84%E3%81%84%E3%81%A7%E3%81%99)


## 関数を書く

`index.js`

```js
export function add(a, b) {
  return a + b;
}
```

## テストを書く

```js
import { add } from "./index";

test('adds 1 + 2 to equal 3', () => {
  expect(add(1, 2)).toBe(3);
});

```

ターミナルから実行
`node_modules/.bin/jest`


<img src="https://terracetech.jp/wp-content/uploads/2021/07/スクリーンショット-2021-07-31-9.36.44.png" />


例えばundefinedが渡った時のテストは?

```js
add(undefined, 4)
```

ターミナルから実行
`node_modules/.bin/jest`

こうなる

```js
test('adds undefined + 2 to equal 3', () => {
  expect(add(undefined, 2)).toBe(3);
});
```

失敗する

```bash
moritakenji@moritaknjinoMBP jest-for-static-site-2 % node_modules/.bin/jest
 FAIL  ./index.test.js
  ✓ adds 1 + 2 to equal 3 (2ms)
  ✕ adds undefined + 2 to equal 3 (3ms)

  ● adds undefined + 2 to equal 3

    expect(received).toBe(expected) // Object.is equality

    Expected: 3
    Received: NaN

       7 |
       8 | test('adds undefined + 2 to equal 3', () => {
    >  9 |   expect(add(undefined, 2)).toBe(3);
         |                             ^
      10 | });
      11 |

      at Object.<anonymous> (index.test.js:9:29)

Test Suites: 1 failed, 1 total
Tests:       1 failed, 1 passed, 2 total
```

なぜなら
このテストで期待している
`Expected: 3`

ここが3になることを想定しているのに

実際に返ってきた値は
`Received: NaN`
だから

undefinedが渡った時にはNaNになるように修正

```js
test('adds undefined + 2 to equal NaN', () => {
  expect(add(undefined, 2)).toBe(NaN);
});
```


## VSCode拡張をインストール

`Jest`
<img src="https://terracetech.jp/wp-content/uploads/2021/07/スクリーンショット-2021-07-31-11.21.20.png" width="500" />

`Jest Runner`

<img src="https://terracetech.jp/wp-content/uploads/2021/07/スクリーンショット-2021-07-31-13.41.42.png" width="500" />


## [matcher](https://jestjs.io/docs/using-matchers)

色々なテストを試してみましょう

## jest課題

### Truthiness

WIP

### Numbers

WIP

### Strings

WIP

### Arrays and iterables

WIP

### Exceptions

[jest-changed-files](https://github.com/facebook/jest/blob/master/packages/jest-changed-files/README.md)