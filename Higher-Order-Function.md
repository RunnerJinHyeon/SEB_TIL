# SEB_TIL

#### TIL 첫 작성

## 고차함수
- 2023년 5월 15일
- 고차함수란 함수를 전달인자로 받을 수 있고, 함수를 리턴할 수 있는 함수이다.
- 예시 : 
  function double(num){
    return num *2;
  }

  function doubleNum(func,num){
    return func(num);
  }

  위의 예시에서 고차함수 doubleNum에 전달인자로 함수인 double을 넣고, num 전달인자에 숫자 4를 입력하면, 결과는 8이 나온다.

## Underbar 라이브러리
- 2023년 5월 15일
- 고차함수의 특징을 활용하여 기존에 배열에 사용하던 메소드들인 .map , .reduce 등을 _.map , _.reduce 로 나만의 새로운 함수를 만들어봄.

