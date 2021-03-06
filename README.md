## 뉴스 및 신문기사 크롤러

주로 국내 뉴스기사 및 RSS FEED를 보다 편리하게 크롤링할 수 있는 크롤러(crawler)입니다.



## 사용법



### crawl_url

단일 url에 대한 뉴스 정보를 가져옵니다.



**Parameter**

| parameter      | usage                             |
| -------------- | --------------------------------- |
| url            | 요청 url                          |
| shuffle_header | user-agent의 셔플(랜덤) 여부      |
| language       | 뉴스기사 언어 설정 (기본값: 'ko') |



**Return**

크롤링 한 후 결과값은 dictionary 형태로 반환합니다.

| key          | value                             |
| ------------ | --------------------------------- |
| title        | 뉴스 기사 제목                    |
| image        | 대표 이미지                       |
| crawl_url    | 요청한 뉴스 기사 url              |
| url          | 뉴스 기사 url                     |
| published_at | 발간일 (publish date)             |
| text         | 텍스트 형식의 본문                |
| body         | html 형식의 본문                  |
| language     | 설정된 language 옵션 (기본: 'ko') |

**Example**

```python
from news_crawler import NewsCrawler

sample_url = """
https://news.naver.com/main/ranking/read.nhn?mid=etc&sid1=111&rankingType=popular_day&oid=001&aid=0011193089&date=20191106&type=1&rankingSeq=4&rankingSectionId=105
"""

c = NewsCrawler()
c.crawl_url(sample_url)
```

```
{'title': '삼성 中서 갤럭시폴드 첫 공개…5G폰 점유율 29%로 급등',
 'image': 'https://imgnews.pstatic.net/image/001/2019/11/06/AKR20191106077700089_02_i_20191106112039711.jpg',
 'crawl_url': 'https://news.naver.com/main/ranking/read.nhn?mid=etc&sid1=111&rankingType=popular_day&oid=001&aid=0011193089&date=20191106&type=1&rankingSeq=4&rankingSectionId=105',
 'url': 'https://news.naver.com/main/ranking/read.nhn?mid=etc&sid1=111&rankingType=popular_day&oid=001&aid=0011193089&date=20191106&type=1&rankingSeq=4&rankingSectionId=105',
 'published_at': datetime.datetime(2019, 11, 6, 13, 57, 47, 3626),
 'text': "중국국제수입박람회 전시된 갤럭시폴드(상하이=연합뉴스) 차대운 특파원 = 5일 중국 상하이에서 진행 중인 제2회 중국국제수입박람회의 삼성 전시장에서 관람객들이 유리 상자 속에 놓인 갤럭시폴드를 살펴보고 있다. 2019.11.6\n\ncha@yna.co.kr\n\n(끝) 중국국제수입박람회 전시된 갤럭시폴드(상하이=연합뉴스) 차대운 특파원 = 5일 중국 상하이에서 진행 중인 제2회 중국국제수입박람회의 삼성 전시장에서 관람객들이 유리 상자 속에 놓인 갤럭시폴드를 살펴보고 있다. 2019.11.6cha@yna.co.kr(끝)\n\n3분기 중국 5G 스마트폰 시장 점유율[ICD 홈페이지] 3분기 중국 5G 스마트폰 시장 점유율[ICD 홈페이지]\n\n수입박람회장서 실물 전시…삼성, 5G 서비스 개시 계기 반등 노려삼성·화웨이 1주일 격차로 '폴더블폰 대결'…5G폰 시장도 격전 예고(상하이=연합뉴스) 차대운 특파원 = 삼성전자가 중국에서 처음으로 갤럭시폴드 실물을 대중 앞에 선보였다.삼성전자는 5일 개막한 제2회 국제수입박람회 전시장에서 갤럭시폴드 3대를 전시했다.현장에서는 많은 관람객이 유리 상자 안에 놓인 채로 전시된 갤럭시폴드에 큰 관심을 보였다.삼성전자는 이달 8일 중국에서 갤럭시폴드를 출시하기로 하고 현재 고객들로부터 예약 신청을 받고 있다.업계에서는 이번에 중국에 공급될 갤럭시폴드가 2만여대가량일 것으로 추정하고 있다. 출시 가격은 1만4천위안(231만원)가량으로 관측되고 있다.삼성전자와 화웨이가 글로벌시장에서 격돌 중인 가운데 삼성은 화웨이보다 1주일 앞서 폴더블폰을 내놓고 시장 선점에 들어간다.화웨이는 이달 15일 첫 폴더블폰인 메이트X를 출시한다.중국이 이달부터 5세대(5G) 이동통신 서비스를 시작한 것을 계기로 삼성은 5G 스마트폰을 앞세워 그동안 침체한 중국 시장에서 반전을 노리고 있다.2013년까지만 해도 삼성전자는 중국 스마트폰 시장에서 20%대의 시장 점유율로 1위 자리를 지켰다.그러나 '가성비'를 앞세운 화웨이, 샤오미, 오포 등 중국 토종 브랜드의 출혈에 가까운 저가 경쟁 속에서 최근 삼성전자의 중국 시장 점유율은 계속 내려가 결국 1% 미만으로까지 추락했다.하지만 5G 스마트폰은 원가 부담이 커 저가 경쟁이 어렵다. 이런 상황을 이용해 삼성은 빠르게 5G 시장에서 시장 점유율을 높여나가고 있다.여세를 몰아 삼성전자는 '중국의 쇼핑 1번지'로 상징성이 큰 상하이 난징둥루(南京東路)에 첫 모바일 플래그십 매장을 내고 중국 시장에서 공격적인 마케팅에 들어갔다.시장 정보 업체 IDC에 따르면 삼성전자는 출하량을 기준으로 3분기 중국 5G 스마트폰 시장에서 29.0%의 시장 점유율로 54.3%의 비보에 이어 2위를 차지했다.현재 삼성전자는 중국 시장에서 갤럭시노트10플러스(7천999위안), A90(4천499위안) 두 종류의 5G 스마트폰을 판매 중이다.특히 마진이 높은 고가 단말기 시장에서 독주하고 있는 점도 삼성전자에는 고무적 현상이다.비보가 550달러 미만의 중·저가 5G 스마트폰에서 1위를 차지했지만 삼성전자는 700달러 이상의 고가 5G 스마트폰에서 1위를 차지했다.따라서 출하량이 아닌 매출액을 기준으로 하면 삼성전자의 시장 점유율은 훨씬 높을 것으로 추정된다.주력 5G 상품 출시가 늦은 화웨이는 9.5%의 점유율로 3위에 그쳤다. 이어 샤오미(4.6%), ZTE(1.5%) 등이 뒤를 이었다.3분기 중국 시장에서는 48만5천대의 5G 스마트폰이 출시됐다.향후 삼성전자는 5G 시장에서 중국 시장을 독식하려는 화웨이와 정면 대결을 벌여야 할 전망이다.미국의 제재로 신제품 개발과 출시에 영향을 받는 화웨이는 최근 들어서야 주력 5G 스마트폰인 메이트30을 출시해 본격적으로 5G 단말기 시장에 뛰어들었다.cha@yna.co.kr",
 'body': '<div class="_article_body_contents" id="articleBodyContents">\n\n\n\n\n\t\n\t수입박람회장서 실물 전시…삼성, 5G 서비스 개시 계기 반등 노려<br/><br/>삼성·화웨이 1주일 격차로 \'폴더블폰 대결\'…5G폰 시장도 격전 예고<br/><br/><span class="end_photo_org"></span><br/><br/>(상하이=연합뉴스) 차대운 특파원 = 삼성전자가 중국에서 처음으로 갤럭시폴드 실물을 대중 앞에 선보였다.<br/><br/>    삼성전자는 5일 개막한 제2회 국제수입박람회 전시장에서 갤럭시폴드 3대를 전시했다.<br/><br/>    현장에서는 많은 관람객이 유리 상자 안에 놓인 채로 전시된 갤럭시폴드에 큰 관심을 보였다.<br/><br/>    삼성전자는 이달 8일 중국에서 갤럭시폴드를 출시하기로 하고 현재 고객들로부터 예약 신청을 받고 있다. <br/><br/>    업계에서는 이번에 중국에 공급될 갤럭시폴드가 2만여대가량일 것으로 추정하고 있다. 출시 가격은 1만4천위안(231만원)가량으로 관측되고 있다.<br/><br/>    삼성전자와 화웨이가 글로벌시장에서 격돌 중인 가운데 삼성은 화웨이보다 1주일 앞서 폴더블폰을 내놓고 시장 선점에 들어간다.<br/><br/>    화웨이는 이달 15일 첫 폴더블폰인 메이트X를 출시한다.<br/><br/>    중국이 이달부터 5세대(5G) 이동통신 서비스를 시작한 것을 계기로 삼성은 5G 스마트폰을 앞세워 그동안 침체한 중국 시장에서 반전을 노리고 있다.<br/><br/>    2013년까지만 해도 삼성전자는 중국 스마트폰 시장에서 20%대의 시장 점유율로 1위 자리를 지켰다.<br/><br/>    그러나 \'가성비\'를 앞세운 화웨이, 샤오미, 오포 등 중국 토종 브랜드의 출혈에 가까운 저가 경쟁 속에서 최근 삼성전자의 중국 시장 점유율은 계속 내려가 결국 1% 미만으로까지 추락했다.     <br/><br/>    하지만 5G 스마트폰은 원가 부담이 커 저가 경쟁이 어렵다. 이런 상황을 이용해 삼성은 빠르게 5G 시장에서 시장 점유율을 높여나가고 있다.<br/><br/>    여세를 몰아 삼성전자는 \'중국의 쇼핑 1번지\'로 상징성이 큰 상하이 난징둥루(南京東路)에 첫 모바일 플래그십 매장을 내고 중국 시장에서 공격적인 마케팅에 들어갔다.<br/><br/>    시장 정보 업체 IDC에 따르면 삼성전자는 출하량을 기준으로 3분기 중국 5G 스마트폰 시장에서 29.0%의 시장 점유율로 54.3%의 비보에 이어 2위를 차지했다.<br/><br/>    현재 삼성전자는 중국 시장에서 갤럭시노트10플러스(7천999위안), A90(4천499위안) 두 종류의 5G 스마트폰을 판매 중이다.<br/><br/><span class="end_photo_org"></span><br/><br/>    특히 마진이 높은 고가 단말기 시장에서 독주하고 있는 점도 삼성전자에는 고무적 현상이다. <br/><br/>    비보가 550달러 미만의 중·저가 5G 스마트폰에서 1위를 차지했지만 삼성전자는 700달러 이상의 고가 5G 스마트폰에서 1위를 차지했다.<br/><br/>    따라서 출하량이 아닌 매출액을 기준으로 하면 삼성전자의 시장 점유율은 훨씬 높을 것으로 추정된다.<br/><br/>    주력 5G 상품 출시가 늦은 화웨이는 9.5%의 점유율로 3위에 그쳤다. 이어 샤오미(4.6%), ZTE(1.5%) 등이 뒤를 이었다.<br/><br/>    3분기 중국 시장에서는 48만5천대의 5G 스마트폰이 출시됐다.<br/><br/>    향후 삼성전자는 5G 시장에서 중국 시장을 독식하려는 화웨이와 정면 대결을 벌여야 할 전망이다.<br/><br/>    미국의 제재로 신제품 개발과 출시에 영향을 받는 화웨이는 최근 들어서야 주력 5G 스마트폰인 메이트30을 출시해 본격적으로 5G 단말기 시장에 뛰어들었다.<br/><br/>    cha@yna.co.kr<br/><br/><a href="https://m.yna.co.kr" target="_blank">▶확 달라진 연합뉴스 웹을 만나보세요</a><br/><br/><a href="https://media.naver.com/channel/promotion.nhn?oid=001&amp;naver_promotion&amp;did=1195s" target="_blank">▶네이버 [연합뉴스] 채널 구독   </a><a href="https://hng.yna.co.kr/?site=hng_tit&amp;did=1195s" target="_blank">▶뭐 하고 놀까? #흥</a><br/><br/>\n\n</div>',
 'language': 'ko'}
```



### crawl_rss

rss feed형식의 .xml을 parsing하여 크롤링 할 전체 url을 가져온 다음 뉴스 기사 정보를 추출하여 리턴해 줍니다.



**Parameter**

| parameter      | usage                             |
| -------------- | --------------------------------- |
| rss_url        | 요청 rss url                      |
| shuffle_header | user-agent의 셔플(랜덤) 여부      |
| language       | 뉴스기사 언어 설정 (기본값: 'ko') |



**Return**

크롤링 한 후 결과값은 dictionary list 형태로 반환합니다.

dictionary는 상위 `crawl_url` 으로부터 얻은 리턴 값과 동일합니다.



**Example**

```python
from news_crawler import NewsCrawler

rss_url = "http://platum.kr/feed"

c = NewsCrawler()
c.crawl_rss(rss_url)
```

**Output**

```
https://platum.kr/archives/130922
https://platum.kr/archives/130911
https://platum.kr/archives/130904
https://platum.kr/archives/130900
https://platum.kr/archives/130896
```

```
[{'title': '‘혁신가들이 그리는 미래’를 먼저 만나는 아시아 최대 규모 스타트업 축제 열린다',
  'image': 'https://platum.kr/wp-content/uploads/2019/11/page.jpg',
  'crawl_url': 'https://platum.kr/archives/130937',
  'url': 'https://platum.kr/archives/130937',
  'published_at': datetime.datetime(2019, 11, 6, 11, 59, 49, tzinfo=tzoffset(None, 32400)),
  'text': '최근 미국, 유럽, 아시아 등 전 세계적으로 스.....
```















