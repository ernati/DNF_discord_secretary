관련 링크
https://developers.neople.co.kr/contents/guide/pages/all#%EB%8D%98%ED%8C%8C-%EC%95%84%EC%9D%B4%ED%85%9C-%EB%A0%88%EC%96%B4%EB%A6%AC%ED%8B%B0

공통 가이드
오픈 API는 게임 내 다양한 정보를 외부 개발자가 쉽게 이용할 수 있도록 제공되는 REST API 서비스입니다.
오픈 API는 개발자들이 활용할 수 있는 리소스(API)를 제공하고 있으며, 게임 내 정보의 범위를 지속적해서 검토 및 추가하고 있습니다.




오픈 API 시작하기
오픈 API를 사용하기 위해서는 회원가입 후 애플리케이션 등록을 하셔야 합니다.
애플리케이션을 등록하면 API Key가 발급되며, API Key를 이용하여 오픈 API 서비스를 이용할 수 있습니다.
오픈 API 이용을 위해서는 API 호출 시 HTTP 헤더 또는 요청 변수에 API Key를 포함해야 합니다.

API 호출 시 요청 제한이 있기 때문에 API Key가 외부로 노출되어 사용에 제한이 가지 않도록 주의하시기 바랍니다.





API 구성


API 호출
Direct URL 호출 예제
https://api.neople.co.kr/df/servers?apikey={APIKey}
CURL 호출 예제
curl --include --request GET 'https://api.neople.co.kr/df/servers?apikey={APIKey}'
Request Header에 API Key값 전송 예제
curl -i -XGET -H 'apikey: <APIKey>' 'https://api.neople.co.kr/df/servers'


API 제한
API 이용 시 요청 가능 수가 제한 되어 있습니다.

애플리케이션 기준 1초당 1,000건입니다.

1초 최대 허용량	1분 최대 허용량	1시간 최대 허용량
1,000건	60,000건	3,600,000건


URL 인코딩
오픈 API에서 일부 요청은 검색 값을 URL 인코딩하여 사용하셔야 합니다.
URL 인코딩이 필요한 요청 변수는 API Doc 에서 확인 가능합니다.
해당 변수들은 한글과 특수문자를 보낼 수 있기 때문에 javascript encodeURIConpoment와 같은 형식의 인코딩 사용을 권장합니다.
(encodeURI 는 일부 특수문자를 인코딩하지 않기 때문에 원하는 결과를 받을 수 없습니다.)

샘플 코드의 경우 언어별 버전에 따라 다를 수 있습니다.

Node.js 인코딩 샘플
const qs = require('querystring');
let itemName = '무색 큐브 조각';
let url = `https://api.neople.co.kr/df/items?&apikey=<APIKey>&itemName=${qs.escape(itemName)}`;
PHP 인코딩 샘플
$encText = rawurlencode("오픈API");

$url = "https://api.neople.co.kr/df/items?itemName=".$encText;
JAVA 인코딩 샘플
private String getUrl(itemName){
    String url = "https://api.neople.co.kr/df/items?itemName=" + encodeURIComponent(itemName);
}

public static String encodeURIComponent(String component)   {     
    String result = null;      

    try {       
        result = URLEncoder.encode(component, "UTF-8") ;     
    catch (UnsupportedEncodingException e) {       
        result = component;     
    }      

    return result;   
}





API 용어 정리


API의 기본
API (Application Programming Interface)
운영체제, 시스템, 애플리케이션, 라이브러리 등을 개발자들이 프로그래밍 작업을 통해 응용 프로그램을 작성할 수 있는 다양한 인터페이스들을 총칭합니다. (예: Window API, Java API, HTML5 API, Android API...)

오픈 API
오픈 API는 API 중에서 게임 내의 컨텐츠를 외부에서 쓸 수 있도록 웹 프로토콜(HTTP)로 호출할 수 있도록 개방(open)한 API를 의미합니다. Neople Developers에서 제공하고 있는 캐릭터, 경매장 정보 등 대부분 API 들은 URL HTTP로 호출할 수 있는 오픈 API에 해당합니다.



API 인증
API 게이트웨이
오픈 API는 대부분 https://api.neople.co.kr 서버를 통하여 호출합니다. 이 서버가 바로 API 게이트웨이 서버이며, 오픈 API 호출이 들어오면 API 호출이 정확한지 판별하고, 인증된 사용자인지, 호출 허용량이 맞는지를 확인해서 실제 각 API 서버를 호출한 다음 결과값을 리턴합니다. 만일 호출이 잘못되었을 경우는 에러 코드와 메시지를 리턴합니다.

API Key
오픈 API를 이용하려면 각 API별로 'API Key'라고 하는 유니크한 텍스트 문자열을 발급받고, 이를 API 호출시 같이 API 게이트웨이 서버로 전송함으로써 인증된 사용자임을 입증합니다.



API 요청
요청 URL (Request URL)
오픈 API를 호출하기 위한 API의 웹 주소(URL)을 의미합니다. 현재 URL 호출은 https://api.neople.co.kr/서비스구분/API 구분 형태로 구성되어 있습니다.

요청 변수 (Request Parameter)
오픈 API를 호출할 때 함께 서버로 전송해야 하는 값들로서, 각 API 명세를 참조하여 요청 변수명이 틀리거나 필수 요청변수가 빠지지 않도록 주의하셔야 합니다.

URL 인코딩
한글이나 특수문자가 요청 변수값에 포함되어 있으면 서버 전송 시 값이 깨지기 때문에 지정된 규칙에 따라 문자 값을 코드값으로 변환해서 전송해야 하며 이를 URL 인코딩이라 합니다. URL 인코딩된 값을 다시 원래의 값으로 변환하는 것을 URL 디코딩이라고 합니다.



HTTP 관련 용어
메소드(Method)
HTTP 프로토콜에서 웹서버가 요청과 응답 데이터를 전송할 때 사전에 약속된 동작 방식으로 W3C에서는 GET, POST를 비롯해 8가지의 방법이 정의되어 있습니다.
오픈 API의 경우 GET 메소드만 지원하며 반드시 GET 메소드를 통해 API를 호출해야 합니다.

HTTP 헤더
HTTP 헤더는 웹서버로 보내는 요청과 요청 데이터를 설명하는 메타 정보 ( 메서드, 요청 URL, http protocol version 등 )들이 들어있습니다. 또한, HTTP 헤더에 추가적으로 지정된 이름과 값을 전송할 수 있습니다. 오픈 API는 기본적으로 API Key를 HTTP 헤더에 포함하여 전송하여 이용할 수 있습니다.

HTTP 상태 코드
API 호출 시 서버에서는 API 호출에 대해서 HTTP 상태 코드값과 함께 응답 내용을 보냅니다. 호출이 정상적으로 이뤄졌을 경우 HTTP 상태 코드는 200으로 전달 되며, 호출 방법이 잘못된 경우에는 400, 401, 404, 500, 503등과 같은 상태 코드를 리턴합니다. 자세한 내용은 HTTP 상태 코드를 참조하시기 바랍니다.






던전앤파이터 게임 정보
던파 서버
던전앤파이터 API에서 공통으로 사용되는 serverId에 대한 설명입니다.

서버 아이디	한글명
anton	안톤
bakal	바칼
cain	카인
casillas	카시야스
diregie	디레지에
hilder	힐더
prey	프레이
siroco	시로코



던파 아이템 레어리티
던전앤파이터 아이템 정보의 레어리티(rarity)에 대한 설명입니다.

레어리티	색상코드
커먼	#FFFFFF
언커먼	#68D5ED
레어	#B36BFF
유니크	#FF00FF
에픽	#FFB400
크로니클	#FF6666
레전더리	#FF7800
신화	-
태초	-



던파 타임라인 코드
던전앤파이터 타임라인 정보의 코드(code)에 대한 설명입니다.

코드	설명
101	캐릭터 생성
102	캐릭터명 변경
103	캐릭터 전직
104	캐릭터 최고 레벨 달성
105	모험단명 변경
201	레이드
202	비탄의 탑 정복
203	절망의 탑 정복
204	(구)마수던전 토벌
205	제국투기장 하드모드 클리어
206	마수던전 토벌
207	핀드워 클리어
208	무덤의 탑 정복
209	레기온 클리어
210	레이드(선발대)
301	결투장 경험치 등급 상승
401	아이템 강화
402	아이템 증폭
403	아이템 재련
404	아이템 개조
405	아이템 새김
406	아이템 계승
407	아이템 단조
501	봉인된 자물쇠 아이템 획득
502	레전더리 획득
503	에컨 레전더리 획득
504	아이템 획득(항아리&상자)
505	아이템 획득(던전 드랍)
506	아이템 획득(조각 교환)
507	아이템 획득(레이드 카드 보상)
508	아이템 획득(상점)
509	아이템 초월 전송(NPC)
510	아이템 교환
511	아이템 획득(업그레이드)
512	권능
513	아이템 획득(던전 카드 보상)
514	아이템 획득(제작서)
515	아이템 초월 수령(NPC)
516	아이템 초월(초월의돌)
517	아이템 융합 분리
518	특수 아이템 획득
519	아이템 변환
520	아이템 획득(장비 제작)
521	아이템 획득(레이드 경매 보상)
550	서약 획득(던전 드랍)
551	서약 획득(레이드 카드 보상)
552	서약 획득(항아리&상자)
553	서약 획득(업그레이드)
554	서약 획득(제작서)
555	서약 획득(무기고)
556	서약 초월(초월의 돌)
557	서약 획득(던전 카드 보상)
601	룬 획득
602	탈리스만 획득



던파 아바타마켓 엠블렘코드
던전앤파이터 아바타 마켓 엠블렘 정보의 코드(code)에 대한 설명입니다.

코드	설명
100	없음
110	빛나는
120	화려한
130	찬란한
999	혼합 엠블렘



던파 컬럼 정보
던전앤파이터 API에서 사용되는 일부 컬럼에 대한 설명입니다.

API	컬럼명	설명
캐릭터	characterId	캐릭터 고유 코드
캐릭터	characterName	캐릭터 명
캐릭터	jobId	캐릭터 직업 고유 코드
캐릭터	jobName	캐릭터 직업 명칭
캐릭터	jobGrowId	캐릭터 전직 직업 고유 코드
캐릭터	jobGrowName	캐릭터 전직 직업 명칭
캐릭터	adventureName	모험단명
캐릭터	fame	캐릭터 모험가 명성
캐릭터	guildId	길드 고유 코드
캐릭터	guildName	길드명
아이템	itemId	아이템 고유 코드
아이템	itemName	아이템명
아이템	itemRarity	아이템 희귀도 등급
아이템	itemTypeId	아이템 타입 고유 코드
아이템	itemType	아이템 타입
아이템	itemTypeDetailId	아이템 세부 타입 고유 코드
아이템	itemTypeDetail	아이템 세부 타입
아이템	itemAbility	아이템 고정 능력치
아이템	itemAvailableLevel	아이템 장착 가능 레벨
아이템	optionAbility	아이템 추가 or 선택 능력치
아이템	setItemId	세트 아이템 고유 코드
아이템	setItemName	세트 아이템 명칭
아이템	setItemOption	세트 아이템 옵션 정보
아이템	setItemInfo	세트 아이템 구성 정보
아이템	fullsetExplain	세트 아이템 전체 착용 부가 옵션에 대한 설명
아이템	setEquipCount	세트 아이템 활성화된 장착 갯수
아이템	slotColor	아이템 슬롯 고유 색상
아이템	slotNo	아이템 슬롯 고유 번호
아이템	slotId	아이템 슬롯 고유 코드
아이템	slotName	아이템 슬롯명
아이템	itemStatus	장비 아이템 수치 정보
아이템	obtainInfo	아이템 획득 정보 (dungeon / shop)
아이템	itemExplain	아이템 부가 옵션에 대한 설명
아이템	itemExplainDetail	아이템 부가 옵션에 대한 상세 설명
아이템	itemFlavorText	아이템 배경담 - 스토리 설명
아이템	itemReinforceSkill	장비 아이템 스킬 강화 정보
아이템	itemGradeName	아이템 등급명
아이템	itemGradeValue	아이템 등급 수치(1 ~ 100%)
아이템	cardInfo	카드 정보
아이템	enchant	카드 업그레이드 수치 정보
아이템	itemBuff	크루세이더, 인챈트리스 전용 옵션
아이템	transformOptionInfo	변환 옵션 정보
아이템	transformOptionInfo.active	옵션 변환 여부
아이템	remodelInfo	개조 아이템 옵션 정보
아이템	remodelInfo.stepInfo	개조 단계별 옵션 정보
아이템	remodelInfo.stepInfo.transformOption	개조 단계별 옵션 정보 중 변환 옵션 여부
아이템	mythologyInfo	신화 아이템 옵션 정보
아이템	sirocoInfo	시로코 융합 아이템 옵션 정보
아이템	aeternaInfo	에테르나 융합 아이템 옵션 정보
아이템	ozmaInfo	오즈마 융합 아이템 옵션 정보
아이템	fixedOption	고정 옵션 정보
아이템	customOption	커스텀 옵션 정보
아이템	asrahanOption	안개신 무기 기억의 성단 옵션 정보
아이템	transfer	옵션 전송 가능 여부 및 특정 옵션 전송 여부
아이템	expRate	경험치 정보
아이템	damage	공격력 증가
아이템	buff	버프력
아이템	hashtag	해시태그
아이템	exaltedInfo	유일 장비 옵션 정보
장착장비	refine	아이템 재련 수치
장착장비	reinforce	아이템 강화 or 증폭 or 개조 수치
장착장비	amplificationName	아이템 증폭 능력치 속성 ( 예 : 차원의 힘 )
장착장비	enchant	마법(보주) 부여
장착장비	darkRevelation	흑천의 무기 검은 권능 발현 정보
장착장비	skin	무기 스킨
장착장비	upgradeInfo	융합 재료 아이템 정보
장착장비	engrave	이명 각인 정보
장착장비	mistGear	미스트 기어 여부
장착장비	refinedMistGear	정제된 미스트 기어 여부
장착장비	pureMistGear	순수한 미스트 기어 여부
장착장비	tune	장비 조율 정보
장착장비	setPoint	아이템 세트 포인트 수치
장착장비	fusionStone	융합석 여부
장착장비	potency	유일 장비 정밀도 정보
장착장비	weaponRelease	장비 개방률 정보
장착장비	adjustedPoint	보정 수치 정보
장착서약	oath.info	장착 서약 정보
장착서약	oath.crystal	서약 결정 정보
장착서약	oath.blessing	서약의 가호 정보
안개융화	mistAssimilation	안개 융화 정보
크리쳐	cooldownTime	스킬 쿨타임
크리쳐	clone	크리쳐 스킨
크리쳐	description	부가 정보
경매장	auctionNo	경매 고유 번호
경매장	count	수량
경매장	regCount	최초등록수량
경매장	upgradeMax	카드/보주의 최대 업그레이드 수치
경매장	seal	아이템의 밀봉 정보 ( count : 소모한 밀봉 횟수, limit : 밀봉 제한 횟수 )
경매장	seller.warning	판매자의 블랙리스트 정보 표기
경매장	currentPrice	즉시 구매 가격
경매장	unitPrice	즉시 구매 개당 가격
경매장	price	현재 입찰 가격(즉시구매만 가능 상품의 경우 -1)
경매장	averagePrice	아이템의 평균 구매 가격
경매장	expireDate	마감 시간
경매장	regDate	등록 시간
경매장	soldDate	판매 시간
경매장	fame	아이템의 모험가 명성
경매장	exchange	아이템의 거래가능 정보 (아바타만 제공)
타임라인	channelNo	채널 번호
타임라인	channelName	채널명
타임라인	dungeonName	던전명
타임라인	monsterName	몬스터명
타임라인	beforeName	변경 전 캐릭터 명칭
타임라인	afterName	변경 후 캐릭터 명칭
타임라인	level	캐릭터 레벨
타임라인	raidName	레이드 명칭(안톤, 루크)
타임라인	phaseName	레이드, 마수던전 달성 단계
타임라인	single	싱글 레이드 여부
타임라인	hard	레이드 하드 모드 여부
타임라인	guide	레이드 가이드 던전 여부
타임라인	squad	레이드 스쿼드 던전 여부
타임라인	matching	레이드 매칭 모드 여부
타임라인	raidPartyName	레이드 공격대 명칭
타임라인	point	마수던전 획득 포인트
타임라인	playTime	마수던전 참여 시간
타임라인	pvpGradeName	결투장 등급 명칭
타임라인	before	강화/증폭/재련/개조 전 수치
타임라인	after	강화/증폭/재련/개조 성공 후 변경 예정 수치
타임라인	ticket	강화/증폭/재련/개조에 사용한 아이템 정보
타임라인	result	강화/증폭/재련/개조 성공 여부
타임라인	resultItems	융합 분리를 통해 획득한 아이템 목록
타임라인	booster	봉인된 자물쇠 부스터 적용 유무
타임라인	adventureSafeMoveType	계정 금고로 이동 및 획득 정보 ( in : 금고로 이동 / out : 금고에서 획득 )
타임라인	safe	안전 강화 여부
타임라인	mistGear	미스트 기어 여부
타임라인	refinedMistGear	정제된 미스트 기어 여부
타임라인	pureMistGear	순수한 미스트 기어 여부
타임라인	itemObtainInfo	아이템 획득에 방식에 대한 정보
스킬	skillId	스킬 고유 코드
스킬	requiredLevel	최소 습득 레벨
스킬	requiredLevelRange	습득 레벨 구간
스킬	desc	스킬 설명
스킬	descDetail	스킬 상세 설명
스킬	descSpecial	스킬 특수 기능 설명
스킬	consumeItem	스킬 사용 소모 아이템
스킬	maxLevel	최대 레벨
스킬	preRequiredSkill	선행 스킬
스킬	consumeMp	MP 소모량
스킬	coolTime	쿨타임
스킬	castingTime	시전시간
스킬	levelInfo	스킬옵션 상세 정보
스킬	hash	스킬 트리 공유 코드
스킬	evolution	스킬 개화 정보
스킬	enhancement	스킬 강화 정보
스킬	chain	스킬 체인 정보
스킬	chain.resetTime	스킬 초기화 시간 정보
