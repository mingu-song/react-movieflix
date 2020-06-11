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
