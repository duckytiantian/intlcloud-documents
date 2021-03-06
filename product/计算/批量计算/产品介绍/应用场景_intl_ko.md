## 유전자 서열분석
생물 정보 관련 회사 또는 실험실은 서열분석기를 이용하여 유전자 그룹 서열의 원본 파일을 획득합니다. 그리고 유전자 그룹 서열 초보 분석을 완료한 뒤 정보를 COS와 같은 클라우드 저장 시스템에 업로드합니다. 그런 다음 Tencent Cloud Batch Compute를 통해 정보를 자세하게 분석합니다.

![유전자 서열분석](https://main.qcloudimg.com/raw/77a08df12588d5b6a8b0e8980bb00465.svg)

#### 일반 절차
1. 생물 정보 전문가는 서열분석기 또는 개인 클라우드 스토리지에서 원본 정보를 획득한 뒤 COS, CFS와 같은 Tencent Cloud 스토리지 서비스에 업로드합니다.
2. 정보를 분석하기 위해 Batch 작업을 사용자 지정하고 작업을 제출합니다. 작업의 저장 구성은 이전 단계에서 업로드한 원본 정보와 관련이 있습니다.
3. Batch는 리소스를 자동 스케줄링하고 사용자가 업로드한 사용자 지정 분석 이미지를 스케줄링된 CVM에 배포합니다. 동시에 작업을 자동으로 스케줄링하여 원본 정보를 분석하기 시작합니다.
4. CVM의 컴퓨팅이 완료되면 Batch는 분석 결과를 사용자 지정 위치에 자동 업로드합니다.
분석 대기인 원본 정보는 COS에 업로드됩니다.

## 동영상 렌더링
미디어 방송과 광고, 건축 디자인 등 분야에서 컨텐츠 제작자와 후반 작업 회사는 대량의 장치를 사용하여 미디어 방송 특수효과, 3D 애니메이션, 특수효과 이미지 등 관련 렌더링 작업을 완료하여야 합니다. Tencent Cloud Batch Compute으로 사용자는 콘텐츠 렌더링 작업 흐름을 자동화할 수 있습니다. 사용자가 나만의 렌더링 의존 프로세스를 구축할 수 있으며 Batch의 엄청난 양의 리소스와 작업 스케줄링 능력을 활용하여 작업을 효율적으로 완료할 수 있습니다.

![동영상 렌더링](https://main.qcloudimg.com/raw/099b313d27c2616e4c8c88c51a92b4f9.svg)

#### 일반 절차
1. 사용자는 렌더링해야 할 원본 재료를 준비하고 COS, CFS와 같은 Tencent Cloud 저장 서비스에 업로드합니다.
2. 정보를 분석하기 위해 Batch 작업을 사용자 지정하고 작업을 제출합니다. 작업의 저장 구성은 이전 단계에서 업로드한 원본 정보와 관련이 있습니다.
3. Batch는 리소스를 자동 스케줄링하고 사용자가 업로드한 사용자 지정 렌더링 이미지를 스케줄링된 CVM에 배포합니다. 동시에 작업을 자동으로 스케줄링하여 동영상 또는 특수효과 이미지를 분석하기 시작합니다.
4. Batch는 CVM에서 렌더링 프로세스를 완료한 뒤, 생성된 동영상 또는 특수효과 이미지를 사용자 지정 위치에 업로드합니다.
