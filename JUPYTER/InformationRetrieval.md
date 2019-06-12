# 정보검색

<https://nlp.stanford.edu/IR-book/newslides.html>

<table>
<tr><td>01</td><td>Boolean retrieval</td></tr>
<tr><td>02</td><td>The term vocabulary & postings lists</td></tr>
<tr><td>03</td><td>Dictionaries and tolerant retrieval</td></tr>
<tr><td>04</td><td>Index construction</td></tr>
<tr><td>05</td><td>Index compression</td></tr>
<tr><td>06</td><td>Scoring, term weighting & the vector space model</td></tr>
<tr><td>07</td><td>Computing scores in a complete search system</td></tr>
<tr><td>08</td><td>Evaluation in information retrieval</td></tr>
<tr><td>09</td><td>Relevance feedback & query expansion</td></tr>
<tr><td>10</td><td>XML retrieval (old)</td></tr>
<tr><td>11</td><td>Probabilistic information retrieval (old)</td></tr>
<tr><td>12</td><td>Language models for information retrieval (old)</td></tr>
<tr><td>13</td><td>Text classification & Naive Bayes</td></tr>
<tr><td>14</td><td>Vector space classification</td></tr>
<tr><td>15-1</td><td>Support vector machines</td></tr>
<tr><td>15-2</td><td>Learning to rank</td></tr>
<tr><td>16</td><td>Flat clustering</td></tr>
<tr><td>17</td><td>Hierarchical clustering</td></tr>
<tr><td>18</td><td>Matrix decompositions & latent semantic indexing</td></tr>
<tr><td>19</td><td>Web search basics</td></tr>
<tr><td>20</td><td>Web crawling and indexes</td></tr>
<tr><td>21</td><td>Link analysis</td></tr>
</table>

<https://jjeong.tistory.com/1122>
<http://nlp.stanford.edu/IR-book/>

Chap01. Information retrieval! using the Boolean model

- 상용 검색서비스의 대부분이 채택하고 있는 모델인 불리언 검색 모델에 대한 내용
- AND, OR 등의 연산자를 포스팅 리스트를 통해서 어떻게 처리하고 있는지를 설명

> 현재 우리가 사용하고 있는 검색엔진의 작동 방식을 설명. 여러 관련 컴포넌트는 어떤것들이 있는지 등등…

Chap02. The dictionary and postings lists

- 빠른 검색을 위해 색인 처리를 하는데, 이를 구성하는 사전과 포스팅 리스트에 대한 내용
- 우리가 사용하고 있는 사전과 포스팅 외에도 다양한 용도의 다른 사전과 텀 포지션 정보들에 대해 설명

> 빠른 검색을 위해 문서의 정보를 검색엔진에 적합하도록 가공하는데 그것에 대한 결과물이죠.

Chap03. Tolerant retrieval! –

- 실데이터를 다룰 때 발생하는, 질의어 상에 또는 문서나 사전 상에, 여러 오류를 처리하는 내용
- 부분패턴 검색, k-Gram 처리, 오타처리, 동음어 처리 등에 대해 설명

> 검색 서비스를 위해서 꼭 필요한 유틸리티라 할 수 있는데 편의성과 융통성 등을 높여줍니다.

Chap04. Index construction

- 제한된 머신의 리소스 안에서 대용량의 색인을 처리하는 방법에 대한 내용
- 블록병합색인, 분산색인, 동적색인, 포지션 정보를 포함한 색인, 권한 정보를 포함한 색인

> 서비스 파트에서 열심히 하고 있는 작업이죠. 대용량의 색인을 할 때 필요한 지식입니다.

Chap05. Index compression

- 색인 데이터를 실제 메모리에 올려 사용해야 하기 때문에 성능을 고려한 압축이 필요. 그에 대한 내용
- 색인용량 예측방법(사전,포스팅), Dictionary압축, 블록저장, PostingFile압축, γ코드 압축, Zipf의법칙

> 데이터 특성에 따라 더 효율적인 압축도 가능합니다. 더 빠르게, 더 작게.. 맨날 하는 색인작업이 1시간 안에 끝난다면 좋겠죠.

Chap06. Term weighting and vector space models

- 단어 가중치 기법을 이용하여 질의어와 문서의 유사성 거리를 벡터 방식으로 풀어내는 검색 모델 소개
- 단어와 문서 구역에 대한 Scoring 및 Weighting, TF, IDF, TF*IDF, 가중치 정규화, 유사도 함수

> 불리언의 필터링 성격보다 보다 진보한 형태의 검색기법입니다. 질의와 문서의 유사도에 대한 개념이 시작됩니다.

Chap07. Computing scores in a complete search system

- 단어 가중치 기법 이외의 스코어링과 랭킹 기법에 대한 설명

- 스코어링과 랭킹, 챔피온 리스트, 품질 스코어링, Ordering, 스코어링용 Features, 스코어링 디자인

> 랭킹에 대한 가중치는 우리도 많이 사용하고 있죠. 더 좋은 검색 품질을 위해 끊임없이 개발해야 하는 부분입니다.



Chap08. Eval!uation in information retrieval!

- 검색 모델의 검색 성능 측정 방법에 대한 내용

- 테스트 콜렉션, 정확도와 재현율, 랭킹에 대한 평가, 적합도 판정, 시스템 품질과 사용성

> 검색 서비스의 오픈할 때 하는 성능측정 외에도 계속적인 평가와 모니터링이 필요합니다. 쿼리 파라미터의 뭘 수정해야 할까요??



Chap09. Relevance feedback and query expansion

- 사용자 피드백에 의한 재검색 모델과 질의어 확장에 대한 내용

- 최적화된 결과를 내놓기 위한 방법, Rocchio 알고리즘, 확률적 적합도, 질의 확장용 사전, 자동 시소러스 생성

> 쇼핑관련 검색서비스 등에 적용하면 좋은 모델입니다. 쿼리확장은 공통이지만 모호성이 있는 특히 지식, 뉴스, 일반 웹검색 등에 더욱 필요하죠.



Chap10. XML retrieval!

- 일반 텍스트가 아닌 구조적 텍스트인 XML 문서에 대한 검색 방법에 대한 내용

- XML 문서, XML 검색 개요, XML 검색용 벡터 모델, 콘텐츠 중심과 구조적 중심의 검색 비교

> 그다지 새로운 개념은 아닙니다. 전처리파트에서 HTML, PDF, DOC, PPT 파일등을 XML로 가공해서 퍼주면 해야할 일들입니다.



Chap11. Probabilistic information retrieval!

- 확률적 검색 모델에 대한 내용

- 확률이론, 확률적 랭킹기법, 이진독립모델, 확률값(기대치) 추정, 다양한 확률 모델

> 불리언 검색의 대안 모델중에 하나인 확률모델입니다. 0/1 대신에 질의어에 대한 문서 적합성을 확률로 계산하죠.



Chap12. Language models for information retrieval!

- 언어적 특징(특정 단어가 실제로 쓰여질 확률)에 기반한 검색 모델 소개

- Query likelihood model, Ponte & Croft 실험, 다양한 언어모델 기법

> 많이 쓰이는 단어 많이 쓰이지 않는 단어에 각기 다른 가중치를 두어 질의어를 가공하면 좀 더 주제가 명확한 결과가 나오겠죠.



Chap13. Text classification and Naive Bayes

-        문서 분류와 나이브 베이지안(확률적) 분류 기법에 대한 내용

- 문서 분류, Naïve Bayes 분류기법, Bernoulli 모델, 특징 추출, 상호 정보성(Mutual Information), 카이스퀘어 특징추출, 분류 평가

> 검색은 대규모의 컬렉션에서 사용자의 의도에 적합한 문서를 필터링하는 작업을 말하는데 이를 분류라고 표현할 수도 있습니다.
 유사성 혹은 관련성에 의한 분류 기법으로 검색품질을 높일수 있습니다. 서치 플러그인 등에서 사용하면 좋겠죠.



Chap14. Vector space classification

- 벡터 공간 모델에 의한 분류 기법에 대한 내용

- Rocchio 분류, k-nearest neighbor(k근접이웃), 선형 및 비선형 분류, 분류의 tradeoff

> 유사하다는 개념을 어떻게 정의하면 좋을까요? 뚝딱 반으로 자를까요? 고려할 요소가 많아 복잡한건 어떻게 자를까요?


Chap15. Support vector machines and kernel functions

- 14장의 벡터공간모델에 의한 기계학습기법인 SVM에 대한 내용, 분류 기법에 대한 핵심 함수

- SVM, 유연한 경계에 의한 분류, 비선형 SVMs

> 분류를 위한 대표적인 기계학습기법인 SVM입니다. 수학을 잘하면 재밋는데 못하면 재미없습니다. 
   결과가 주어졌을 때 x,y,z 등에 의한 선형분석입니다. 오류를 최소로 만드는 해를 찾는 기법이죠. 분류는 다 이런 식입니다.



Chap16. Flat clustering

- 비교사학습인 군집화 기법에 대한 내용 (vs 분류는 정답이 있는 교사학습기법), 평면적인 군집

- 정보검색에서의 군집화, 군집평가, k평균 알고리즘, EM 클러스터링

> 분류는 검색형태에 대한 의도를 품고서 문서를 솎아내는 방식이라 지속적으로 관리가 필요합니다. 구체적인 기획이 필요하죠.
   반면에 군집은 유사성이라는 척도 하나로 알아서 다해줍니다. 후처리에서 미리 해주면 검색품질이 엄청 좋아집니다.
   또는 검색엔진을 거친 후 재가공으로서 사후클러스터링을 하면 같은 질의어에 다른 내용의 문서들을 어느정도 모아서 볼여줄 수 있겠죠.



Chap17. Hierarchical clustering

- 구조적인(상향식, 하향식) 군집기법에 대한 내용

- 싱글링크&완전링크 군집화, 그룹핑 방식의 군집화, 중심축 기반의 군집화, 군집명명기법

> 앞에 군집기법은 좀 옛날겁니다. 요즈음은 인간의 군집화 방식을 좀 더 흉내내어 다 부순다음에 하나씩 모아가는 방식이거나
   또는 하나로 뭉쳐놓은 상태에서 아닌것들을 짤라내는 형식으로 군집화를 합니다. 제 논문도 이에 관련한거죠. 재밋습니다.



Chap18. Matrix decompositions and Latent Semantic Indexing

- 행렬분해와 잠재의미인덱싱 기법에 대한 내용 (요인분석과 차원축소를 이용한 인덱싱)

- 선형대수학, 행렬분해, 단어-문서 행렬, 고유값분해, 저차원 추정과 잠재의미색인(LSI)

> 행렬이 나오는데 아주 골치아프더군요. 내용인즉슨… 단어로 쪼개진 사전 기반의 색인방식을 해결하기 위한 대안으로 단어와 문서의 관계를 통째로 색인하자는거죠. 통째로 색인하면 콜렉션과 단어의 관계성이 그대로 살아있게됩니다. 그걸 그냥 쓰려니 너무 커서 줄여서 쓰는 방법을 고안한거죠.



Chap19. Web search basics

- 웹검색에 관련한 다양한 이슈들에 대한 내용

- 웹의 특징, 웹 그래프, 스팸, 웹광고, 웹검색 경향, fingerprint, 중복문서 해결기술과 Shingling

> 중복문서 제거입니다. 수집 문서중에서 많게는 70~80%가 중복이라는군요.
   이를 해결하기 위해 핑거프리트와 Shingling에 대해 소개하고 있습니다. 구글에 적용된 방식이기도 하구요. 스팸처리도 있군요.



Chap20. Web crawling and indexes

- 웹문서 수집과 색인에 대한 내용
- Crawling, 크롤러 구조, DNS 처리방안, URL 프론티어, 분산색인, 병렬서버
jk
> 누가 더 많이 수집하고 누가 더 빨리 처리해서 색인기에 집어 넣느냐는 절대적인 성능지표이죠.
   또 우리나라 검색회사가 글로벌로 성장해서 아시아의 모든 문서를 하나의 검색서비스로 제공한다면 어떻게 해야 할까요? 구글은 하고 있습니다.

Chap21. Link analysis

- 그래프 구조의 형태를 갖는 웹문서의 특징을 이용한 분석기법에 대한 내용 (구글의 Pagerank)
- Pagerank, 마코브 체인, 페이지랭크 계산, 특정 토픽기반의 Pagerank, Hubs(참조) and Authorities(권위)

> 21세기 히트작이죠. 구글의 페이지랭크입니다. 이를 기회로 ‘사회적 네트워크’에 대한 관심이 폭발적으로 높아졌습니다.
   싸이월드도 그 대표적인 사례죠. 카페가 강점인 우리회사도 이를 충분히 이용할 수 있습니다. 블로그는 더더욱 그렇구요. 펌질~흐
   우리나라 사람들은 입소문을 잘 내기도 하고 군중심리도 있기 때문에 그래프 분석을 하면 검색에 큰 효과를 가져올 수 있을겁니다. 제가 궁극적으로 하고 싶은 분야도 이쪽입니다. 게시판의 글들을 컨셉별로 나눌수도 있고 관련 UCC를 연결할 수도 있겠죠. 잘~되면^^

출처: https://jjeong.tistory.com/1122 [jjeong]