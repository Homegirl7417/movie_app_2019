Memo

1. props
//props를 사용하는 방법은 2가지.
//pros.fav 
//또는 { fav } . pros 내부에서 바로 가지고 오는 방법.
function Food({ name, picture, rating }) {
  return <div>
    <h1>I like {name}</h1>
    <h4>{rating}/5.0</h4>
    <img src={picture} alt={name}></img>
  </div>
}

2. prop-types
//propTypes 체크는 npm i prop-types 설치 후.
//propTypes 조건을 만족시키지 못하면 웹에 로딩은 되는 데, 콘솔에 error message가 뜸.
Food.propTypes = {
  name: PropTypes.string.isRequired,
  picture: PropTypes.string.isRequired, 
  rating: PropTypes.number.isRequired
};

3. state
  //state는 직접 변경 X. this.setState를 이용 O.
  //this.state.count 대신 
  //this.setState(current => ({ count: current.count + 1 }));

  render(){
      const { isLoading } = this.state;
      return <div>{isLoading}</div>;
  }

  4. life cycle
  1) componentDidMount : data를 fectch 하기 좋음.

  5. map
  map은 항상 무언갈 return 해야 함.
  map은 array를 return.
  map 자체에서 두번째 파라미터로 index를 제공하고, 이걸로 key를 만들 수 있음. 

  Ex.
  genres.map((genre, index) => (
                    <li key={index} className="genres__genre">
                        {index}{genre}
                    </li>
                ))


6. github page에 업로드 하는 방법
step1. npm i gh-pages
step2. package.json에 다음을 추가.

1) 홈페이지 (다 소문자여야함 / 뛰어쓰기 안됨)
"homepage": "https://homegirl7417.github.io/movie_app_2019/"

2) 디플로이, 프리 디플로이 - 빌드한 파일을 홈페이지에 올리는 것.
"scripts": {
    "start": "react-scripts start",
    "build": "react-scripts build",
    "deploy": "gh-pages -d build",
    "predeploy": "npm run build"
}

3) npm run deploy 실행

ps. github page에서 browerRouter는 정확히 설정하기 어렵다. github page를 쓸거라면 hashRouter를 쓰는 편이 좋다.

7. route 핸들링
-영화 목록에서 하나를 클릭해서 movie-detail로 가면,
history -> location -> state에 props로 전달받은 데이터들이 보인다.

-하지만, 주소창에 'movie-detail'을 입력해 들어가면, 전달받은 props가 없고 undefined로 나옴.
이걸 핸들링 해야 한다.
아래는 주소창에 'movie-detail'을 입력하면 history.push를 이용해 홈 화면으로 리다이렉션 시켜버리는 코드.

componentDidMount() {
        const { location, history } = this.props;
        if (location.state === undefined) {
            history.push('/');
        }
}
=======
# movie_app_2019
rating이 높은 영화들을 보여주는 웹사이트
>>>>>>> a63cff080b54ff53ebfa51708519037876aff97f
