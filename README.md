# React MovieFlix
Learning React and ES6 by building a Movie Discovery App. (normadcoders)

## Screens

- [ ] Home
- [ ] TV Shows
- [ ] Search
- [ ] Detail

## 프로젝트에 필요한 컴포넌트

* 프로젝트 설치
    * `npx create-react-app react-movie-flix`
* npm 보다 가벼운 yarn 사용
    * `brew install yarn`
* 필요없는 소스 정리 후 prop-types 추가
    * `yarn add prop-types`
* Route를 위한 컴포넌트 추가
    * `yarn add react-router-dom`    
* 어플리케이션 실행
    * `yarn start`

# 강의 메모

## 3.2 CSS in React part Three

* `yarn add styled-components`
* html 의 속성을 styled.태그 로 따로 설정하여 css를 localization 처리할 수 있다.
* 실제 브라우저에서 각 태그의 class 이름은 랜덤하게 생성되므로 중복되지 않는다.
    ```js
    import React from "react";
    import { Link } from "react-router-dom";
    import styled from "styled-components";

    const Header = styled.header``;

    const List = styled.ul`
        display: flex;
    `;

    const Item = styled.li``;

    const SLink = styled(Link)``;


    export default () => (
        <Header>
            <List>
                <Item>
                    <SLink to="/">Movies</SLink>
                </Item>
                <Item>
                    <SLink to="/tv">TV</SLink>
                </Item>
                <Item>
                    <SLink to="/search">Search</SLink>
                </Item>
            </List>
        </Header>
    )
    ```

## 3.3 GlobalStyles and Header

* `yarn add styled-reset`
* styled components 를 이용하여 global css 가 적용되도록 하는 컴포넌트
* 아래 처럼 reset 을 이용해 작성하고 App.js에 추가하여 사용
    ```js
    import { createGlobalStyle } from "styled-components";
    import reset from "styled-reset";

    const globalStyles = createGlobalStyle`
        ${reset};
        a{
            text-decoration:none;
            color:inherit;
        }
        *{
            box-sizing:border-box;
        }
        body{
            font-family:--apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
            font-size:14px;
            background-color:rgba(20, 20, 20, 1);
        }
    `;

    export default globalStyles;
    ```

## 4.0 Introduction to The Movie DB API

* the moviedb api (한글가능)
    * https://www.themoviedb.org 가입
    * 계정설정 > API 키 생성
    * https://developers.themoviedb.org/3/getting-started/introduction 참고 하여 개발
* http 를 사용하기 위해 axios 설치
    * `yarn add axios@0.18.1`
    * axios^0.19.2 버전에서는 url params 가 넘어가지 않는 현상있음
    * 만약 이미 최신버전이 설치 되었다면 `yarn remove axios` 로 삭제하고 재설치하는 것이 정신건강에 좋음

* API Verbs
    - [ ] New Playing (Movie)
    - [ ] Upcoming (Movie)
    - [ ] Top Rated (TV)
    - [ ] Popular (TV, Movie)
    - [ ] Airing Today (TV)
    - [ ] TV Show Detail
    - [ ] Movie Detail
    - [ ] Search (TV, Movie)

## 5.0 Container Presenter Pattern

* 데이터 처리 영역과 화면 표시 영역의 개발을 분리하고 관리하기 위한 패턴
* Router 에서 path에 해당하는 component 를 호출하는데 보통 js 파일이 되지만, 같은 이름의 폴더로 만들어놓고 내부에 index.js가 있다면 동일하게 인식하고 동작함
* 호출된 index.js -> Container.js -> Presenter.js 순서로 호출하게 구조화한다
    * Container : 실제 동작을 위한 class component 와 state 를 이용하여 데이터 로딩
    * Presenter : 넘겨진 데이터를 이용하여 화면에 표시
* 자바 스크립트에서 async 를 펑션앞에 사용하면 비동기처리하고 내부에서 특별히 기다려야 한다면 await 를 명령 앞에 표시
    ```js
    async componentDidMount() {
        const nowPlaying = await moviesApi.nowPlaying();
    }
    ```

## 6.0 Presenter Structure

