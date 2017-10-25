# Page Object Pattern을 활용한 GUI테스트 코드 작성

##### 개요
```
UI에서 페이지를 하나의 Object로 보고 Page Object를 구성하여 해당 Object에 element와 action을 구현.
테스트 코드 작성 시, 이 Page Object 인스턴스의 메서드를 호출.
```
##### 장점
```
- driver를 직접 호출하는 부분이 적어지면서 속도가 빨라짐.
- 코드 가독성 향상
- 유지보수가 쉬움

```
##### 예시
```
ContentPage contentPage = new ContentPage().open(driver);
PlayListPage playListPage = contentPage.clickAddButtonAndVerify();
playListPage.dragAndDropAndVerify();
```

##### 참고
```
https://www.guru99.com/page-object-model-pom-page-factory-in-selenium-ultimate-guide.html
https://www.pluralsight.com/guides/software-engineering-best-practices/getting-started-with-page-object-pattern-for-your-selenium-tests
```
