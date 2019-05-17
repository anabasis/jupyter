# KONLPY

<http://konlpy.org/en/latest/references/>

## Subpackages

### tag

#### 1. Hannanum

JHannanum은 Java로 작성된 형태소분석기 및 POS 태그 작성기로 1999년부터 KAIST 시맨틱 웹 연구 센터(SWRC)에서 개발.

```python
from konlpy.tag import Hannanum
hannanum = Hannanum()

print(hannanum.analyze(u'롯데마트의 흑마늘 양념 치킨이 논란이 되고 있다.'))

[[[('롯데마트', 'ncn'), ('의', 'jcm')], [('롯데마트의', 'ncn')], [('롯데마트', 'nqq'), ('의', 'jcm')], [('롯데마트의', 'nqq')]], [[('흑마늘', 'ncn')], [('흑마늘', 'nqq')]], [[('양념', 'ncn')]], [[('치킨', 'ncn'), ('이', 'jcc')], [('치킨', 'ncn'), ('이', 'jcs')], [('치킨', 'ncn'), ('이', 'ncn')]], [[('논란', 'ncpa'), ('이', 'jcc')], [('논란', 'ncpa'), ('이', 'jcs')], [('논란', 'ncpa'), ('이', 'ncn')]], [[('되', 'nbu'), ('고', 'jcj')], [('되', 'nbu'), ('이', 'jp'), ('고', 'ecc')], [('되', 'nbu'), ('이', 'jp'), ('고', 'ecs')], [('되', 'nbu'), ('이', 'jp'), ('고', 'ecx')], [('되', 'paa'), ('고', 'ecc')], [('되', 'paa'), ('고', 'ecs')], [('되', 'paa'), ('고', 'ecx')], [('되', 'pvg'), ('고', 'ecc')], [('되', 'pvg'), ('고', 'ecs')], [('되', 'pvg'), ('고', 'ecx')], [('되', 'px'), ('고', 'ecc')], [('되', 'px'), ('고', 'ecs')], [('되', 'px'), ('고', 'ecx')]], [[('있', 'paa'), ('다', 'ef')], [('있', 'px'), ('다', 'ef')]], [[('.', 'sf')], [('.', 'sy')]]]

print(hannanum.morphs(u'롯데마트의 흑마늘 양념 치킨이 논란이 되고 있다.'))
['롯데마트', '의', '흑마늘', '양념', '치킨', '이', '논란', '이', '되', '고', '있', '다', '.']

print(hannanum.nouns(u'다람쥐 헌 쳇바퀴에 타고파'))
['다람쥐', '쳇바퀴', '타고파']

print(hannanum.pos(u'웃으면 더 행복합니다!'))
```

> 매개 변수
> __jvmpath__ - JVM을의 경로로 전달 init_jvm().
> __max_heap_size__ - 최대 메모리 사용 제한 (메가 바이트) init_jvm().

##### analyze(구문)

구문 분석기.

이 분석기는 각 토큰에 대한 다양한 형태 학적 후보를 반환합니다. 그것은 두 부분으로 구성되어 있습니다 : 1) 사전 검색 (차트), 2) 분류되지 않은 용어 세분화.

##### morphs(구문)

형태소 분석 문구.

##### nouns(구문)

명사 추출기.

##### pos(phrase,ntags=9,flatten=True,join=False)

POS 태거.
이 태그 작성기는 HMM기반이며 태그 확률을 계산합니다.

> 매개 변수
> __ntags__ - 태그의 수. 9 또는 22 중 하나 일 수 있습니다.
> __flatten__ - 거짓이면, '어절'을 보존합니다.
> __join__ - 참이면 모프(형태소)와 태그의 결합 된 세트를 반환합니다.

#### 2. Kkma

Kkma는 서울대 지능정보시스템(IDS)연구실에서 개발 한 자바로 작성된 형태소분석기 및 자연 언어 처리 시스템.

```python
from konlpy.tag import Kkma
kkma = Kkma()

print(kkma.morphs(u'공부를 하면할수록 모르는게 많다는 것을 알게 됩니다.'))
['공부', '를', '하', '면', '하', 'ㄹ수록', '모르', '는', '것', '이', '많', '다는', '것', '을', '알', '게', '되', 'ㅂ니다', '.']

print(kkma.nouns(u'대학에서 DB, 통계학, 이산수학 등을 배웠지만...'))
['대학', '통계학', '이산', '이산수학', '수학', '등']

print(kkma.pos(u'다 까먹어버렸네요?ㅋㅋ'))
[('다', 'MAG'), ('까먹', 'VV'), ('어', 'ECD'), ('버리', 'VXV'), ('었', 'EPT'), ('네요', 'EFN'), ('?', 'SF'), ('ㅋㅋ', 'EMO')]

print(kkma.sentences(u'그래도 계속 공부합니다. 재밌으니까!'))
['그래도 계속 공부합니다.', '재밌으니까!']
```

> 매개 변수
> __jvmpath__ - JVM을의 경로로 전달 init_jvm().
> __max_heap_size__ - 최대 메모리 사용 제한 (메가 바이트) init_jvm().

##### morphs(구문)

형태소 분석 문구.

##### nouns( 구문 )
명사 추출기.

##### pos(phrase,flatten=True,join=False)

POS 태거.

> 매개 변수
> __flatten__ - 거짓이면, 오정을 보존합니다.
> __join__ - 참이면 모프와 태그의 결합 된 세트를 반환

##### sentences(구문)

문장 감지.

#### 3. Komoran


#### 4. Mecab

#### 5. Okt

### corpus

## data

## downlaoder

## jvm

## utils
