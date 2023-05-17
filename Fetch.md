# SEB_TIL

## fetch
- 특정 url로부터 정보를 받아올 수 있음.
- 이과정은 비동기 과정으로 작업이 오래걸릴 수 있음.
- fetch(url)  
    .then((response)=>reponse.json())  
    .then(json=>console.log(json))
- 위 예시처럼 임의의 사이트 url에서 정보를 json데이터 형태로 저장 후 콘솔창에 보일 수 있다.

## Axios
- 앞선 fetch와 달리 써드파티 라이브러리로 npm install을 통해 설치해야 사용가능하다.
- 기능은 fetch와 유사하나 다른점은 json을 사용할 필요 없이 json데이터 형태로 자동으로 반환이 된다는 점이다.
- axios  
    .get(//url주소)
    .then(response => {
        console.log(response);
        const{data} = response;
        console.log(data);
    })
    .catch(err=>console.log(err));
- 위예시처럼 사용가능.
