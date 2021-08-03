# :boom: Workshop

---

​			

## 1. Semantic Tag

 제시된 semantic.html과 semantic.css를 수정하여 다음 이미지와 같은 형태가 되도록 코드를 작성하시오.



```html
/* 1. article 태그는 white로 나머지 시멘틱 태그는 lightgrey로 배경색을 바꿔주세요. */
header, nav, section, aside, footer {
  background-color: lightgrey;
}
article {
  background-color: white;
  margin: 4px;
}
/* 2. header, nav, footer 태그의 margin을 4px로 만들어주세요. */
header, nav, footer {
  margin: 2px;
}
/* 3. header, nav, footer 태그의 padding을 4px로 만들어주세요. */
header, nav, footer {
  padding: 4px;
}
/* 4. h1 태그를 수평 중앙 정렬 시켜주세요. */
h1 {
  text-align: center;
}
/* 5. section 태그는 width 490px height 300px, 
   aside 태그는 width 280px height 300px로 만들어주세요.*/
section {
  width: 490px;
  height: 300px;
  padding: 2.5px;
}
aside {
  width: 280px;
  height: 300px;
  padding: 2.2px;
}   

/* 6. 모든 semantic 태그의 border 두께를 1px, 실선, 검은색으로 만들어주세요. */
header, nav, section, article, aside, footer {
  border-width: 1px;
  border:black;
  border-style: solid;
}

/* 7. 모든 semantic 태그의 border 모서리 반경을 4px로 만들어주세요. */
header, nav, section, article, aside, footer {
  border-radius: 4px;
}

```

​						