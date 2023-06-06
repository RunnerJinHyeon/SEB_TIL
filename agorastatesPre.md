## SEB_TIL

## 나만의 아고라 스테이츠 서버 예습

### app.js
- app.use(cors());
- app.use(express.json({strict:false}));

### /router/discussions.js
- router.get("/",findAll);
- router.get("/:id",findById);

### /controller/index.js
- findAll: (req, res) => {
    // TODO: 모든 discussions 목록을 응답합니다.
    if(Object.keys(req.query).length === 0){
      return res.status(200).send(discussionsData);
    }
  },

- findById: (req, res) => {
    // TODO: 요청으로 들어온 id와 일치하는 discussion을 응답합니다.
    const { id } = req.params;

    let filteredData = discussionsData.filter(discussion => {
      return discussion.id === Number(id);
    })

    if(filteredData.length === 0){
      return res.status(404).json(`${id} is not found`);
    }else{
      return res.status(200).json(filteredData[0])
    }
    
  }



