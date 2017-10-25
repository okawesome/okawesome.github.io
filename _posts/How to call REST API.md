# REST API 라이브러리 

### RestTemplate
```
Spring에서 제공하는 Client Side에서 REST를 활용하기 위한 클래스
```
##### 예시
```java
import org.junit.Assert;
import org.junit.Test;
import org.springframework.http.HttpStatus;
import org.springframework.http.ResponseEntity;
import org.springframework.web.client.RestTemplate;

public class SpringbootstudyApplicationTests {

	@Test
	public void restTemplateTest() {
		RestTemplate r = new RestTemplate();
		ResponseEntity resp = r.getForEntity("https://jsonplaceholder.typicode.com/posts", String.class);
		Assert.assertEquals(resp.getStatusCode(), HttpStatus.OK);
	}

}

```
##### Retrofit
```
- Android, Java를 위한 client-side REST API 라이브러리
- API명세를 정의하는 Interface, Response에 대한 Model객체, 이들을 활용하기 위한 Retrofit객체 인스턴스가 반드시 필요하다.
```

##### 예시 
##### Interface
```java
package RetrofitTest;

import retrofit.Call;
import retrofit.http.GET;

import java.util.List;

public interface RetrofitInterface {

    @GET("/posts")
    Call<List<ResponseModel>> getFromSamplePage();

}

```
##### Response Model
```java
package RetrofitTest;

public class ResponseModel {

    private String userId;
    private String id;
    private String title;
    private String body;
    
    public String getUserId() {
        return userId;
    }

    public void setUserId(String userId) {
        this.userId = userId;
    }

    public String getId() {
        return id;
    }

    public void setId(String id) {
        this.id = id;
    }

    public String getTitle() {
        return title;
    }

    public void setTitle(String title) {
        this.title = title;
    }

    public String getBody() {
        return body;
    }

    public void setBody(String body) {
        this.body = body;
    }
}

```
##### Test Code
```java

import org.junit.Assert;
import org.junit.Test;
import retrofit.Call;
import retrofit.GsonConverterFactory;
import retrofit.Retrofit;

import java.util.List;

public class RetrofitTest {
    
    @Test
    public void retrofitTest() throws Exception {
        Retrofit.Builder builder = new Retrofit.Builder()
                .baseUrl("https://jsonplaceholder.typicode.com/")
                .addConverterFactory(GsonConverterFactory.create());
        Retrofit retrofit = builder.build();

        RetrofitInterface retrofitInterface = retrofit.create(RetrofitInterface.class);
        Call<List<ResponseModel>> call = retrofitInterface.getFromSamplePage();
        List<ResponseModel> resp = call.execute().body();

        resp.forEach(rm -> {
            System.out.println("userId : " + rm.getUserId().toString());
            System.out.println(" id : " + rm.getId().toString() + "\n");
        });

         Assert.assertEquals(resp.get(0).getId().toString(),"1");
    }
}

```
