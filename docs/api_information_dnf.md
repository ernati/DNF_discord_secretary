관련 링크
https://developers.neople.co.kr/contents/apiDocs/df

01. 서버 정보/df/servers 
요청변수	유형	설명	필수여부	기본값	최대값
Request URL

https://api.neople.co.kr/df/servers?apikey=wif1LHXm6V2yLk1vgV8CNtlL3Nvhhcec
02. 캐릭터 검색/df/servers/:serverId/characters 
참고 사항
캐릭터 이미지 URL : https://img-api.neople.co.kr/df/servers/<serverId>/characters/<characterId>?zoom=<zoom>
※ zoom 요청 변수를 통해서 1 ~ 3까지 사이즈 조절 가능
※ 잘못되었거나 불필요한 요청 변수 추가 시 zoom 요청 변수 기본 값(1) 처리

요청변수	유형	설명	필수여부	기본값	최대값
serverId	String	서버 아이디 : 해당 서버군 검색
all : 전체 서버군 통합 검색	Y		
characterName	String	캐릭터 명칭 (URL 인코딩 필요)	Y		
jobId	String	캐릭터 직업 고유 코드			
jobGrowId	String	캐릭터 전직 직업 고유 코드 (jobId 필요)			
isAllJobGrow	Boolean	jobGrowId 입력 시 연계되는 전체 전직 포함 조회		false	
wordType	String	검색타입
동일 단어(match), 전문 검색(full)
※ full의 경우 최소 2자에서 최대 12자까지 이용 가능		match	
limit	Integer	반환 Row 수		10	200
Request URL

https://api.neople.co.kr/df/servers/<serverId>/characters?characterName=<characterName>&jobId=<jobId>&jobGrowId=<jobGrowId>&isAllJobGrow=<isAllJobGrow>&limit=<limit>&wordType=<wordType>&apikey=wif1LHXm6V2yLk1vgV8CNtlL3Nvhhcec
03. 캐릭터 `기본 정보` 조회/df/servers/:serverId/characters/:characterId 
참고 사항
캐릭터 이미지 URL : https://img-api.neople.co.kr/df/servers/<serverId>/characters/<characterId>?zoom=<zoom>
※ zoom 요청 변수를 통해서 1 ~ 3까지 사이즈 조절 가능
※ 잘못된 파라미터 또는 불필요한 파라미터 추가 시 zoom 파라미터 기본 값(1) 처리

요청변수	유형	설명	필수여부	기본값
serverId	String	서버 아이디	Y	
characterId	String	캐릭터 고유 코드	Y	
Request URL

https://api.neople.co.kr/df/servers/<serverId>/characters/<characterId>?apikey=wif1LHXm6V2yLk1vgV8CNtlL3Nvhhcec
04. 캐릭터 `타임라인 정보` 조회/df/servers/:serverId/characters/:characterId/timeline 
참고 사항
타임라인 코드 다중 입력 시 콤마(,)를 이용해서 구분 처리
  ex) /timeline?code=101,102,103

startDate, endDate 요청 변수 사용 예시
  ex) /timeline?startDate=20180901T0000&endDate=20180930T2359
          /timeline?startDate=2018-09-01 00:00&endDate=2018-09-30 23:59
  ※ 기간 검색 요청 시 하나의 파라미터(startDate, endDate)라도 누락 될 경우 검색이 불가능합니다.
  ※ 다양한 Date Type을 지원하지만, 상황에 따라 변경될 수 있으므로 예시 Date Type을 이용 부탁드립니다.
  ※ 초 단위 설정의 경우 startDate : 00초, endDate : 59초로 처리됩니다.
  ※ 기간 설정은 최대 90일까지 가능합니다.
  ※ 2017.09.21 타임라인 서비스 이후 데이터만 조회 가능합니다.

next 요청변수 사용 예시
  ex) /timeline?next=<next>&apikey=<apikey>
  ※ next 사용 시 limit, code, startDate, endDate등 요청변수는 최초 조회 기준으로 적용됩니다.
요청변수	유형	설명	필수여부	기본값	최대값
serverId	String	서버 아이디	Y		
characterId	String	캐릭터 고유 코드	Y		
startDate	Date	검색 시작일		현재시간 기준 30일전	
endDate	Date	검색 종료일		현재시간	
limit	Integer	반환 Row 수		10	100
code	String	타임라인 코드			
next	String	다음 데이터 조회			
Request URL

https://api.neople.co.kr/df/servers/<serverId>/characters/<characterId>/timeline?limit=<limit>&code=<code>&startDate=<startDate>&endDate=<endDate>&next=<next>&apikey=wif1LHXm6V2yLk1vgV8CNtlL3Nvhhcec
05.캐릭터 `능력치 정보` 조회/df/servers/:serverId/characters/:characterId/status 
참고 사항
최근 1년 이내 접속한 캐릭터에 한해서만 제공 됩니다.
능력치 정보의 경우 최근 인게임 접속 기준으로 갱신되며, 캐릭터 접속 환경 및 인게임 업데이트 간 오차 또는 미 제공될 수 있습니다.

요청변수	유형	설명	필수여부	기본값
serverId	String	서버 아이디	Y	
characterId	String	캐릭터 고유 코드	Y	
Request URL

https://api.neople.co.kr/df/servers/<serverId>/characters/<characterId>/status?apikey=wif1LHXm6V2yLk1vgV8CNtlL3Nvhhcec
06. 캐릭터 `장착 장비` 조회/df/servers/:serverId/characters/:characterId/equip/equipment 
요청변수	유형	설명	필수여부	기본값
serverId	String	서버 아이디	Y	
characterId	String	캐릭터 고유 코드	Y	
Request URL

https://api.neople.co.kr/df/servers/<serverId>/characters/<characterId>/equip/equipment?apikey=wif1LHXm6V2yLk1vgV8CNtlL3Nvhhcec
07. 캐릭터 `장착 아바타` 조회/df/servers/:serverId/characters/:characterId/equip/avatar 
요청변수	유형	설명	필수여부	기본값
serverId	String	서버 아이디	Y	
characterId	String	캐릭터 고유 코드	Y	
Request URL

https://api.neople.co.kr/df/servers/<serverId>/characters/<characterId>/equip/avatar?apikey=wif1LHXm6V2yLk1vgV8CNtlL3Nvhhcec
08. 캐릭터 `장착 크리쳐` 조회/df/servers/:serverId/characters/:characterId/equip/creature 
요청변수	유형	설명	필수여부	기본값
serverId	String	서버 아이디	Y	
characterId	String	캐릭터 고유 코드	Y	
Request URL

https://api.neople.co.kr/df/servers/<serverId>/characters/<characterId>/equip/creature?apikey=wif1LHXm6V2yLk1vgV8CNtlL3Nvhhcec
09. 캐릭터 `장착 서약` 조회/df/servers/:serverId/characters/:characterId/equip/oath 
요청변수	유형	설명	필수여부	기본값
serverId	String	서버 아이디	Y	
characterId	String	캐릭터 고유 코드	Y	
Request URL

https://api.neople.co.kr/df/servers/<serverId>/characters/<characterId>/equip/oath?apikey=wif1LHXm6V2yLk1vgV8CNtlL3Nvhhcec
10. 캐릭터 `안개 융화` 조회/df/servers/:serverId/characters/:characterId/equip/mist-assimilation 
요청변수	유형	설명	필수여부	기본값
serverId	String	서버 아이디	Y	
characterId	String	캐릭터 고유 코드	Y	
Request URL

https://api.neople.co.kr/df/servers/<serverId>/characters/<characterId>/equip/mist-assimilation?apikey=wif1LHXm6V2yLk1vgV8CNtlL3Nvhhcec
11. 캐릭터 `스킬 스타일` 조회/df/servers/:serverId/characters/:characterId/skill/style 
참고 사항
아이템 및 장비를 통한 스킬 강화 제외 입니다.

요청변수	유형	설명	필수여부	기본값
serverId	String	서버 아이디	Y	
characterId	String	캐릭터 고유 코드	Y	
Request URL

https://api.neople.co.kr/df/servers/<serverId>/characters/<characterId>/skill/style?apikey=wif1LHXm6V2yLk1vgV8CNtlL3Nvhhcec
12. 캐릭터 `버프 스킬 강화 장착 장비` 조회/df/servers/:serverId/characters/:characterId/skill/buff/equip/equipment 
참고 사항
버프 스킬 상세 수치 정보의 경우 최근 인게임 접속 기준으로 제공되며, 캐릭터 접속 상황에 따라서 오차 또는 미제공 될 수 있습니다.

요청변수	유형	설명	필수여부	기본값
serverId	String	서버 아이디	Y	
characterId	String	캐릭터 고유 코드	Y	
Request URL

https://api.neople.co.kr/df/servers/<serverId>/characters/<characterId>/skill/buff/equip/equipment?apikey=wif1LHXm6V2yLk1vgV8CNtlL3Nvhhcec
13. 캐릭터 `버프 스킬 강화 장착 아바타` 조회/df/servers/:serverId/characters/:characterId/skill/buff/equip/avatar 
참고 사항
버프 스킬 상세 수치 정보의 경우 최근 인게임 접속 기준으로 제공되며, 캐릭터 접속 상황에 따라서 오차 또는 미제공 될 수 있습니다.

요청변수	유형	설명	필수여부	기본값
serverId	String	서버 아이디	Y	
characterId	String	캐릭터 고유 코드	Y	
Request URL

https://api.neople.co.kr/df/servers/<serverId>/characters/<characterId>/skill/buff/equip/avatar?apikey=wif1LHXm6V2yLk1vgV8CNtlL3Nvhhcec
14. 캐릭터 `버프 스킬 강화 장착 크리처` 조회/df/servers/:serverId/characters/:characterId/skill/buff/equip/creature 
참고 사항
버프 스킬 상세 수치 정보의 경우 최근 인게임 접속 기준으로 제공되며, 캐릭터 접속 상황에 따라서 오차 또는 미제공 될 수 있습니다.

요청변수	유형	설명	필수여부	기본값
serverId	String	서버 아이디	Y	
characterId	String	캐릭터 고유 코드	Y	
Request URL

https://api.neople.co.kr/df/servers/<serverId>/characters/<characterId>/skill/buff/equip/creature?apikey=wif1LHXm6V2yLk1vgV8CNtlL3Nvhhcec
15. 캐릭터 명성 검색/df/servers/:serverId/characters-fame 
참고 사항
최근 90일 이내 접속한 110 레벨 이상 캐릭터만 검색 가능합니다.
최대 2,000 범위내에서만 검색 가능합니다
※ minFame : 50000, maxFame : 60000 요청 시 minFame : 58000, maxFame : 60000으로 변경되어 검색 결과 제공

요청변수	유형	설명	필수여부	기본값	최대값
serverId	String	서버 아이디 : 해당 서버군 검색
all : 전체 서버군 통합 검색	Y		
minFame	Integer	명성 구간 최소값		maxFame - 2000	
maxFame	Integer	명성 구간 최대값		게임 내 가장 높은 명성
(55,000 이상)	
jobId	String	캐릭터 직업 고유 코드			
jobGrowId	String	캐릭터 전직 직업 고유 코드(jobId 필요)			
isAllJobGrow	Boolean	jobGrowId 입력 시 연계되는 전체 전직 포함 조회		false	
isBuff	Boolean	버퍼만 조회(true), 딜러만 조회(false), 전체 조회(미 입력)			
limit	Integer	반환 Row 수		10	200
Request URL

https://api.neople.co.kr/df/servers/<serverId>/characters-fame?minFame=<minFame>&maxFame=<maxFame>&jobId=<jobId>&jobGrowId=<jobGrowId>&isAllJobGrow=<isAllJobGrow>&isBuff=<isBuff>&limit=<limit>&apikey=wif1LHXm6V2yLk1vgV8CNtlL3Nvhhcec
16. 경매장 등록 아이템 검색/df/auction 
참고 사항
검색 변수 : itemId / itemName / itemIds 중 한가지의 파라미터는 필수로 입력 하셔야 합니다.
정렬 : sort가 정의되어 있지 않을 경우 기본적으로 auctionNo에 대해서만 오름차순(asc)으로 정렬됩니다.

요청변수	하위변수	유형	설명	필수여부	기본값	최대값
limit		Integer	반환 Row 수		10	400
sort=			정렬 관련 요청변수			
unitPrice	String	가격별 정렬
오름차순(asc), 내림차순(desc)			
reinforce	String	등급별 정렬
오름차순(asc), 내림차순(desc)			
auctionNo	String	등록순서 정렬
오름차순(asc), 내림차순(desc)			
itemId		String	아이템 고유 코드	Y		
itemName		String	아이템 명칭 (URL 인코딩 필요)	Y		
itemIds		String	아이템 고유 코드
쉼표(,)를 통한 구분 값 처리 (최대10개)	Y		
wordType		String	검색타입
동일 단어(match), 앞 단어 검색(front), 전문 검색(full)		match	
wordShort		Boolean	아이템명 단축어 사용여부 사용(true), 미사용(false)		true	
q=			검색 관련 요청변수			
minLevel	Integer	최소 장착 레벨			
maxLevel	Integer	최대 장착 레벨			
rarity	String	아이템 레어리티 (URL 인코딩 필요)			
reinforceTypeId	String	강화타입(URL 인코딩 필요)
강화, 증폭, 개조			
minReinforce	Integer	최소 강화 수치			
maxReinforce	Integer	최대 강화 수치			
minRefine	Integer	최소 제련 수치			
maxRefine	Integer	최대 제련 수치			
minFame	Integer	최소 모험가 명성			
maxFame	Integer	최대 모험가 명성			
Request URL

https://api.neople.co.kr/df/auction?itemName=<itemName>&wordType=<wordType>&wordShort=<wordShort>&q=minLevel:<minLevel>,maxLevel:<maxLevel>,rarity:<rarity>,reinforceTypeId:<reinforceTypeId>,minReinforce:<minReinforce>,maxReinforce:<maxReinforce>,minRefine:<minRefine>,maxRefine:<maxRefine>,minFame:<minFame>,maxFame:<maxFame>&sort=unitPrice:<unitPrice>,reinforce:<reinforce>,auctionNo:<auctionNo>&limit=<limit>&apikey=wif1LHXm6V2yLk1vgV8CNtlL3Nvhhcec
17. 경매장 등록 아이템 조회/df/auction/:auctionNo 
요청변수	유형	설명	필수여부	기본값
auctionNo	Int	경매장 등록 번호	Y	
Request URL

https://api.neople.co.kr/df/auction/<auctionNo>?apikey=wif1LHXm6V2yLk1vgV8CNtlL3Nvhhcec
18. 경매장 시세 검색/df/auction-sold 
참고 사항
검색 변수 : itemId / itemName / itemIds 중 한가지의 파라미터는 필수로 입력 하셔야 합니다.
최근 100개의 거래 내역 혹은 최대 1개월 전의 거래 내역에 대해서만 제공합니다.
레벨, 레어리티등 상세 조건에 대한 검색 기능은 제공 하지 않습니다.

요청변수	하위변수	유형	설명	필수여부	기본값	최대값
limit		Integer	반환 Row 수		10	100
itemId		String	아이템 고유 코드	Y		
itemIds		String	아이템 고유 코드
쉼표(,)를 통한 구분 값 처리 (최대10개)	Y		
itemName		String	아이템 명칭 (URL 인코딩 필요)	Y		
wordType		String	검색타입
동일 단어(match), 앞 단어 검색(front), 전문 검색(full)		match	
wordShort		Boolean	아이템명 단축어 사용여부 사용(true), 미사용(false)		true	
Request URL

https://api.neople.co.kr/df/auction-sold?itemName=<itemName>&wordType=<wordType>&wordShort=<wordShort>&limit=<limit>&apikey=wif1LHXm6V2yLk1vgV8CNtlL3Nvhhcec
19. 아바타 마켓 상품 검색/df/avatar-market/sale 
참고 사항
hashtag 정보는 "아바타 마켓 해시태그 조회 API"를 통해서 확인 가능합니다.

요청변수	하위변수	유형	설명	필수여부	기본값	최대값
limit		Integer	반환 Row 수		10	50
sort=			정렬 관련 요청변수			
price	String	가격별 정렬
오름차순(asc), 내림차순(desc)			
goodsNo	String	등록순서 정렬
오름차순(asc), 내림차순(desc)			
hashtag		String	해시태그 구분자 (,)로 구성된 문자열(URL 인코딩 필요)			
title		String	아바타 마켓 등록 제목 (URL 인코딩 필요)			
wordType		String	검색타입
동일 단어(match), 앞 단어 검색(front), 전문 검색(full)		match	
q=			검색 관련 요청변수			
jobId	String	캐릭터 직업 고유 코드			
emblemCode	Integer	엠블렘 코드			
avatarSet	String	아바타 세트 여부
세트(true), 일반(false)			
avatarRarity	String	아바타 레어리티
상급, 레어, 혼합 (URL 인코딩 필요)			
minPrice	Integer	최소 판매 금액			
maxPrice	Integer	최대 판매 금액			
minAvatarCount	Integer	최소 아바타 장착 갯수			
maxAvatarCount	Integer	최대 아바타 장착 갯수			
Request URL

https://api.neople.co.kr/df/avatar-market/sale?hashtag=<hashtag>&title=<title>&wordType=<wordType>&limit=<limit>&q=jobId:<jobid>,emblemCode:<emblemCode>,avatarSet:<avatarSet>,avatarRarity:<avatarRarity>&sort=price:<price>,goodsNo:<goodsNo>&apikey=wif1LHXm6V2yLk1vgV8CNtlL3Nvhhcec
20. 아바타 마켓 상품 조회/df/avatar-market/sale/:goodsNo 
요청변수	하위변수	유형	설명	필수여부	기본값	최대값
goodsNo		Integer	아바타 마켓 등록 번호	Y		
Request URL

https://api.neople.co.kr/df/avatar-market/sale/<goodsNo>?apikey=wif1LHXm6V2yLk1vgV8CNtlL3Nvhhcec
21. 아바타 마켓 상품 시세 검색/df/avatar-market/sold 
참고 사항
hashtag 정보는 "아바타 마켓 해시태그 조회 API"를 통해서 확인 가능합니다.

요청변수	하위변수	유형	설명	필수여부	기본값	최대값
limit		Integer	반환 Row 수		10	50
sort=			정렬 관련 요청변수			
price	String	가격별 정렬
오름차순(asc), 내림차순(desc)			
goodsNo	String	등록순서 정렬
오름차순(asc), 내림차순(desc)			
hashtag		String	해시태그 구분자 (,)로 구성된 문자열(URL 인코딩 필요)			
title		String	아바타 마켓 등록 제목 (URL 인코딩 필요)			
wordType		String	검색타입
동일 단어(match), 앞 단어 검색(front), 전문 검색(full)		match	
q=			검색 관련 요청변수			
jobId	String	캐릭터 직업 고유 코드			
emblemCode	Integer	엠블렘 코드			
avatarSet	String	아바타 세트 여부
세트(true), 일반(false)			
avatarRarity	String	아바타 레어리티
상급, 레어, 혼합 (URL 인코딩 필요)			
minPrice	Integer	최소 판매 금액			
maxPrice	Integer	최대 판매 금액			
minAvatarCount	Integer	최소 아바타 장착 갯수			
maxAvatarCount	Integer	최대 아바타 장착 갯수			
Request URL

https://api.neople.co.kr/df/avatar-market/sold?hashtag=<hashtag>&title=<title>&wordType=<wordType>&limit=<limit>&q=jobId:<jobid>,emblemCode:<emblemCode>,avatarSet:<avatarSet>,avatarRarity:<avatarRarity>&sort=price:<price>,goodsNo:<goodsNo>&apikey=wif1LHXm6V2yLk1vgV8CNtlL3Nvhhcec
22. 아바타 마켓 상품 시세 조회/df/avatar-market/sold/:goodsNo 
요청변수	하위변수	유형	설명	필수여부	기본값	최대값
goodsNo		Integer	아바타 마켓 등록 번호	Y		
Request URL

https://api.neople.co.kr/df/avatar-market/sold/<goodsNo>?apikey=wif1LHXm6V2yLk1vgV8CNtlL3Nvhhcec
23. 아바타 마켓 해시태그 조회/df/avatar-market/hashtag 
요청변수	하위변수	유형	설명	필수여부	기본값	최대값
hashtagType		String	해시태그타입
카테고리(category), 분위기(mood)			
Request URL

https://api.neople.co.kr/df/avatar-market/hashtag?hashtagType=<hashtagType>&apikey=wif1LHXm6V2yLk1vgV8CNtlL3Nvhhcec
24. 아이템 검색/df/items 
참고 사항
현재 인게임에서 획득 가능한 아이템의 경우만 검색 가능합니다.
아이템 이미지 URL : https://img-api.neople.co.kr/df/items/<itemId>

요청변수	하위변수	유형	설명	필수여부	기본값	최대값
limit		Integer	반환 Row 수		10	30
itemName		String	아이템 명칭(URL 인코딩 필요)
itemName 또는 hashtag 필수 입력	Y		
hashtag		String	해시태그 (URL 인코딩 필요)
쉼표(,)를 통한 구분 값 처리	Y		
wordType		String	검색타입
동일 단어(match), 앞 단어 검색(front), 전문 검색(full)
※ full의 경우 최소 2자에서 최대 12자까지 이용 가능		match	
q=						
minLevel	Integer	최소 장착 레벨			
maxLevel	Integer	최대 장착 레벨			
rarity	String	아이템 레어리티 (URL 인코딩 필요)			
Request URL

https://api.neople.co.kr/df/items?itemName=<itemName>&wordType=<wordType>&hashtag=<hashtag>,<hashtag>&q=minLevel:<minLevel>,maxLevel:<maxLevel>,rarity:<rarity>&limit=<limit>&apikey=wif1LHXm6V2yLk1vgV8CNtlL3Nvhhcec
25. 아이템 상세 정보 조회/df/items/:itemId 
참고 사항
장비 스탯의 경우, 최상급 100% 기준으로 표시됩니다.
예외적으로 칭호의 경우, 중급 평균 수치로 표시됩니다.
아이템 이미지 URL : https://img-api.neople.co.kr/df/items/<itemId>

talismanInfo buff 컬럼 정보 안내
  - buff 컬럼의 경우 크루세이더(남) "성령의 메이스 스킬의 습득 여부"에 따른 버프 옵션 정보입니다.
  - 크루세이더(여), 인챈트리스의 경우 explain / explainDetail에 포함됩니다.

요청변수	유형	설명	필수여부	기본값
itemId	String	아이템 고유 코드	Y	
Request URL

https://api.neople.co.kr/df/items/<itemId>?apikey=wif1LHXm6V2yLk1vgV8CNtlL3Nvhhcec
26. 아이템 상점 판매 정보 조회/df/items/:itemId/shop 
참고 사항
인게임 백과사전 기준의 상점 판매 95레벨 에픽, 100레벨 이상 유니크, 레전더리, 에픽 장비가 조회 가능 합니다.

요청변수	유형	설명	필수여부	기본값
itemId	String	아이템 고유 코드	Y	
Request URL

https://api.neople.co.kr/df/items/<itemId>/shop?apikey=wif1LHXm6V2yLk1vgV8CNtlL3Nvhhcec
27. 아이템 획득 정보 조회/df/items/:itemId/obtain 
요청변수	유형	설명	필수여부	기본값
itemId	String	아이템 고유 코드	Y	
Request URL

https://api.neople.co.kr/df/items/<itemId>/obtain?apikey=wif1LHXm6V2yLk1vgV8CNtlL3Nvhhcec
28. 다중 아이템 상세 정보 조회/df/multi/items 
참고 사항
아이템 최대 15개 조회 가능합니다.
중복된 아이템 ID 요청 시 중복된 항목은 제거 됩니다.
예시) https://api.neople.co.kr/df/multi/items?itemIds=6ed94ca4a1c10af06f5c79969a1d30e8,2dfaf59a126c85104771d33ecf099e6f

요청변수	하위변수	유형	설명	필수여부	기본값
itemIds		String	아이템 고유 코드
쉼표(,)를 통한 구분 값 처리	Y	
Request URL

https://api.neople.co.kr/df/multi/items?itemIds=<itemId>,<itemId>,<itemId>&apikey=wif1LHXm6V2yLk1vgV8CNtlL3Nvhhcec
29. 아이템 해시태그/df/item-hashtag 
요청변수	유형	설명	필수여부	기본값	최대값
Request URL

https://api.neople.co.kr/df/item-hashtag?apikey=wif1LHXm6V2yLk1vgV8CNtlL3Nvhhcec
30. 세트 아이템 검색/df/setitems 
요청변수	하위변수	유형	설명	필수여부	기본값	최대값
setItemName		String	세트 아이템 명칭, URL 인코딩 하여 사용한다	Y		
limit		Integer	반환 Row 수		10	100
wordType		String	검색타입
동일 단어(match), 앞 단어 검색(front), 전문 검색(full)
※ full의 경우 최소 2자에서 최대 12자까지 이용 가능		match	
Request URL

https://api.neople.co.kr/df/setitems?setItemName=<setItemName>&limit=<limit>&wordType=<wordType>&apikey=wif1LHXm6V2yLk1vgV8CNtlL3Nvhhcec
31. 세트 아이템 상세 정보 조회/df/setitems/:setItemId 
요청변수	유형	설명	필수여부	기본값
setItemId	String	세트 아이템 고유 코드	Y	
Request URL

https://api.neople.co.kr/df/setitems/<setItemId>?apikey=wif1LHXm6V2yLk1vgV8CNtlL3Nvhhcec
32. 다중 세트 아이템 상세 정보 조회/df/multi/setitems 
참고 사항
세트 아이템 최대 15개 조회 가능합니다.
중복된 세트 아이템 ID 요청 시 중복된 항목은 제거 됩니다.
예시) https://api.neople.co.kr/df/multi/setitems?setItemIds=ddaa9c29eb95033a772f40c48b6f429e,861e52afdbbcbcc015188a5d77f30dc1

요청변수	하위변수	유형	설명	필수여부	기본값
setItemIds		String	세트 아이템 고유 코드
쉼표(,)를 통한 구분 값 처리	Y	
Request URL

https://api.neople.co.kr/df/multi/setitems?setItemIds=<setItemId>,<setItemId>,<setItemId>&apikey=wif1LHXm6V2yLk1vgV8CNtlL3Nvhhcec
33. 직업 정보/df/jobs 
요청변수	유형	설명	필수여부	기본값	최대값
Request URL

https://api.neople.co.kr/df/jobs?apikey=wif1LHXm6V2yLk1vgV8CNtlL3Nvhhcec
34. 직업별 스킬 리스트/df/skills/:jobId 
요청변수	유형	설명	필수여부
jobId	String	캐릭터 직업 고유 코드	Y
jobGrowId	String	캐릭터 전직 직업 고유 코드	Y
Request URL

https://api.neople.co.kr/df/skills/<jobId>?jobGrowId=<jobGrowId>&apikey=wif1LHXm6V2yLk1vgV8CNtlL3Nvhhcec
35. 직업별 스킬 상세 정보 조회/df/skills/:jobId/:skillId 
요청변수	유형	설명	필수여부
jobId	String	캐릭터 직업 고유 코드	Y
skillId	String	스킬 고유 코드	Y
Request URL

https://api.neople.co.kr/df/skills/<jobId>/<skillId>?apikey=wif1LHXm6V2yLk1vgV8CNtlL3Nvhhcec
36. 다중 스킬 상세 정보 조회/df/multi/skills/:jobId 
참고 사항
스킬 목록 최대 10개 조회 가능합니다.
중복된 스킬 ID 요청 시 중복된 항목은 제거 됩니다.
예시) https://api.neople.co.kr/df/multi/skills/41f1cdc2ff58bb5fdc287be0db2a8df3?skillIds=fc7a3f4c2852c832a2f20af63d5d212f,3c5604bdbb0240b8f130f59ab40509c3

요청변수	유형	설명	필수여부
jobId	String	캐릭터 직업 고유 코드	Y
skillIds	String	스킬 고유 코드
쉼표(,)를 통한 구분 값 처리	Y
Request URL

https://api.neople.co.kr/df/multi/skills/<jobId>?skillIds=<skillId>,<skillId>,<skillId>&apikey=wif1LHXm6V2yLk1vgV8CNtlL3Nvhhcec