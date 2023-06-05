## SEB_TIL

## fligthController
 findAll: (req, res) => {
    const { departure_times, arrival_times, destination, departure } = req.query;
    // TODO:

    let list = flights;
    if(req.query.departure_times){
      list = list.filter((item)=>{
        return req.query.departure_times === item.departure_times;
      })
    }
    if(req.query.arrival_times){
      list = list.filter((item)=>{
        return req.query.arrival_times === item.arrival_times;
      })
    }
    if(req.query.destination){
      list = list.filter((item)=>{
        return req.query.destination === item.destination;
      })
    }
    if(req.query.departure){
      list = list.filter((item)=>{
        return req.query.departure === item.departure;
      })
    }

    return res.status(200).json(list);
  },

  ## 위코드 설명
  - 더미데이터인 flights 를 list 라는 변수에 할당
  - 조건문1 : req.query 에 출발시간이 있을경우 list 에 필터메소드 적용하여 해당 시간만 리턴.
  - 조건문2 : req.query 에 도착시간이 있을경우 list 에 필터메소드 적용하여 해당 시간만 리턴.
  - 조건문3 : req.query 에 목적지가 있을경우 list 에 필터메소드 적용하여 해당 도착지만 리턴.
  - 조건문4 : req.query 에 출발지가 있을경우 list 에 필터메소드 적용하여 해당 출발지만 리턴.
  - 나머지 : 그냥 list그대로 json 형태로 상태코드 200과 함께 리턴.