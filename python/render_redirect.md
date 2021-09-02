# render_redirect

----------------------------------------------------

redirect와 render 차이는 redirect는 url로 이동해서 해당하는 views를 불러오고 render는 html을 불러오는게 차이인것 같은데
render에서는 request가 꼭 필요하잖아요 그러면 redirect는 request 안보내도 그냥 보내지는건가요?

<br/> 


render 와 redirect (view에서 이루어지는) 에서는 둘다 request 를 argument 로 받는걸 보실수 있씁니다
<br/> 
일단 url에 등록된 view 면 기본빵 request 객체를 물고 들어오잖아요?
<br/> 
그 의미는 url을 통해 접근된 view 라는 의미에요
<br/> 
그럼 말씀하신대로 view에는 현재 코드상 render template을 하는 뷰와
<br/> 
redirect 하는 뷰가 있어요
<br/> 
render template은 이해하신대로 request 를 받아 template을 랜더링해서 response 를 주는 뷰구요
<br/> 
redirect의 경우가 재밌는데
<br/> 
일단 response 를 주는데 3xx status code 와 함께 클라이언트에 어디로 redirect 해야할지를 알려줘요
<br/> 
이렇게 하는 경우는 redirect 시 response에 위치를 전달해서 ajax로 받아 처리하는 방법이구요
<br/> 
django에서 사용하신 방식은 조금 다른데
<br/> 
클라이언트까지는 안가고
<br/> 
url -> redirect view -> response -> url -> template view -> response 를 거쳐서 돌아가게 되요
<br/> 
아마 django server log 를 보시면
<br/> 
redirect 할 경우 url이 두번찍히는걸 보실수 있을거에요
<br/> 
status code 도 나왔는지 기억이 안나는데
<br/> 
3xx와 200이 나올거에요 이경우
<br/> 
http status 3xx 는 redirect를 의미하기에 response 에 3xx 를 담아 던지거든요
<br/> 
때문에 redirect 는 url을 거쳐 다시 재진입하기때문에
<br/> 
request를 redirect 시 response 로 주지 않아도
<br/> 
template view 에서 request를 다시 물고 들어와요
<br/> 
이해하셨나요?

<br/> 
<br/> 
template view 에서 request를 다시 물고 들어온다 라고 하셔서 알것 같아요 status code가 뭔지 잘 몰라서 찾아봐야겠지만...
<br/> 
그러면 render는 context가 필요할때 쓰고 나머지는 보통 redirect를 쓰나요?

<br/> 
<br/> 
<br/> 
렌더링 같은 경우는 서버 사이드에서 클라이언트 코드를 서빙할 경우
<br/> 
즉 지금같이 메이즈를 만들 때 주로 쓰구요
<br/> 
클라이언트 코드를 서버와는 별개로 서빙하는 방밥도 있어요
<br/> 
주로 클라이언트 프레임워크 리액트나 앵귤러 뷰를 사용 하는 방식이 그러한데
새 항목
<br/> 
이 경우는 서버에서 html을 렌더링은 안해주고 주로 json 을 넘겨줘요
<br/> 
서버에서 클라이언트를 분리한 방식이죠
<br/> 
리다이렉트 같은 경우는 주로 api를 만들다가 모종의 이유로 해당 api를 못 쓰고 다른 api로 바꿔야하나
<br/> 
구버전 api로 계속 유저나 클라이언트 요청들이 들어올때
<br/> 
그럴때 요청을 새로운 버전으로 돌려주기 위해 사용해요