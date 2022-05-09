# github.io

[GitHub Pages](https://pages.github.com/)

Github에서 지원하는 정적 호스팅 페이지로, 실제 서버를 운영하는듯이 접근 가능 !

![제목 없음.png](github%20io%2035e531ee2644406ba0f66ebdd23f0b90/%EC%A0%9C%EB%AA%A9_%EC%97%86%EC%9D%8C.png)

---

## 정적 사이트 생성기

정적 사이트 생성기를 통해 여러 레퍼런스를 사용할 수 있다.

[Static Site Generators - Top Open Source SSGs | Jamstack](https://jamstack.org/generators/)

그 중에서도 가장 많이 사용하는 정적 사이트 생성기

```
Jekyll
  -루비 기반
  -현재 가장 인기 있음(깃헙 별 수 제일 많음)
  -한글 레퍼런스도 제일 많음
  -느리다는 제보가 많음(몇 십개의 포스팅 뿐인데도 빌드 하는데 5분씩 걸린다고)
  -윈도우 공식 지원 안됨

Hexo
  -자바스크립트(Node.js) 기반
  -한글 레퍼런스 꽤 많음
  -메인 개발자가 손을 놓은 듯
  -개발자가 중국인? 이라 구글링하면 중국어 글이 많이 나옴

Hugo
  -Golang 기반
  -빌드 빠름
  -문서화 잘돼있음
  -깃헙 별 수가 헥소보다 많음
  -한글 레퍼런스가 거의 없음
```

그치만 나는 사용해 본적이 없기에 이런것들이 있구나 ~ 하고 간단히 숙지하고 넘어간다.

---

## 기본적인 사용방법

1. repo 생성
    
    ![다운로드.png](github%20io%2035e531ee2644406ba0f66ebdd23f0b90/%EB%8B%A4%EC%9A%B4%EB%A1%9C%EB%93%9C.png)
    
2. repo 이름 설정
    
    > 반드시 [username.github.io] 형식으로 생성할 것
    > 
    
    사용자의 이름과 정확히 일치하지 않으면 작동하지 않음
    
3. 첫 화면 페이지는 index.html로 설정후 최상위 디렉토리 파일로 빼준 후 커밋
    
    ![6.png](github%20io%2035e531ee2644406ba0f66ebdd23f0b90/6.png)
    
4. username.github.io 도메인으로 이동하여 테스트