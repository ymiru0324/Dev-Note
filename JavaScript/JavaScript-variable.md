# variable

| 변수 | 유효 범위 | 재선언 | 재할당 |
| --- | --- | --- | --- |
| var | Function-scoped | 재선언 O | 재할당 O |
| let | {Block-scoped} | 재선언 X | 재할당 O |
| const | {Block-scoped} | 재선언 X | 재할당 X |

---

### var

- 함수 유효범위
- 영역을 벗어나도 변경된 값 유지, let과 다르게 범위가 다르다

### let

- 블록 유효범위 (블록 밖에서 변수 접근 불가)
- if 벗어나면 if문 안에 선언된 변수와 다른 변수

### const

- 블록 유효범위 (블록 밖에서 변수 접근 불가)
- 변수를 선언하면 값을 바꿀 수 없다

---

## var

```jsx
var a1 = 100;
var a2 = 200;
```

```jsx
a1 = 300;
var a2 = 400;
console.log("a1: %d, a2: %d", a1, a2) // a1: 300, a2: 400
```

```jsx
var foo = 'foo1';
console.log(foo); // foo1
if(true) {
	var foo = 'foo2';
	console.log(foo); // foo2
}
console.log(foo); // foo2
```

```jsx
// if형식
if(true) {
    var y = 3;
}
console.log(y); // 3
```

## let

```jsx
let a1 = 100;
let a2 = 200;
console.log("a1: %d, a2: %d", a1, a2) // a1: 100, a2: 200
```

```jsx
let a2 = 300;
console.log("a2: %d", a2) // error
```

```jsx
let b = 100;
```

```jsx
b = 200;
console.log("b : %d", b) // 200
```

```jsx
let bar = 'bar1';
console.log(bar); // bar1
if(true) {
	let bar = 'bar2';
	console.log(bar); // bar2
}
console.log(bar); // bar1
```

```jsx
// if 형식
if(true) {
    let y = 3;
}
console.log(y); // 3
```

## const

```jsx
let a1 = 100;
let a2 = 200;
console.log("a1: %d, a2: %d", a1, a2) // a1: 100, a2: 200
```

```jsx
let a2 = 300;
console.log("a2: %d", a2) // error
```

```jsx
let b = 100;
```

```jsx
b = 200;
console.log("b : %d", b) // error
```

```jsx
// if형식
if(true) {
    const y = 3;
}
console.log(y); // error
```