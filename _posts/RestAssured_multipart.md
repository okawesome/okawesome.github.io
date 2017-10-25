# RestAssured - Multipart

##### RestAssured 사용시 컨텐츠 타입이 application/json이 아니고 Multipart인 경우
```
.multiPart를 사용하여 전송하려는 파일 경로를 설정, .formParam을 사용하여 파라메터를 설정
```
##### 예시
```
given().
         multiPart("file1", Paths.get(Resources.getResource("images/test.png").toURI()).toFile())
         multiPart("file2", new File("/home/johan/some_other_large_file.bin")).
         multiPart("file3", "file_name.bin", inputStream).
         formParam("name", "value").
expect().
         body("fileUploadResult", is("OK")).
when().
         post("/advancedFileUpload");
```
