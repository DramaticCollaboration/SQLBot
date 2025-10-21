<p align="center"><img src="https://resource-fit2cloud-com.oss-cn-hangzhou.aliyuncs.com/sqlbot/sqlbot.png" alt="SQL봇" width="300" /></p>
대형 모델 및 RAG 기반 지능형 질문 시스템
<p  align="center">
  <a href="https://github.com/dataease/SQLBot/releases/latest"><img src="https://img.shields.io/github/v/release/dataease/SQLBot" alt="최신 릴리스"></a>
  <a href="https://github.com/dataease/SQLBot"><img src="https://img.shields.io/github/stars/dataease/SQLBot?color=%231890FF&style=flat-square" alt="별"></a>    
  <a href="https://hub.docker.com/r/dataease/SQLbot"><img src="https://img.shields.io/docker/pulls/dataease/sqlbot?label=downloads" alt="다운로드"></a><br/>

</p>
<hr/>

SQLBot은 대규모 모델과 RAG(질문과 답변)를 기반으로 하는 지능형 질의응답 시스템입니다. SQLBot의 장점은 다음과 같습니다.

- **즉시 사용 가능**: 빅 모델과 데이터 소스를 구성하여 데이터 검색 여정을 시작하세요. 빅 모델과 RAG를 함께 사용하면 고품질의 Text2SQL을 구현할 수 있습니다.
- **통합이 쉽습니다**: 타사 비즈니스 시스템에 빠르게 내장할 수 있으며 n8n, MaxKB, Dify, Coze와 같은 AI 애플리케이션 개발 플랫폼과 통합할 수 있어 다양한 애플리케이션이 빠르게 지능형 데이터 쿼리 기능을 확보할 수 있습니다.
- **안전하고 제어 가능**: 세분화된 데이터 권한 제어를 가능하게 하는 작업 공간 기반 리소스 격리 메커니즘을 제공합니다.

## 작동 원리

<img width="1105" height="577" alt="system-arch" src="https://github.com/user-attachments/assets/462603fc-980b-4b8b-a6d4-a821c070a048" />


## 빠른 시작

### 설치 및 배포

Linux 서버를 준비하고 [Docker](https://docs.docker.com/get-docker/)를 설치한 후 다음의 원클릭 설치 스크립트를 실행합니다.

```bash
docker run -d \
  --name sqlbot \
  --restart unless-stopped \
  -p 8000:8000 \
  -p 8001:8001 \
  -v ./data/sqlbot/excel:/opt/sqlbot/data/excel \
  -v ./data/sqlbot/file:/opt/sqlbot/data/file \
  -v ./data/sqlbot/images:/opt/sqlbot/images \
  -v ./data/sqlbot/logs:/opt/sqlbot/app/logs \
  -v ./data/postgresql:/var/lib/postgresql/data \
  --privileged=true \
  dataease/sqlbot
```

[1Panel App Store](https://apps.fit2cloud.com/1panel)를 통해서도 SQLBot을 빠르게 배포할 수 있습니다.

인트라넷을 사용하는 경우 [오프라인 설치 패키지](https://community.fit2cloud.com/#/products/sqlbot/downloads)를 사용하여 SQLBot을 배포할 수 있습니다.

### 접근 방법

- 브라우저에서 엽니다: http://<서버 IP>:8000/
- 사용자 이름: admin
- 비밀번호: SQLBot@123456



### UI

  <tr>
    <img width="1304" height="933" alt="image" src="https://github.com/user-attachments/assets/8d146b11-5e3f-423e-92db-d9938dd14cea" />
  </tr>

## 스타 역사

[![별 역사 차트](https://api.star-history.com/svg?repos=dataease/sqlbot&type=Date)](https://www.star-history.com/#dataease/sqlbot&Date)

## Feizhiyun의 다른 스타 프로젝트

- [DataEase](https://github.com/dataease/dataease/) - 모든 사람을 위한 오픈소스 BI 도구
  1패널 - 최신 오픈소스 Linux 서버 관리 및 운영 패널입니다.
- [MaxKB](https://github.com/1panel-dev/MaxKB/) - 강력하고 사용하기 쉬운 엔터프라이즈급 지능형 에이전트 플랫폼
- [JumpServer](https://github.com/jumpserver/jumpserver/) - 인기 있는 오픈 소스 요새 서버
- [Cordys CRM](https://github.com/1Panel-dev/CordysCRM) - 차세대 오픈소스 AI CRM 시스템
- [Halo](https://github.com/halo-dev/halo/) - 강력하고 사용하기 쉬운 오픈 소스 웹사이트 구축 도구
- [MeterSphere](https://github.com/metersphere/metersphere/) - 오픈 소스 지속적 테스트 도구의 새로운 세대

## 라이센스

이 저장소는 기본적으로 GPLv3이지만 몇 가지 추가 제한 사항이 있는 [FIT2CLOUD 오픈 소스 라이선스](LICENSE) 오픈 소스 계약을 따릅니다.

SQLBot 소스 코드를 기반으로 2차 개발을 수행할 수 있지만, 다음 규정을 준수해야 합니다.

- SQLBot 로고 및 저작권 정보는 교체하거나 수정할 수 없습니다.
- 2차 개발 후의 파생 저작물은 GPL V3의 오픈소스 의무를 준수해야 합니다.

제공해주신 소스들을 바탕으로 SQLBot 시스템에 대한 포괄적인 한국어 매뉴얼을 작성해 드립니다. SQLBot은 **대형 언어 모델(LLM)**과 **RAG(검색 증강 생성)** 기술을 기반으로 사용자의 자연어 질문을 SQL 쿼리로 변환하여 데이터 분석 및 시각화 결과를 제공하는 지능형 질의/응답 시스템입니다.



# SQLBot  매뉴얼

## I. SQLBot 개요

SQLBot은 DataEase 오픈소스 팀에서 개발되었으며, **텍스트-투-SQL(Text-to-SQL)** 변환 기능을 핵심으로 합니다. 특히, 버전 v1.2.0에서 한국어 현지화 내용이 업데이트되고 보완되었습니다.

### 주요 특징 및 장점
*   **쉬운 통합 (Easy Integration)**: n8n, MaxKB, Dify, Coze 등 다양한 AI 애플리케이션 개발 플랫폼에 빠르게 통합될 수 있도록 지원합니다.
*   **안전성 및 제어**: **워크스페이스 기반**의 리소스 격리 메커니즘을 제공하며, 세분화된 데이터 권한 설정을 통해 데이터 접근의 보안을 보장합니다.
*   **LLM 기반**: 강력한 자연어 이해 및 SQL 생성 능력을 활용하며, RAG 기술을 결합하여 생성 정확도를 높입니다.
*   **주요 기능**: 질의/응답 분석, 심층 탐색, 데이터 관리, 대시보드 구축 등을 지원합니다.

---

## II. 설치 및 접속

SQLBot은 1Panel, 온라인, 오프라인 등 다양한 방식으로 설치할 수 있으며, 설치 환경으로 Ubuntu 22.04 또는 CentOS 7 (커널 버전 ≥ 3.10), 4코어 8G CPU/메모리, 100G 디스크 공간을 권장합니다.

### 1. 1Panel을 이용한 설치
1Panel 설치 및 배포가 완료된 후, 애플리케이션 스토어에서 SQLBot 애플리케이션을 찾아 설치합니다.
*   설치 시 PostgreSQL이 설치되어 있어야 합니다.
*   **필수 설정**: SQLBot 애플리케이션 이름, **슈퍼 관리자 사용자명 및 비밀번호**.
*   **기본 포트**: SQLBot 서비스 포트는 **8000**, MCP 서비스 포트는 **8001**로 설정됩니다.

### 2. 온라인 설치 (Docker)
Docker 환경이 구성된 서버에서 다음 포트가 개방되어야 합니다:
| 포트 | 용도 | 설명 |
| :--- | :--- | :--- |
| **8000** | Web 서비스 포트 | 기본 웹 서비스 접근 포트 |
| **8001** | MCP 서비스 포트 | 기본 MCP 서비스 접근 포트 |
| 22 | SSH | 설치, 업그레이드 및 관리에 사용 |

### 3. ARM 온라인 설치
커뮤니티 버전은 공식 ARM 이미지를 제공하지 않으며, 개발 버전의 체험 이미지만 제공합니다.

### 4. 로그인 및 접속
설치에 성공하면 브라우저를 통해 **`http://[대상 서버 IP 주소]:8000`** 주소로 접속할 수 있습니다.
*   **기본 관리자 계정**:
    *   사용자 이름: **admin**
    *   기본 비밀번호: **SQLBot@123456**

---

## III. 핵심 기능 및 구성

SQLBot은 **[지능형 질의/응답]**, **[데이터 소스]**, **[대시보드]**, **[설정]**의 네 가지 핵심 모듈로 구성됩니다.

### 1. 지능형 질의/응답 (핵심 기능)
사용자가 자연어로 질문을 하면, 대규모 언어 모델(LLM)이 질문 의도를 파악하고 선택된 데이터 소스를 기반으로 차트와 분석 결과를 자동으로 생성합니다.

*   **대화 생성**: [새 대화] 버튼을 클릭하고 데이터 소스를 선택하여 시작합니다.
*   **자동 추천 질문**: 시스템은 현재 데이터 소스의 구조와 사용자의 과거 질의 기록을 기반으로 추천 질문을 자동으로 생성합니다.
*   **결과 활용**:
    *   **SQL 보기**: 모든 질의/응답에는 자동으로 생성된 **SQL 쿼리**가 표시되며, 이를 확인하고 복사할 수 있습니다.
    *   **심층 분석**: 생성된 차트의 **[데이터 분석]** 버튼을 클릭하면 LLM이 추세 분석 및 비즈니스 해석을 제공합니다.
    *   **데이터 예측**: 시계열 데이터(예: 월별, 분기별 데이터)를 기반으로 **[데이터 예측]** 기능을 통해 미래 지표 값을 예측할 수 있습니다.

### 2. 데이터 소스 관리
SQLBot의 분석 대상이 되는 다양한 데이터 연결 정보를 관리합니다.

*   **지원 데이터 소스 유형**:
    *   **OLTP**: MySQL, SQL Server, Oracle, PostgreSQL, 达梦(Dameng).
    *   **OLAP**: ClickHouse, Apache Doris.
    *   **데이터 웨어하우스/레이크**: AWS RedShift.
    *   **데이터 파일**: Excel/CSV.
*   **데이터 원본 설정**: 데이터 소스 유형을 선택하고, IP, 포트, 데이터베이스, 자격 증명(사용자 이름/비밀번호) 등을 입력하여 연결을 검증합니다.
*   **표 관계 관리**: 다중 테이블 쿼리 시 정확한 SQL 생성을 돕기 위해 데이터 소스 내 테이블 간의 **연관 관계**를 관리할 수 있습니다.
*   **필드 구조**: 데이터 소스 상세 페이지에서 테이블별 필드 구조를 확인하고, 지능형 질의 시 인식할 필드를 선택적으로 **활성화/비활성화**할 수 있습니다.

### 3. 대시보드
[지능형 질의/응답] 기능을 통해 생성된 여러 개의 차트를 모아 **사용자 정의 시각화 데이터 보드**를 구축할 수 있습니다.
*   사용자는 드래그 앤 드롭, 레이아웃 조정, 설명 추가 등을 통해 구조화된 데이터 시각화 보드를 만듭니다.

---

## IV. 고급 설정 및 관리

시스템 관리자는 [설정] 메뉴에서 사용자, 권한, AI 모델 등을 관리합니다.

### 1. AI 모델 설정
SQLBot은 DeepSeek등 주요 LLM과의 통합을 지원합니다.
*   **모델 추가**: 모델 제공업체를 선택하고, 모델 이름, API 주소, Key, 모델 매개변수(온도, 최대 응답 길이 등)를 설정하여 추가합니다.
*   **시스템 기본 모델**: 여러 모델이 구성된 경우, **시스템 기본 모델**을 설정하여 지능형 질의 시 호출할 기본 LLM을 지정할 수 있습니다.
*   **Ollama 통합**: Ollama로 배포된 모델(예: Qwen3)을 직접 연동하거나, DeepSeek R1처럼 OpenAI 인터페이스와 호환되지 않는 모델은 **One API**를 통해 변환하여 SQLBot에 연결할 수 있습니다.

### 2. 권한 및 정확도 향상 설정
*   **워크스페이스 관리**: 데이터 소스, 대화 기록, 대시보드 등의 리소스를 격리하고 권한을 분리하는 기본 단위입니다.
*   **권한 설정**: 데이터 접근 권한을 세밀하게 제어합니다.
    *   **규칙 그룹** 단위로 권한을 관리하며, 행 권한(특정 조건의 데이터만 보기) 및 열 권한(민감 정보 필드 숨기기)을 설정할 수 있습니다.
*   **용어 설정**: 비즈니스 도메인의 전문 용어, 설명, 동의어를 관리하여 LLM이 SQL을 생성할 때 정확도를 높이도록 돕습니다.
*   **SQL 예시 라이브러리**: 자주 묻는 질문과 해당 SQL 예시를 등록해두면, 사용자의 질문이 이에 매칭될 경우 예시 SQL을 LLM에 함께 전송하여 정확한 SQL을 생성하도록 지원합니다.
*   **사용자 정의 프롬프트**: (X-Pack 기능) LLM이 예상되는 SQL 쿼리, 데이터 분석, 데이터 예측 결과를 생성하도록 돕기 위해 사용자 지정 프롬프트(Prompt)를 설정할 수 있습니다.

### 3. 통합 및 확장성 (Embedding/MCP)
SQLBot의 지능형 질의/응답 기능을 외부 시스템에 통합할 수 있습니다.

*   **임베디드(Embedded) 방식**: **[소도우미 임베딩]** 또는 **[웹 페이지 임베딩]** 방식으로 외부 페이지에 통합됩니다.
    *   **기본 애플리케이션**: 백엔드 연동이 필요 없으며, 데이터 권한 설정이 간단합니다 (방문자/직원 권한).
    *   **고급 애플리케이션**: 데이터 권한 제어가 엄격하게 필요한 시나리오에 적합하며, SQLBot이 사용자 식별자를 비즈니스 시스템에 전달하면, 시스템이 사용자가 접근 가능한 데이터 소스 목록을 API 인터페이스를 통해 반환합니다.
*   **MCP 서비스 (Micro-service Chart Processing)**: 서버 측 차트 렌더링 및 지능형 질의 처리를 지원하는 서비스로, 기본 포트는 **8001**입니다.
    *   **활용**: MCP는 외부 AI 애플리케이션 개발 플랫폼(MaxKB, Dify, Coze 등)과의 대화형 통합을 위해 사용됩니다.
    *   **주요 도구**: `mcp_start` (인증 토큰 `access_token` 및 대화 ID `chat_id` 획득)와 `mcp_question` (획득한 토큰과 ID를 사용하여 질문 제출 및 SQL, 시각화 결과 반환)이 있습니다.

### 4. DataEase 연동
SQLBot v1.1.3 이상 버전은 DataEase v2.10.13 이상 버전에 접속하여 지능형 질의/응답 기능을 제공할 수 있도록 지원합니다.

*   SQLBot 플랫폼에서 **고급 애플리케이션**을 생성하고 DataEase 서비스의 접근 주소를 **크로스 도메인 설정**으로 지정해야 합니다.
*   DataEase 측에서는 관리자 계정으로 로그인 후 **[시스템 설정] > [시스템 매개변수] > [타사 임베디드]**에서 SQLBot 서버 URL과 고급 애플리케이션 ID를 입력하여 설정합니다.

---

