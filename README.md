# :pushpin: Java로 테니스 계수기 만들기 (팀' ver & 개인' ver)

> Java의 interface 개념을 활용한 테니스 계수기 구현과 파일 출력기능  
> https://go-quality.dev  

</br> 

### 목차

1. 제작기간 & 참여 인원  <br>

2. 사용 기술  <br>

3. 요구 분석    <br>

4. 순서도 (프로그램 흐름)  <br>

5. 클래스 다이어그램 - Interface의 두가지 사용방법  <br>

6. 핵심 기능 코딩- 팀'ver 코드설명<br>

7. 트러블 슈팅  <br>

8. 객체 지향 프로그래밍을 더 잘 활용해보자 - 개인'ver 코드설명 <br>

9. 프로젝트 회고 <br>

   <br> 


## 1. 제작 기간 & 참여 인원 

- 팀 프로젝트 (7인) - Interface의 첫번째 활용방법   <br>
  -  2023 3월 7일 ~ 3월 10일 (4일)  <br>
- 개인 프로젝트 (1인) - Interface의 두번째 활용방법  <br>
  	*   2023 7월 12일 ~ 7월 13일 (2일)  <br>

</br>



## 2. 사용 기술  

- Java 8 사용  <br>
- 툴 : eclipse 사용   <br>

</br>



## 3. 요구 분석 

① 두 선수 중 포인트를 득점한 선수의 게임 포인트를 증가시킨다. 득점할 때마다 득점 포인트는 0→15→30→40 순으로 표현한다.  <br>
② 게임 점수가 40인 선수가 포인트를 획득하면 그 게임을 승리한다. 단, 두 선수가 모두 40점인 경우는 듀스가 된다. 듀스가 된 후에는 상대방보다 두 포인트를 더 획득한 선수가 그 게임을 승리한다.  <br>
③ 상대방보다 2게임 이상 차이를 두고 6게임 이상을 먼저 획득한 선수가 그 세트를 승리한다.   <br>
④ 경기 세트 수의 반 이상을 먼저 승리한 선수가 최종 승자이다.  <br> <br>

👏 정리하면,  <br>
포인트 > 게임 > 세트 > 매치 (게임종료)   <br>

1. 포인트  <br>
   0(0점) > 15(1점) > 30(2점) > 40(3점)  <br>
   => 40점(3점)인 선수가 한번더 득점시 (4포인트 획득 시) 1게임 획득   <br>

 ✔  듀스 : 40:40 > 어드벤티지룰 : 두포인트 더 획득시 한게임 획득   <br>

2. 게임<br>
   6 게임 승리시 한세트 획득  <br>

✔ 듀스 : 5:5 > 어드벤티지룰 : 두 게임 연속으로 이겨야 한 세트 획득   <br>
✔ 테이브레이크 : 6:6이 되면 2 게임을 더 얻는 방식 (고려 X)  <br>

3. 세트 

* 여성 단식/ 복식 / 혼합복식 : 3세트 => 2세트 획득시 매치(승리)  <br>

* 남성 단식/ 복식 : 5세트 => 3세트 획득시 매치(승리) <br><br>

  

## 4. 순서도 (프로그램 흐름) 



​	이 서비스의 핵심 기능은 포인트를 획득해 전체적인 경기 점수에 반영하는 계수기 기능과 현재 게임 스코어를 출력하는 점수판 기능입니다. 사용자는 경기수와 경기자를 설정하고 실행을 하면 반복적으로 승자를 도출하며 테니스 경기를 자동으로 실행하고 경기 종료시 파일에 그 결과를 출력합니다.


​	이 단순한 기능의 흐름을 보면, 서비스가 어떻게 동작하는지 알 수 있습니다.  



![프로그램 순서도](D:\Programming\images\readme\프로그램 순서도.jpg)



## 5. 클래스 다이어그램 설계



<details>
<summary><b>핵심 기능 설명 펼치기</b></summary>
<div markdown="1">

### 5.1. Interface 개념 및 두가지 활용방안 





### 5.2. 클래스 다이어그램 (팀)

##### 2023-03

![클래스 다이어그램](D:\Programming\images\readme\클래스 다이어그램.jpg)



### 5.3. 클래스 다이어그램 (개인) 

##### 2023-07



![클래스다이어그램](D:\Programming\images\readme\클래스다이어그램.jpg)

* interface ScoreCounter의 활용 : interface에 포인트를 올리는 계수기 기능 메서드와 점수를 출력하는 점수판 기능의 메서드를 선언하여 실제 경기를 진행하는 ClassMain에서 해당 메서드를 실행할 수 있고 Class ScoreCounter에선 해당 인터페이스의 메서드를 구현하는 방식으로 역할분담을 해서 실제로 기능을 명확히 정해놓으니 계수기 객체가 다 구현이 안되었더라도 실행부 개발과 구현부 개발을 동시에 진행할 수 있었다.  <br>



+ 블로그 link : 못했던 구현을 6개월 뒤 교육과정이 끝난 후 성공하다 (우리가 그때 좀더 알았더라면...)









## 6. 핵심 기능

👩‍💻 팀/ 개인 프로젝트는 해당 계수기 객체를 호출하는 방식 부분만 다르기 때문에 기능 코드설명은 팀 프로젝트 기준으로 설명하겠습니다. 

<details>
<summary><b>핵심 기능 설명 펼치기</b></summary>
<div markdown="1">


### 4.1. 전체 흐름

![핵심기능](D:\Programming\images\readme\핵심기능.png)

* Class TennisMain : 테니스 경기수 , 경기할 플레이어 등 경기를 세팅해 해당 정보로 계수기 객체를 생성하고 반복문으로 득점자를 도출해 생성해준 계수기 객체에 반영하는 실제 경기 실행 클래스 <br>
* Class ScoreCounter: 테니스의 전반적인 규칙을 반영한 클래스. 크게 점수를 계산하는 계수기 기능과 점수를 출력하는 점수판 기능으로 이루어져 있다. <br>
* Class WriteResult : 최종적인 경기결과를 파일에 출력해주는 출력기능 클래스 <br>



### 4.2. 게임 세팅 및 진행 - main () 

![](https://zuminternet.github.io/images/portal/post/2019-04-22-ZUM-Pilot-integer/flow_vue.png)

- **URL 정규식 체크** :pushpin: [코드 확인](https://github.com/Integerous/goQuality/blob/b587bbff4dce02e3bec4f4787151a9b6fa326319/frontend/src/components/PostInput.vue#L67)

  - Vue.js로 렌더링된 화면단에서, 사용자가 등록을 시도한 URL의 모양새를 정규식으로 확인합니다.
  - URL의 모양새가 아닌 경우, 에러 메세지를 띄웁니다.

- **Axios 비동기 요청** :pushpin: [코드 확인]()

  - URL의 모양새인 경우, 컨텐츠를 등록하는 POST 요청을 비동기로 날립니다.

  

### 4.3. 계수기 기능 - pointWinner(int p) , scoreBoard()  

![](https://zuminternet.github.io/images/portal/post/2019-04-22-ZUM-Pilot-integer/flow_controller.png)

- **요청 처리** :pushpin: [코드 확인](https://github.com/Integerous/goQuality/blob/b2c5e60761b6308f14eebe98ccdb1949de6c4b99/src/main/java/goQuality/integerous/controller/PostRestController.java#L55)

  - Controller에서는 요청을 화면단에서 넘어온 요청을 받고, Service 계층에 로직 처리를 위임합니다.

- **결과 응답** :pushpin: [코드 확인]()

  - Service 계층에서 넘어온 로직 처리 결과(메세지)를 화면단에 응답해줍니다.

  

### 4.4. 점수판 기능 - dispScoreBoard() 

![](https://zuminternet.github.io/images/portal/post/2019-04-22-ZUM-Pilot-integer/flow_service1.png)

- **Http 프로토콜 추가 및 trim()** :pushpin: [코드 확인]()

  - 사용자가 URL 입력 시 Http 프로토콜을 생략하거나 공백을 넣은 경우,  
    올바른 URL이 될 수 있도록 Http 프로토콜을 추가해주고, 공백을 제거해줍니다.

- **URL 접속 확인** :pushpin: [코드 확인]()

  - 화면단에서 모양새만 확인한 URL이 실제 리소스로 연결되는지 HttpUrlConnection으로 테스트합니다.
  - 이 때, 빠른 응답을 위해 Request Method를 GET이 아닌 HEAD를 사용했습니다.
  - (HEAD 메소드는 GET 메소드의 응답 결과의 Body는 가져오지 않고, Header만 확인하기 때문에 GET 메소드에 비해 응답속도가 빠릅니다.)

  ![](https://zuminternet.github.io/images/portal/post/2019-04-22-ZUM-Pilot-integer/flow_service2.png)

- **Jsoup 이미지, 제목 파싱** :pushpin: [코드 확인]()

  - URL 접속 확인결과 유효하면 Jsoup을 사용해서 입력된 URL의 이미지와 제목을 파싱합니다.
  - 이미지는 Open Graphic Tag를 우선적으로 파싱하고, 없을 경우 첫 번째 이미지와 제목을 파싱합니다.
  - 컨텐츠에 이미지가 없을 경우, 미리 설정해둔 기본 이미지를 사용하고, 제목이 없을 경우 생략합니다.

  


### 4.5. 최종 결과 출력 - writeTennisResult() 

![](https://zuminternet.github.io/images/portal/post/2019-04-22-ZUM-Pilot-integer/flow_repo.png)

- **컨텐츠 저장** :pushpin: [코드 확인]()
  - URL 유효성 체크와 이미지, 제목 파싱이 끝난 컨텐츠는 DB에 저장합니다.
  - 저장된 컨텐츠는 다시 Repository - Service - Controller를 거쳐 화면단에 송출됩니다.

</div>
</details>

</br>

## 5. 핵심 트러블 슈팅

### 5.1. 컨텐츠 필터와 페이징 처리 문제

- 저는 이 서비스가 페이스북이나 인스타그램 처럼 가볍게, 자주 사용되길 바라는 마음으로 개발했습니다.  
  때문에 페이징 처리도 무한 스크롤을 적용했습니다.

- 하지만 [무한스크롤, 페이징 혹은 “더보기” 버튼? 어떤 걸 써야할까](https://cyberx.tistory.com/82) 라는 글을 읽고 무한 스크롤의 단점들을 알게 되었고,  
  다양한 기준(카테고리, 사용자, 등록일, 인기도)의 게시물 필터 기능을 넣어서 이를 보완하고자 했습니다.

- 그런데 게시물이 필터링 된 상태에서 무한 스크롤이 동작하면,  
  필터링 된 게시물들만 DB에 요청해야 하기 때문에 아래의 **기존 코드** 처럼 각 필터별로 다른 Query를 날려야 했습니다.

<details>
<summary><b>기존 코드</b></summary>
<div markdown="1">


~~~java
/**
 * 게시물 Top10 (기준: 댓글 수 + 좋아요 수)
 * @return 인기순 상위 10개 게시물
 */
public Page<PostResponseDto> listTopTen() {

    PageRequest pageRequest = PageRequest.of(0, 10, Sort.Direction.DESC, "rankPoint", "likeCnt");
    return postRepository.findAll(pageRequest).map(PostResponseDto::new);
}

/**
 * 게시물 필터 (Tag Name)
 * @param tagName 게시물 박스에서 클릭한 태그 이름
 * @param pageable 페이징 처리를 위한 객체
 * @return 해당 태그가 포함된 게시물 목록
 */
public Page<PostResponseDto> listFilteredByTagName(String tagName, Pageable pageable) {

    return postRepository.findAllByTagName(tagName, pageable).map(PostResponseDto::new);
}

// ... 게시물 필터 (Member) 생략 

/**
 * 게시물 필터 (Date)
 * @param createdDate 게시물 박스에서 클릭한 날짜
 * @return 해당 날짜에 등록된 게시물 목록
 */
public List<PostResponseDto> listFilteredByDate(String createdDate) {

    // 등록일 00시부터 24시까지
    LocalDateTime start = LocalDateTime.of(LocalDate.parse(createdDate), LocalTime.MIN);
    LocalDateTime end = LocalDateTime.of(LocalDate.parse(createdDate), LocalTime.MAX);

    return postRepository
                    .findAllByCreatedAtBetween(start, end)
                    .stream()
                    .map(PostResponseDto::new)
                    .collect(Collectors.toList());
    }
~~~

</div>
</details>

- 이 때 카테고리(tag)로 게시물을 필터링 하는 경우,  
  각 게시물은 최대 3개까지의 카테고리(tag)를 가질 수 있어 해당 카테고리를 포함하는 모든 게시물을 질의해야 했기 때문에  
- 아래 **개선된 코드**와 같이 QueryDSL을 사용하여 다소 복잡한 Query를 작성하면서도 페이징 처리를 할 수 있었습니다.

<details>
<summary><b>개선된 코드</b></summary>
<div markdown="1">


~~~java
/**
 * 게시물 필터 (Tag Name)
 */
@Override
public Page<Post> findAllByTagName(String tagName, Pageable pageable) {

    QueryResults<Post> results = queryFactory
            .selectFrom(post)
            .innerJoin(postTag)
                .on(post.idx.eq(postTag.post.idx))
            .innerJoin(tag)
                .on(tag.idx.eq(postTag.tag.idx))
            .where(tag.name.eq(tagName))
            .orderBy(post.idx.desc())
                .limit(pageable.getPageSize())
                .offset(pageable.getOffset())
            .fetchResults();

    return new PageImpl<>(results.getResults(), pageable, results.getTotal());
}
~~~

</div>
</details>

</br>

## 6. 그 외 트러블 슈팅

<details>
<summary>npm run dev 실행 오류</summary>
<div markdown="1">


- Webpack-dev-server 버전을 3.0.0으로 다운그레이드로 해결
- `$ npm install —save-dev webpack-dev-server@3.0.0`

</div>
</details>

<details>
<summary>vue-devtools 크롬익스텐션 인식 오류 문제</summary>
<div markdown="1">


  - main.js 파일에 `Vue.config.devtools = true` 추가로 해결
  - [https://github.com/vuejs/vue-devtools/issues/190](https://github.com/vuejs/vue-devtools/issues/190)

</div>
</details>

<details>
<summary>ElementUI input 박스에서 `v-on:keyup.enter="메소드명"`이 정상 작동 안하는 문제</summary>
<div markdown="1">


  - `v-on:keyup.enter.native=""` 와 같이 .native 추가로 해결

</div>
</details>

<details>
<summary> Post 목록 출력시에 Member 객체 출력 에러 </summary>
<div markdown="1">


  - 에러 메세지(500에러)
    - No serializer found for class org.hibernate.proxy.pojo.javassist.JavassistLazyInitializer and no properties discovered to create BeanSerializer (to avoid exception, disable SerializationConfig.SerializationFeature.FAIL_ON_EMPTY_BEANS)
  - 해결
    - Post 엔티티에 @ManyToOne 연관관계 매핑을 LAZY 옵션에서 기본(EAGER)옵션으로 수정

</div>
</details>
    

<details>
<summary> 프로젝트를 git init으로 생성 후 발생하는 npm run dev/build 오류 문제 </summary>
<div markdown="1">


  ```jsx
    $ npm run dev
    npm ERR! path C:\Users\integer\IdeaProjects\pilot\package.json
    npm ERR! code ENOENT
    npm ERR! errno -4058
    npm ERR! syscall open
    npm ERR! enoent ENOENT: no such file or directory, open 'C:\Users\integer\IdeaProjects\pilot\package.json'
    npm ERR! enoent This is related to npm not being able to find a file.
    npm ERR! enoent

    npm ERR! A complete log of this run can be found in:
    npm ERR!     C:\Users\integer\AppData\Roaming\npm-cache\_logs\2019-02-25T01_23_19_131Z-debug.log
  ```

  - 단순히 npm run dev/build 명령을 입력한 경로가 문제였다.

</div>
</details>    

<details>
<summary> 태그 선택후 등록하기 누를 때 `object references an unsaved transient instance - save the transient instance before flushing` 오류</summary>
<div markdown="1">


  - Post 엔티티의 @ManyToMany에 영속성 전이(cascade=CascadeType.ALL) 추가
    - JPA에서 Entity를 저장할 때 연관된 모든 Entity는 영속상태여야 한다.
    - CascadeType.PERSIST 옵션으로 부모와 자식 Enitity를 한 번에 영속화할 수 있다.
    - 참고
      - [https://stackoverflow.com/questions/2302802/object-references-an-unsaved-transient-instance-save-the-transient-instance-be/10680218](https://stackoverflow.com/questions/2302802/object-references-an-unsaved-transient-instance-save-the-transient-instance-be/10680218)

</div>
</details>    

<details>
<summary> JSON: Infinite recursion (StackOverflowError)</summary>
<div markdown="1">


  - @JsonIgnoreProperties 사용으로 해결
    - 참고
      - [http://springquay.blogspot.com/2016/01/new-approach-to-solve-json-recursive.html](http://springquay.blogspot.com/2016/01/new-approach-to-solve-json-recursive.html)
      - [https://stackoverflow.com/questions/3325387/infinite-recursion-with-jackson-json-and-hibernate-jpa-issue](https://stackoverflow.com/questions/3325387/infinite-recursion-with-jackson-json-and-hibernate-jpa-issue)

</div>
</details>  
    

<details>
<summary> H2 접속문제</summary>
<div markdown="1">


  - H2의 JDBC URL이 jdbc:h2:~/test 으로 되어있으면 jdbc:h2:mem:testdb 으로 변경해서 접속해야 한다.
        

</div>
</details> 
    

<details>
<summary> 컨텐츠수정 모달창에서 태그 셀렉트박스 드랍다운이 뒤쪽에 보이는 문제</summary>
<div markdown="1">


   - ElementUI의 Global Config에 옵션 추가하면 해결
     - main.js 파일에 `Vue.us(ElementUI, { zIndex: 9999 });` 옵션 추가(9999 이하면 안됌)
   - 참고
     - [https://element.eleme.io/#/en-US/component/quickstart#global-config](https://element.eleme.io/#/en-US/component/quickstart#global-config)

</div>
</details> 

<details>
<summary> HTTP delete Request시 개발자도구의 XHR(XMLHttpRequest )에서 delete요청이 2번씩 찍히는 이유</summary>
<div markdown="1">


  - When you try to send a XMLHttpRequest to a different domain than the page is hosted, you are violating the same-origin policy. However, this situation became somewhat common, many technics are introduced. CORS is one of them.

      In short, server that you are sending the DELETE request allows cross domain requests. In the process, there should be a **preflight** call and that is the **HTTP OPTION** call.

      So, you are having two responses for the **OPTION** and **DELETE** call.

      see [MDN page for CORS](https://developer.mozilla.org/en-US/docs/Web/HTTP/Access_control_CORS).

    - 출처 : [https://stackoverflow.com/questions/35808655/why-do-i-get-back-2-responses-of-200-and-204-when-using-an-ajax-call-to-delete-o](https://stackoverflow.com/questions/35808655/why-do-i-get-back-2-responses-of-200-and-204-when-using-an-ajax-call-to-delete-o)

</div>
</details> 

<details>
<summary> 이미지 파싱 시 og:image 경로가 달라서 제대로 파싱이 안되는 경우</summary>
<div markdown="1">


  - UserAgent 설정으로 해결
      - [https://www.javacodeexamples.com/jsoup-set-user-agent-example/760](https://www.javacodeexamples.com/jsoup-set-user-agent-example/760)
      - [http://www.useragentstring.com/](http://www.useragentstring.com/)

</div>
</details> 
    

<details>
<summary> 구글 로그인으로 로그인한 사용자의 정보를 가져오는 방법이 스프링 2.0대 버전에서 달라진 것</summary>
<div markdown="1">


  - 1.5대 버전에서는 Controller의 인자로 Principal을 넘기면 principal.getName(0에서 바로 꺼내서 쓸 수 있었는데, 2.0대 버전에서는 principal.getName()의 경우 principal 객체.toString()을 반환한다.

    - 1.5대 버전에서 principal을 사용하는 경우
    - 아래와 같이 사용했다면,

    ```jsx
    @RequestMapping("/sso/user")
    @SuppressWarnings("unchecked")
    public Map<String, String> user(Principal principal) {
        if (principal != null) {
            OAuth2Authentication oAuth2Authentication = (OAuth2Authentication) principal;
            Authentication authentication = oAuth2Authentication.getUserAuthentication();
            Map<String, String> details = new LinkedHashMap<>();
            details = (Map<String, String>) authentication.getDetails();
            logger.info("details = " + details);  // id, email, name, link etc.
            Map<String, String> map = new LinkedHashMap<>();
            map.put("email", details.get("email"));
            return map;
        }
        return null;
    }
    ```

    - 2.0대 버전에서는
    - 아래와 같이 principal 객체의 내용을 꺼내 쓸 수 있다.

    ```jsx
    UsernamePasswordAuthenticationToken token =
                    (UsernamePasswordAuthenticationToken) SecurityContextHolder
                            .getContext().getAuthentication();
            Map<String, Object> map = (Map<String, Object>) token.getPrincipal();
    
            String email = String.valueOf(map.get("email"));
            post.setMember(memberRepository.findByEmail(email));
    ```

</div>
</details> 
    

<details>
<summary> 랭킹 동점자 처리 문제</summary>
<div markdown="1">


  - PageRequest의 Sort부분에서 properties를 "rankPoint"를 주고 "likeCnt"를 줘서 댓글수보다 좋아요수가 우선순위 갖도록 설정.
  - 좋아요 수도 똑같다면..........
        

</div>
</details> 
    
</br>

## 6. 회고 / 느낀점

>프로젝트 개발 회고 글: https://zuminternet.github.io/ZUM-Pilot-integer/
