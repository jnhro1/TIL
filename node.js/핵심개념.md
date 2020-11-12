### I /O

- WAS는 동기문제가 있다. 이를 해결하기위한 대책으로 NODE 등장

### 비동기

- 동기 : 어떠한 요청이 있다면 그 요청을 처리하는 대상의 상태가 같아야한다. (데이터 일치)
- 비동기 : 완료되는 시점을 동일시하지 않는다. eventloop

### Non-blocking vs blocking

- non-blocking : 어떠한 작업이 수행되는 동안 기다리지 않고 다른 작업을 진행한다.
- 자바스크립트는 이벤트주도의 개발언어이다.

### node vs browser

- window 객체 없다! 웹 브라우저상의 ui 화면이기 때문
- import 대신 require 사용
- const let var scope의 차이가 있음
- const : 상수로서 변하지 않는 값
- let : 변수 / 자신을 둘러싼 {} 범위 내에서만 유효
- var : 변수 / 파일 내부 전체에서 사용할 수 있는 변수

### node.js REPL

- nodejs와 채팅하듯
- 파워쉘 기반
- $node
- $String.(tab)
- 한줄단위로 실행하고싶을때

### npm

- —save-dev > package.json 안에 추가시키기
- -g 다른 프로젝트에서도 해당 프로그램을 사용할 수 있음
- npx 해당하는 패키지를 단순히 설치하는것이 아니라 실행목적 (파라미터로 넘겨줌)
- 삭제 : npm uninstall express / npm uninstall express -g

### semantic versioning

- 의미가 있는 버저닝 체계를 위해서 조금 더 체계적으로 버전을 관리하는 방법
- 1.0.0
- 세자리 라고 해서 꼭 semantic 이란 보장은 없음
- 각 자리수 마다 의미가 있다.
- 3자리 : 하위 호환 되는 버그 수정
- 2자리 : 하위 호환 되지만 새로운 기능 추가
- 1자리 : 하위 호환 되지 않는 중요한 변화
- ~ : patch 버전이 릴리즈 되었을 때
- ^ 마이너 버전 릴리즈
- * / x 중요한 버전 릴리즈

### npx

- 별도 설치 필요 없음 (npm 설치될 때 자동으로 됨)
- npm : 설치해서 실행하는 방식
- npx : 설치하지 않고 1회성으로 실행해보는 방식 (—save 옵션 같은 것 없음)
- npx cowsay "hello"
- node_modules 안에 설치되지 않고 임시폴더에 저장됨
- package.lock.json에 적힌 모듈 npm install 시 >  불필요한 파일로 인한 의존성 문제로 무결성이 깨질 수 있음
- 의존성 되는 모듈 최소화 해야함

### nodemon

- $npm install nodemon -g
- file>auto save
- 파일이 변경되면 그것을 감지해서 실행해주는 역할

### module.exports

- 객체나 함수/클래스 exports 가능

```jsx
function eidt() {}
function write() {}
class updeate {}

module.exports = { edit, write}
// 단일 함수 시
module.exports = edit
// 단일 클래스 시
module.exports = update;
```

### event loop

- queue (fifo)

```jsx
const queue = []
queue.push(1)
queue.push(2)
console.log(queue)
const r = queue.shift()  //(fifo)배열의 첫번째 요소를 제거하고 요소를 반환한다.
console.log(r)
```

- stack (lifo)

```jsx
const stack = []
stack.push(1)
stack.push(2)
var s = stack.pop() // 마지막 요소를 제거하고 요소를 반환
console.log(s)
```

- 직관적으로 event loop 확인할 수 있는 사이트 loupe

### every

- 해당하는 배열이 어떠한 조건에 대해 모두 만족하는 경우에!
- 'use strict'

```jsx
'use strict'
const arr = [2,3,4]

const isBiggerThanOne = arr.every(key => key > 1)
console.log(isBiggerThanOne)
```

- true 출력됨
- 배열의 모든 조건이 만족해야함
- 하나라도 만족 못하면 false 반환

### find, includes

- find : 배열에서 특정한 요소 찾기
- includes : 배열이나 문자열에서 해당 문자가 존재하는지 t/f
- find/includes 사용한다고 해서 arr 가 변하지 않음
- 새로운 데이터가 생성되고 반환되는 것

```jsx
'use strict'

const arr = ['node.js', '조나현']

const ret = arr.find(key => key == '조나현')
console.log(ret)

결과 : 조나현
// 해당하는 값을 찾고 실제 데이터를 return 시 find
```

```jsx
'use strict'

const arr = ['node.js', '조나현']

const ret = arr.includes('조나현')
console.log(ret)

결과 : true
// 해당 데이터 반환 없고 확인만 하고 싶으면 includes
// if 문에 조건절
```

### ForEach

- 직관적이고 가독성이 좋아서 사용한다.
- 비동기적으로 실행되지 않기 때문에 비동기 코드를 사용할때는 조심해야한다.

```jsx
'use strict'

const arr = [1,2,3]
const newArr = []

arr.forEach(item => console.log(item))

arr.forEach(item => {
		newArr.push(item)
})

console.log(newArr)

결과 : 1 2 3 1 2 3
```

### map, filter

- map : 배열내의 모든 요소에 대하여 주어진 함수를 호출한 결과를 모아 새로운 배열을 반환

```jsx
const a = [1,2,3]
const b = a.map(x => x+1)
console.log(b)

결과 : 2 3 4
```

- filter : 주어진 함수의 테스트를 통과하는 모든 요소를 모아 새로운 배열을 반환

```jsx
const a = [1,2,3]
const f = a.filter(x=>x>1)
console.log(f)

결과 : 2,3
```

### Object.assign vs spread

- assign : 할당하다
- 새로운 객체를 생성하기도 하고 두개의 객체를 합친다.

```jsx
'use strict'

const obj = {
	name: '조나현"
}

const newObj = P
	title: '이쁘다'
}

const ret = Obejct.assign({}, obj, newObj)
console.log(ret)

결과 : {name: '조나현', title: '이쁘다'}
```

- spread : 가독성이 좋아서 사용
- 객체뿐만 아니라 array 타입에서도 사용 가능

```jsx
'use strict'

const obj = {
	name: '조나현"
}

const newObj = {
	title: '이쁘다'
}

const arr = [1,2,3]
const newArr = [4,5,6]

const ret = {
	...obj,
  ...newObj
}

const netArr = {
	...arr,
  ...newArr
}

결과 : {name: '조나현', title: '이쁘다'}
       [1,2,3,4,5,6]
```

### Set

- 중복되지 않는 자료구조
- add 를 통해 입력받음
- 자료가 중복되지 않는다는 일관성을 보장받을 수 있음
- has() 메소드를 사용하여 해당 자료구조에 데이터가 존재하는 지 확인할 수 있음 (true/false)
- 배열을 순환하는 방식으로는 for-of 방식이 있다.

```jsx
'use strict'

const test = new Set()

test.add(1)
test.add(1)
test.add(2)
test.add(2)
test.add(3)

for(const item of test) { //test로 이루어진 item 순환
	console.log(item)
}

const ret = test.has(2)
console.log(ret)

결과 : 1 2 3 true

```

### some

- 최소 1개 이상의 요소만 조건에 만족하면 true를 반환 (every와 대조됨)

```jsx
'use strict'

const arr = [1, 2, 0, -1, -2]

const res = arr.some(key => key < 0)
console.log(res)

결과 : true
```

### Template String

- style component 에서 많이 사용됨
- ${  } 사용

```jsx
'use strict'

const details = `자세한 내용`
let str = `node.js`
str += = `어렵당${details}`

const int = 1
str += `${str}의 값은 ${int}`

console.log('입력')
console.log`입력`
```

### String

- 단순한 문자열에 대한 메소드와 객체에 적용

```jsx
'use strict'

let string = 'node.js'

let isStratWith = string.startsWith('n') //해당 문자로 시작하는지
let isIncludes = string.includes('js') // 해당 문자열이 포함되는지
let isEndWith = string.endsWith('s') //해당 문자로 끝나는지

const checkIfContains = () => {

		if (isStartWith && insIncludes && isEndWith) {
			return true
		}

}

const ret = checkIfContains()
console.log(let)
```

### Type Checking

```jsx
'use strict'

const string = 'node.js'
const array = []
const obj = {}
const number = 1

console.log(typeof string)
console.log(typeof array ) //array도 object임
console.log(typeof obj )
console.log(typeof number )
```

### Hoisting

- 생성 및 실행 단계가 어떻게 동작하는지에 대한 일반적인 생각
- js 가 코드 실행 전에 함수 선언을 메모리에 먼저 저장하는 특징

```jsx
say('hi')
function say(word) {
	console.log(word)
}
say('hi')

//코드에서 함수를 선언하기 전에 미리 함수를 실행(호출)할 수 있다.
```

### 즉시실행함수표현(IIFE)

- 정의되자마자 즉시 실행되는 함수
- 괄호 안에 둘러싸인 익명함수
- 전역 스코프에 불필요한 변수를 추가해서 오염시키는 것을 방지
- IIFE 안으로 다른 변수들이 접근하는 것을 막을 수 있는 방법임

```jsx
(function () {
	var lang = 'js';
})();
//()를 통해서 js 엔진 함수를 즉시 해석해서 실행함.
console.log(lang) //IIFE 함수안에 선언된 것은(내부의 변수) 외부에서 접근이 불가능함

결과 : 오류

var r = (function () {
	var lang = 'js';
	return lang
})();
console.log(r)
// IIFE 자체는 저장되지 않고 함수가 실행된 결과만 저장됨

결과 : js
```

### setInterval

- 이 함수가  특정한 간격으로 실행되도록 하는 함수

```jsx
setInterval(() => {}, 1000}
// {} 함수가 1000 밀리세컨 간격으로 실행됨

setInterval(() => {
	console.log('hi')
},1000}

```

### Error handling

```jsx
try {
	a
} catch (e) {
	console.log('Err' + e)
}
```

### Arrow Functions (화살표 함수)

- 람다와 유사함
- 코드 가독성 높아짐
- 기존의 this 와 다른 scope를 가짐
- 글로벌 객체의 this 를 사용한다.

```jsx
'use strict'

function add (var1, var2) {
	 return var1 + var2
}

const add = (var1, var2) => var1 + var2
//return 키워드 사라짐

```

- 연습문제

```jsx
//Curried Function : 합성함수
// 항인율을 회원에 따라 다르게 한다.

function getDiscount (price, rate) {
	return price * rate
}

getDiscount(10000, 0.1) //10000원 물건을 10% 할인

const getDiscount = (price, rate) => price * rate
getDiscount(10000, rate)
getDiscount(10000, 0.6)
getDiscount(10000, 0.6)
getDiscount(10000, 0.6)
getDiscount(10000, 0.6)
getDiscount(10000, 0.6)
getDiscount(10000, 0.6)
//회원 등급별로 다 하드코딩해야함 > 불편해
//getTenpercentOff = 0.1
//getDiscount(10000)
//활용하여 arrow function 만들기

// f(x) = x + 1
// g(x) = x^2
// h(x) = f(g(x))

const getDiscount = rate => price => rate * price
//내부적 closure 생성
//price에 대해서 함수를 선언
//es6를 이전 문법으로 바꾸어주는 사이트 : https://babeljs.io/repl

var getDiscount  = function getDiscount(rate) {
	return function (price) {
		reuturn rate*price;
	}
}
	

const getTenpercentOff = getDiscount(0.1)

getTenpercentOff(price)
```

### class

- js는 객체지향언어면서 함수형 언어면서 프로토타입 기반 언어임
- [node.green](http://node.green) 사이트

```jsx
//cache.js
//ES2015 = ES6
//ES2016 = ES7
//ES2017 = ES8
//ES2018 = ES9

'use strict'

//query manager를 클래스를 사용하여 확장하면 좋음
//class 는 한번만 생성되기 때문에 환경변수와 같이 한번만 사용되면 좋을 경우 class 사용
class cacheManager {
	constructor() {
		this.conifg = []
	}

	addConfig (obj = {})
		this.config.push(obj)
	}
	getConfig (obj = {})
		return this.config
	}
}
//constructor 는 async-await과 같은 비동기 사용 못함

const CacheManager = new cacheManager()

module.exports = cacheManager
```

### Class Extends

- 기존의 모듈화된 기능들을 재사용 할 수 있다.

```jsx
'use strict'

const cacheManager = require('./cacha')

class sessionManager extends cacheManager {

}
const SessionManager = new sessionMAnager()
SessionMAnager.addConfig({
	token: 'ran'
})
console.log(config)
```

```jsx
class Robot {
	constructor(name) {
		this.name = name
	}

	speak() {
		console.log(`$this.name}`)
	}
}

class Ai extends Robot {
	constructor(name) {
		super(name)
	}

	walk() {
		console.log(`walk: ${this.name}`)
	}
}

const r = new Robot('hi')
r.speak()

const a = new Ai('hi')
a.speak()
a.walk()

결과 : hi
hi
walk: hi
```

### Static method

- 클래스에서 new 메소드를 사용해 생성하지 않고도 사용할 수 있는 메소드

```jsx
'use strict'

class test {
	constructor() {
		this.config = {}
	}
	
	fn () {
	
	}

	static call () {
	//클래스를 생성하지 않고 클래스 내부에 바로 접근하여 함수를 실행할 수 있다.
	//constructor에 선언된 객체나 어떠한 자료도 접근할 수 없음
		console.log('static method')
	
	}
}

//일반적인 class 생성
const Test = new Test()

test.call()
//클래스임에도 불구하고 constructor 거치지 않고 사용함
```

### Destructuring : 비구조화

- 객체와 array 가능
- 배열이나 객체를 선언한다 = 구조화한다.
- 비구조화 : 선언된 데이터에서 어떠한 값을 가져오는 것

```jsx
'use strict'

const obj = {
	title: 'node.js'
	value: '어렵다'
}

const { title, value } = obj

//예전엔
//const title = obj.title
//const value = obj.value

console.log(title,value)

결과 : node.js 어렵다

const arr = [0, 1, 2]
const [, a, b] = arr
//1대1 매칭이기 때문에 비어있어도 알아서 할당됨 
console.log(a,b)

결과 : 1 2

```

### Generator 개념적 접근

- async-await 출현 이후 줄어듬
- react 에서 redux사과(?) 이해하는데 많은 도움이 됨
- generator : 생성자 / 생성하는 함수
- yield 라는 특별한 문법 사용 > return 과 다른 기능
- return :  다음 로직으로 넘어가지 않게 해당 로직을 끝내는 역할을 함
- yield : 데이터를 반환하는데 함수를 끝내지 않음 / 해당하는 조건이 실행될 때 마다 변할 때를 전제 조건으로 함
- arrow function 사용하면 안됨
- 명시적으로 선언해줘야함

```jsx
'use strict'

function* log () {
	console.log(0, yield)
	//첫번째 yield 값이 next인 해당하는 로직 호출
	console.log(1, yield)
	console.log(2, yield)
}

const gen = log()

gen.next('zero')
gen.next('first')
gen.next('second')

결과 : 0 zero
			1 first
			2 second
```

```jsx
const obj = {
	*gen() {
		let con = 0
		yield ++cnt;
		yield ++cnt;
		yield ++cnt;
	}
}

const g = obj.gen()
console.log(g.next());
console.log(g.next());
console.log(g.next());

결과 : 1,2,3
```

### Timers

- event loop의 기반이 됨
- 몇 초 뒤에 실행해야 하는 코드를 작성할 때
- timehandler 가 수행되는 조건
- 정확하게 해당하는 시간이 소요된 후 수행되는 것이 아니라 최소지연시간임!
- timer 가 여러개라면 코드레벨상에서 고려할 수 없는 외부상황에 의해 달라질 수 있음

```jsx
'use strict'

//해당 시간 후에 실행
const timeoutObj = setTimeout(() => {
	console.log('first')
}, 1000)

//즉시실행
const immediateObj = setImmediate(() => {
	console.log('second')
}

//만약 setTimeout과 setImmediate가 같다면?
setTimeout(() => {
	console.log('first')
}, 0)
setImmediate(() => {
	console.log('second')
}
// 결과 예측할 수 없음 > 임의의 결과

//해당 시간마다 반복
const IntervalObj = setInterval(() => {
	console.log('third')
},1000)

//메모리 누수를 막기 위한 비할당 과정

clearTimeout(timeoutObj)
clearImmediate(immediateObj)
clearInterval(IntervalObj )
```

### Event Emitter

- 특정 이벤트가 발생했을 때 일괄적으로 특정 코드들을 실행할 수 있도록 구조적으로 코드를 작성할 수 있는 방법을 제공

```jsx
'use strict'

const EventEmitter = require('events')

class ChatManager extends EventEmitter  {}

const chatManager = new ChatManager()
chatManager.on("join", () => {
	console.log("new user joined")
})
//join 이라는 이벤트를 등록
chatManager.emit("join")
// join 이벤트 호출
```

### DNS

```jsx
'use strict'

const dns = require('dns')

dns.lookup('google.com', (err, address, family) => {
	console.log(`address: ${adress}, ${family}`)
})

//family : ip 버전 IPv4 => 4

// 모든 도메인이 정상적인 값을 return하는 것이 아니다.
// 해당 resolve를 지원하지 않을 수도 있기 때문
// 한개의 주소가 아닌 여러개의 주소를 받는다.
// addresses 가 객체형인 경우 여러개 받을 수 있음
dns.resolve4('archive.org', (err, addresses) => {
	if (err) throw err

	const res = JSON.stringify(addresses) //객체 -> 문자열
	console.log(res)

addresses.forEach(a => {
		dns.reverse(a, (err, hostname) => {
			if (err) throw err
		
			console.log(`reverse for ${a}; ${JSON.stringify(hostnames)}`)
			})
		})
})

```

### File System

```jsx
'use strict'

const fs = require('fs')

//생략시 default utf-8
fs.readFile('test.txt', 'utf-8', (err, data) => {
	if (err) {
		console.error(err)
		return
	}

	console.log(data)
  // 콜백 형식

})

const content = 'hello world'
fs.writeFile('hello.txt', content, err => {
	if (err) {
		console.error(err)
		return
	}
	console.log('success')
})
```

```jsx
'use strict'

const fs = require('fs')
const { promisfy } = require('util')
//비구조화를 통한 선언

const read = promisfy(fs.readFile)
const wirte = promisfy(fs.wirteFile)

//promise 때문에 await 다음에 바로 콜백함수 사용 가능
//콜백함수일때는 date와 err를 반환하기 때문에 에러처리가 가능
//async-await 일때는 try-catch문으로 에러처리
const writeAndRead = async (data = '') => {
		try {
				await write('test.txt', data)
				return (await read('test.txt'))
		} catch (e) {
			console.error(e)
		}

}

wirteAndRead('something to write')
```

### Promise.all

- 여러가지 비동기 promise에 대해서 모든 작업 완료를 보장받을 수 있는 것

```jsx
'use stict;

const promise1 = new Promise((resolve, reject) => resolve('즉시 호출'))
//호출되는 시점에서 바로 반환
const promise2 = new Promise((resolve, reject) => {
	setTimeout(() => resolve('3초 뒤에 호출'), 3000)
})
//호출되고 3초 후에 실행
Promise.all([promise1, promise2])
.then(values => console.log(values))
//배열안의 모든 promise가 실행될 때까지 대기 후 리턴
//promise1도 3초동안 기다린 후 실행

결과 : 즉시 호출, 3초 뒤에 호출
```

### Promise.race

- promise들이 경쟁하여 가장 먼저 resolve 된 promise가 리턴 됨

```jsx
'use stirct'

const promise1 = new Promise(resolve, reject) => {
	setTimeout(() => resolve(2000), 2000)

consst promise2 = new Promise((resolve, reject) => {
	setTimeout(() => resolve('즉시'), 0)
})

Promise.race([promise1, promise2]). then(value => console.log(value))

결과 : 즉시
```

### http

- 간단한 로직을 작성할 때는 express보다 row level인 http 모듈을 사용해야한다.

```jsx
'use stirct'

const http = require('http')

const server = http.createServer((req, res) => {
	res.stutusCode = 200
	res.setHeader('Content-Type', 'text/html')
	res.end('<div>hello world</div?')
})
const port = process.env.PORT
server.listen(port, () => {
	console.log(`server listening on ${port}`)
})
```

### https

- secure (SSL) 프로토콜 포함
- 모든 데이터 교류 과정중에 SSL 프로토콜이 추가되어서 데이터 처리 과정이 암호화됨

```jsx
'use stirct'

const https = require('https')
const options = {
	hostname: 'google.com'
	port: 443 //기본적인 https 포트 번호
	path: '/login'
	method: 'GET'
	//create read update delete
	//POST   GET   PUT    DELETE
}

const req = https.request(options, res => {
	console.log(`statusCode: ${res.statusCode}`)

	res.on('data', d => {
		process.stdout.write(e)
	})

	req.on('error', e => {
		console.log(e)
	})
})
```

### Class vs Prototype

- 기존의 함수나 객체를 바탕으로 새로운 함수를 만드는 틀을 제공하는 것
- arrow function 사용 지양하고 명시적 함수 지향
- 프로토타입을 활용한 내부 클로저를 생성하는 방법
- 해당하는 함수가 함수 외부에 있는 함수에 접근할 수 있다.
- arrow function 내의 this는 글로벌 this 이다.
- this로 바인딩 하는 경우 문제가 생긴다.

```jsx
'use strict'

function fullstack (backend, frontend) {
	this.backend = backend
	this.frontend = frontend

	fullstack.prototype.getBackend = () => this.backend
	fullstack.prototype.setBackend = () => this.backend = backend

	fullstack.prototype.getFrontend = () => this.frontend
	fullstack.prototype.setFrontend = () => this.frontend = frontend
}

const Fullstack = new fullstack('javascript', 'javascript')
Fullstack.getBackend()
Fullstack.getFonrtend()

```

- 코드 리팩토링 : 해당 코드를 사용하는 기능과 방법을 유지하는 전제로 내부적인 동작 메커니즘을 개선하는 것

```jsx
//class 로 리팩토링

'use strict'

class fullStack {
	constructor(backend, frontend) {
		this.backend = backend
		this.frontend = frontend
	}

	getBackend () {
		return this.backend
	}

	getfrontend  () {
		return this.frontend 
	}

	setBackend (backend) {
		this.backend = backend
	}

	setFrontend (frontend) {
		this.frontend = frontend
	}
}

const Fullstack = new fullStack('javascript', 'javascript')
Fullstack.getBackend()
Fullstack.getFonrtend()
```

- 기능 상의 차이는 없지만 내부적으로 동작하는 매커니즘은 개선
- 코드의 퍼포먼스 향상과 모듈화/유지보수 쉽게 하기 위해

### Node.js TDD 프레임워크

- mocha (nodejs뿐만 아니라 frontend 에서도 사용 가능)
- intanbul  : 코드 뿐만 아니라 라이브러리 코드까지  coverage 판단 가능 (unit test)
- jest : frontend 에서 많이 사용됨
- cypress

### Memory Leaks 개념적 접근

```jsx
function study(value1, value2) {
	this.value1 = value1
	this.value2 = value2

	this.fuc1 = () => {
  //prototype 없이 함수 할당
	}
}

const problem = new study(undefined, undefined)
problem.fucn1()
```

### core repo로 살펴보는 TDD 실무

- integration 테스트 : 기존의 결과와 잘 통합이 되는지 확인

### Functional Programming

- 리듀스 사용하면 배열의 모든 요소를 for 문을 사용한 것처럼 접근 가능해짐 (한줄로!)
- map, filter 등을 사용하여 2번이상의 연산을 해야하는 과정을 1가지로 줄여줌

```jsx
'use strict'

const numbers = [10, 20, 30, 40]

const sum = numbers.reduce((tot, val) => tot + val)

const avg = numbers.reduce((tot, val, idx, arr) => {
	tot += val
	if (idx === arr.length - 1) {
		return tot/arr.length
	} else {
		return tot
	}

console.log(sum)

결과 : 100

```

```jsx
'use stirct'

const numbers = [0, 1, 2, 3, 4, 5, 6]

const res = numbers.reduce((tot, amt) => {
	if (amt > 0) tot.push(amt)
	return tot
}, [])

console.log(res)

결과 : [ 1, 2, 3, 4, 5, 6]
```

```jsx
'use stirct'

const arr = ['pdf', 'html', 'html', 'gif', 'gif', 'gif']

const res = arr.reduce((cnt, fileType) => {
	cnt[fileType] = (cnt[fileType] || 0) + 1
	return cnt
}, {})

console.log(res) //res ret

결과 : {pdf: 1, html: 2, gif: 3}
```

### Node.js 디자인 패턴 - 싱글톤 패턴

- 객체나 데이터에 대해서 단일성(최초 한번만 생성되는)을 필요로 할때
- 환경설정

```jsx
'use strict'

class CacheManager {
	constructor() {
		if(!CacheManager.instance) {
			 this._cache = []
			 CacheManager.instance = this
		}

		return CacheManager.instance
	}

}

const instance = new Cachemanager()
Object.freeze(instance)

```

### Adapter 패턴

- 클래스의 인터페이스를 사용자가 기대하는 다른 인터페이스로 변환하는 패턴
- 호환성이 없는 인터페이스여서 함께 작동할 수 없는 클래스들이 함께 작동함

### Bridge 패턴

- 동일한 ui에 대해서 여러가지 패턴을 적용할 수 있음 (dark 모드)

### Decorator 패턴

- 주어진 상황 용도에 따라 어떤 객체에 책임을 덧붙이는 패턴

### Composite 패턴

- 객체들의 관계를 트리구조로 구성하여 부분/전체를 객체로 표현하는 패턴으로 사용자가 단일,복합객체를 모두 동일하게 다룰 수 있음

### 비동기  패턴

- constructor 에서는 원래 비동기 async-await 사용할 수 없음
- 코드 리펙토링 꾸준히 해야함 (퍼포먼스와 가독성을 위해)

```jsx
'use strict'
//메소드로서
class Sample {
	*gen() {
		let cnt = 0
		yield cnt++
	}
}

const fn = new Sample()
const gn = Sample.gen()

console.log(gen.next())
console.log(gne.next())
```

```jsx
'use strict'
//동적으로
class Sample {
	// Coumputed Property
	*[Symbol.iterator]() {
		let cnt = 0
		yield cnt++
	}
}

const fn = new Sample()
const gn = Sample.gen()

console.log(Array.from(Sample))
```

- constructor에서 비동기 쓸 수 없지만 사용하는 방법

```jsx
'use strict'

class DatabaseManager {
	constructor(config) {
		this.config = config
		this.init = init //Promise <Pending> , Promise cache
	}

	query () {
		//QUERY('') Agrostic
	}

	async init () { // 최초 1회 실행(싱글톤처럼)
		
	}

	async newMember () {
		await this.init()
	}

	async deleteMember () {
		await this.init()
	}
// 반복되는 로직이 있을때는 디자인패턴고려해야함

}
```

- static factory > constructor에서의 생성자의 기능을 버리고 그 기능을 static으로 구현

```jsx
'use strict'

class DatabaseManager {
	constructor() {
	}

	static async BUILD (config) {
		const config = await this.init(config)
		return new DatabaeMAnager([Promise])
	}

	query () {
		//QUERY('') Agrostic
	}

	async init () { // 최초 1회 실행(싱글톤처럼)
		
	}

	async newMember () {
		await this.init()
	}

	async deleteMember () {
		await this.init()
	}
// 반복되는 로직이 있을때는 디자인패턴고려해야함

}

const manager = DatabaseManager.BUILD(config)
```
