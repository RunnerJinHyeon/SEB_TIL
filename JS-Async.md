# SEB_TIL

## 비동기 자바스크립트
- 2023년 5월 16일
- 자바스크립트는 싱글스레드기반으로 동작하는 언어이므로 동기적으로 작동하지만, 자바스크립트가 작동하는 환경(런타임)에서 비동기처리를 도와준다.
- 비동기 자바스크립트 예시 :
  const printString = (string) => {
    setTimeout(function () {
      console.log(string);
    },Math.floor(Math.random()*100)+1);
  };

  const printAll = () => {
    printString('A');
    printString('B');
    printString('C');
  }
  위의 코드가 실행되면 동작이 완료되는 순서대로 작동한다. 즉 코드의 순서를 예측할 수 없다.
- 비동기 예측 가능하도록 구현 :
  const printString = (string, callback) => {
  setTimeout(function () {
    console.log(string);
    callback();
  }, Math.floor(Math.random() * 100) + 1);
};

const printAll = () => {
  printString('A', () => {
    printString('B', () => {
      printString('C', () => {});
    });
  });
};
위 코드처럼 printString 함수 안에 콜백함수로 또 printString함수를 사용하여 비동기 함수의 순서를 예측할 수 있도록 구현.

## Promise

- 비동기 구현에서 배운듯이 콜백함수를 활용하여 비동기함수를 작성하게되면 짧으면 괜찮으나 작동시켜야 하는 함수가 많아지면 매우 길고 보기 안좋은 코드를 작성해야 한다. 이를 방지하고자 Promise 클래스를 활용한다.
- let promise = new Promise((resolve , reject)=>{
  //정상처리 되었을떄
  resolve(value);
  //에러가 발생했을때
  reject(error);
})
- 위 코드에서 정상처리 되었을때 .then 메소드를 활용하여 처리된 해당 데이터를 가져와 콜백함수의 인자로 사용가능.
- let promise = new Promise((resolve, reject) => {
	resolve("성공");
});

promise.then(value => {
	console.log(value);
	// "성공"
})
- 에러가 발생했을땐 .catch 메소드를 활용하여 접근가능.

## Promise Chaining
- Promise 를 활용해서 순차적으로 비동기작업 진행.
- let promise = new Promise(function(resolve, reject) {
	resolve("성공");
});

promise
.then(value => {
	console.log(value);
	// "성공"
})
.catch(error => {
	console.log(error);
})
.finally(() => {
	console.log("성공이든 실패든 작동!");
	// "성공이든 실패든 작동!"
})
- 위코드처럼 순서대로 .then , .catch , .finally 메소드를 작동시킴.


## Async / Await
- 일반적인 함수선언식 앞에 async 키워드를 작성.
- 함수내에 실행시키고자 하는 코드 앞에 await 키워드를 작성.
- // 함수 선언식
async function funcDeclarations() {
	await 작성하고자 하는 코드
	...
}

// 함수 표현식
const funcExpression = async function () {
	await 작성하고자 하는 코드
	...
}

// 화살표 함수
const ArrowFunc = async () => {
	await 작성하고자 하는 코드
	...
}


