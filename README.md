# GPD React study final homework
개퍼디 리액트 스터디의 마지막 과제입니다.   
요구사항에 따라 웹 페이지 구현을 완성해주세요!

# 사전 지식
프로젝트의 구성에 대한 기본적인 이해를 돕기 위한 설명입니다.   

## 프로젝트 설명
해당 프로젝트는 공개 API인 `OMDb API`를 기반으로 만들어졌습니다.   
(http://www.omdbapi.com/)

`OMDb API`의 영화 메타데이터를 기반으로 백엔드 API 시스템을 구축하였습니다.   
이러한 백엔드 시스템을 통해 필터 기반으로 영화를 검색하고, 해당 영화에 대한 메타데이터를 보여줍니다.   
또한 사용자별 좋아하는 영화 리스트를 서버에 저장하고, 다른 사용자에게 보여줍니다.

## 프로젝트 구성
전체적인 프로젝트 구성을 설명합니다.   
(중요하지 않은 구성은 생략)

### 디렉토리 구조
```
|- public   
    |- assets                     => 프로젝트에 필요한 이미지 리소스   
    index.html                    => 기본 구성 + 폰트 설치 스크립트 추가   
|- src   
    |- components   
        |- Footer.js   
        |- Header.js              => 상단 바 컴포넌트   
        |- Headline.js            => Search page의 헤드라인 텍스트   
        |- Loader.js              => 로딩 프로그레스   
        |- Logo.js                => TopNav의 네비게이션 로고   
        |- MovieCard.js           => MovieList의 요소   
        |- MovieDetail.js         => 영화 상세 컴포넌트   
        |- MovieList.js           => Search 탭의 결과 컴포넌트   
        |- Recommend.js           => Recommend 탭 컴포넌트
        |- Search.js              => Search 탭의 검색 컴포넌트   
        |- TopNav.js              => 상단 바의 네비게이션   
    |- data                       => 프로젝트에 필요한 데이터들   
    |- style                      => scss 스타일. 각 컴포넌트명과 동일   
    App.js   
    App.scss   
    index.css   
    index.js   
```

### 의존성
해당 앱은 create-react-app으로 구성되었습니다.
추가 된 의존성
- react-router-dom@v5
- node-sass
- react-redux

# 기능 요구사항
최소 기능 및 기본적인 스타일은 구성되어 있습니다.    
데이터 형태나 스타일은 수정해도 됩니다.    
아래 요구사항을 추가 구현해주세요.

## 상단 네비게이션
1. 상단 네비게이션 바 우측의 Github 아이콘 링크 주소를 본인의 프로젝트 주소로 변경해주세요.(./data/nav.js의 데이터 수정)

## Search 탭
1. 검색창의 입력, 장르 선택, 연도 선택 데이터를 `State`와 동기화해주세요.
2. Apply 버튼 클릭 시 `axios`를 통해 서버에서 데이터를 검색해주세요.(선택사항 : 입력 데이터 검증 과정도 있으면 좋습니다)
3. axios로 데이터를 검색하는 동안 `Loader` 컴포넌트를 활용해 로딩중 효과를 적용해주세요.
4. 영화 데이터를 가져오면 각 영화 데이터를 `MovieList` 및 `MovieCard` 컴포넌트에 뿌려주세요.    
    (`MovieCard`의 각 컴포넌트는 포스터 이미지를 재요청 하게되고, 해당 이미지가 로딩 될 때까지 로딩바가 나타나도록 구현되어있습니다. 이 과정이 어떻게 구현되었는지 자세히 살펴보세요.)
5. `MovieCard` 클릭 시 `/movie/:id` 경로로 라우팅 후에 `axios`를 통한 영화 상세 정보 요청을 구현해주세요.
6. 영화 상세 정보를 가져오는 도중에는 Loader를 활용하여 로딩중 효과를 적용해주세요.
7. 데이터를 가져오면 `MovieDetail` 컴포넌트에 데이터를 뿌려주세요.
8. 영화 상세 페이지에서 ♡를 누르면 서버에 해당 데이터를 저장해주세요.

```javascript
// 찜하기 데이터 구조
{
  "name": "String",
  "movieId": "String",
  "like": "boolean"
}
```

## Recommend 탭(선택사항)
1. 찜하기 테이블의 모든 데이터를 가져옵니다.
2. 유저별로 찜한 영화 리스트를 화면에 뿌려주세요.(최대 5개)
