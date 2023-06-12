## SEB_TIL

## JSON stringify
- 서버로 데이터를 보낼때 단순한 문자열로 변환해야 호환성문제가 생기지않는다.
- JSON.stringify(obj) 로 직렬화
- JSON.parse(stringifiedObj) 로 역직렬화

## 함수 구현
- function stringifyJSON(obj) {
  
  if (typeof obj === "undefined" || typeof obj === "function") {
    return undefined;
  }

  
  if (typeof obj === "string") {
    return '"' + obj + '"';
  }

  
  if (Array.isArray(obj)) {
    const result = [];
    if (obj.length === 0) {
      return "[]";
   
    } else {
      for (let i = 0; i < obj.length; i++) {
        result.push(stringifyJSON(obj[i]));
    
      }
      return "[" + result + "]";
    }
  }

  
  if (typeof obj === "object" && obj !== null) {
    let result = "";
    
    for (let key in obj) {
      if (typeof obj[key] === "function" || obj[key] === undefined) {
        
        return "{}";
      }
      
      let json = stringifyJSON(key);
      obj[key] = stringifyJSON(obj[key]);
      result = result + json + ":" + obj[key];
      result = result + ",";
    }
    result = result.slice(0, -1);
    
    return "{" + result + "}";
  }

  return String(obj);
  
}

- 인자로 받아오는 데이터의 형태(문자열,객체,배열 등) 의 조건에 따라 각각 다른 조건문으로 구현.


## Tree ui
- function createTreeView(menu, currentNode) {
  // TODO: createTreeView 함수를 작성하세요.

  for (let item of menu) {
    if (item.children === undefined) {
    
      const li = document.createElement("li");
      currentNode.append(li);
      li.textContent = item.name;
    
    } else {
     
      const li = document.createElement("li");
      currentNode.append(li);
      
      const input = document.createElement("input");
      input.type = "checkbox";
      li.append(input);
      
      const span = document.createElement("span");
      span.textContent = item.name;
      li.append(span);
 
      const childrenUl = document.createElement("ul");
      li.append(childrenUl);

      createTreeView(item.children, childrenUl);
      
    }
  }
}
- 인자로 받아온 메뉴의 아이템에 자식요소가 없으면 li태그 생성 후 아이템 이름넣기.
- 나머지경우 li 태그 생성 후 체크박스와 이름 넣고 해당 자식요소의 ul생성.
- 생성한 자식요소의 ul을 인자로 자기자신함수를 재귀호출하여 사용.