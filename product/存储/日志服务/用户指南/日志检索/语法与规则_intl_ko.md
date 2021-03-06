CLS는 다양한 검색 기능을 제공하여 구문 조회, 규칙 검색을 통해 실시간으로 로그를 조회할 수 있고 및 초 수준으로 검색 결과를 반환하여 비즈니스 문제를 신속하게 찾을 수 있도록 도와줍니다.

## 검색 시작

로그 검색은 CLS가 제공하는 매우 중요한 기능입니다. 조회 조건을 사용자 지정하여 몇 초 내에 1억 수준의 로그 데이터를 조회할 수 있습니다. 자세한 조작 절차는 다음과 같습니다.

1. [CLS 콘솔](https://console.cloud.tencent.com/cls)에 로그인합니다.
2. 콘솔 왼쪽의 [로그 검색]을 선택하여 검색 페이지로 들어갑니다.
3. 조회 시간 범위, 로그 집합 및 로그 토픽을 선택합니다.
4. 키워드를 입력하고 [조회]를 클릭하여 결과를 얻습니다.

## 조회 구문
검색은 다음 조회 구문을 지원합니다.

|구문|의미|
|--|--|
|A and B| "및" 논리, A와 B의 교집합 결과를 반환합니다. 여러 키워드가, 쉼표, 세미콜론 또는 공백으로 구분되는 경우 기본값은 and입니다.|
|A or B|"또는" 논리, A 또는 B 의 합집합 결과를 반환합니다.|
|not B|"비" 논리, B를 포함하지 않는 결과를 반환합니다.|
|A not B| "빼기" 로직, A에 적합하지만 B에 적합하지 않는 결과를 반환합니다. 즉 A-B|
|(A , B)| 여러 개의 쿼리를 하나의 쿼리로 합칩니다. 주로 연산자 우선 순위를 제어합니다.|
|A:B |key-value 쌍의 조회 형식, key 또는 value에 공백, 콜론 등 핵심 문자를 포함하면 따옴표로 묶어야 합니다. 예: "error level":high |
|'a'| 문자 a는 일반 문자로 간주되며 구문 키워드로 취급되지 않습니다.|
|"A" | A의 모든 키워드는 일반 문자로 간주되며 구문 키워드로 취급되지 않습니다.|
|\ |이스케이프 문자, 이스케이프된 문자는 문자 자체를 표시합니다. 예: 이스케이프 따옴표 `\"`, 이스케이프 콜론 `\:` 등 |
|* |퍼지 조회를 위한 키워드. 0개, 1개 또는 여러 개의 문자와 일치하며 \*으로 시작할 수 없습니다. 예: `abc*`를 입력하면 abc로 시작한 모든 적중 로그가 반환됩니다.|
| ?|퍼지 조회 키워드, 특정 위치에 한 문자만 일치할 수 있습니다. 예: ab?c를 입력하면 ab로 시작하고 c로 끝나며 중간에 한 문자만 있는 모든 적중 로그를 반환합니다.|
|>| 보다 큼, 숫자 필드에 해당|
|>=| 보다 크거나 같음. 숫자 필드에 해당|
|<| 보다 작음. 숫자 필드에 해당|
|<=| 보다 작거나 같음. 숫자 필드에 해당|
|=| 같음. 숫자 필드 또는 텍스트 유형에 해당|
| in | 숫자 범위 조회, 중괄호 `[]`는 닫힌 구간, `()`는 열린 구간을 표시합니다. 예를 들어 `(0 100]`은 >0 및 <=100을 표시합니다.|
| \_source_ |소스 로그 조회. 예: \_source_:127.0.0.1|

>!
>- 연산자의 우선 순위는 위로부터 아래로 `:` > `"` > `()` > `and` > `not` > `or`입니다.
>- 범위 검색을 수행하려면 숫자 유형을 double 또는 long으로 설정해야 합니다. 그렇지 않으면 반환된 결과가 예상과 일치하지 않을 수 있습니다.
>- b가 텍스트인 경우 `a=b`와 `a:b`의 차이는 전자는 a가 b와 같고 후자는 a가 b를 포함한다는 것입니다(단어 세분화 로직으로 퍼지 검색 지원).
>- 구문 키워드는 대/소문자를 구분하지 않습니다.



## 검색 규칙
로그를 검색할 때 검색 시간 범위, 로그 집합 및 로그 토픽은 3가지 꼭 필요한 조건입니다. 기본 시간 범위는 현재 날짜입니다. 필요에 따라 로그 집합 및 로그 토픽을 선택할 수 있습니다. 검색창은 비워 둘 수 있으며 이 경우 필터 조건이 없음을 의미하고 모든 유효한 로그 데이터가 반환됩니다.

### 전체 텍스트 검색
전체 텍스트 검색을 활성화하는 로그 토픽의 경우, 시스템이 단어 구분 기호로 여러 구로 나뉘어 특정 키워드로 로그를 검색할 수 있습니다.

예를 들어 키워드 `error`가 포함된 로그 데이터를 검색하려면 검색창에 `error`를 입력하고 검색하면 됩니다.

### 키 값 검색
키 값 인덱스를 활성화하는 로그 토픽의 경우 시스템이 지정된 kv 키 값 쌍을 기반으로 관리됩니다. key 필드를 지정하여 로그를 검색할 수 있습니다.

예를 들어, `status` 필드가 `error`인 로그 데이터를 검색하려면 검색창에 `status:error`를 입력하여 검색하십시오.

### 퍼지 키워드 검색
CLS는 특수 퍼지 키워드로 로그를 검색할 수 있는 퍼지 조회를 지원합니다. 세부 정보는 다음과 같습니다.

|메타 문자|설명|
|-----|:-----|
| * | 퍼지 조회를 위한 키워드. 0개, 1개 또는 여러 개의 문자와 매칭합니다. 예: `abc*`를 입력하면 `abc`로 시작한 모든 적중 로그가 반환됩니다.|
| ? |퍼지 조회를 위한 키워드. 특정 위치에 한 문자만 매칭합니다 예: `ab?c`를 입력하면 `ab`로 시작하고 `c`로 끝나며 중간에 한 문자만 있는 모든 적중 로그를 반환합니다.|

### 토픽 간 검색
로그 검색을 사용하면 하나의 로그 집합만 선택할 수 있지만 여러 로그 토픽은 로그 집합에서 선택할 수 있습니다. 즉, 하나의 로그 집합 아래에서 동시에 여러 개의 로그 토픽을 검색할 수 있으므로 문제 해결이 쉬워집니다.

## 주의 사항
1. 로그 검색을 수행하기 전에 해당 로그 토픽에 대해 검색이 활성화한지 확인하십시오. 그렇지 않으면 유효한 로그를 검색할 수 없습니다.
2. 키 값 검색을 수행하기 전에 조회할 인덱스 필드가 로그 토픽의 인덱스 구성에 성공적으로 구성되었는지 확인하십시오.
3. 검색된 결과는 기본적으로 내림차순으로 표시됩니다.
