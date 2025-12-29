# 🚀 Total SQLi Exploit Suite v6.0 (Enterprise Edition)

이 프로젝트는 웹 보안 전문가를 위한 **고도화된 SQL Injection 통합 프레임워크**입니다. 단순한 취약점 스캔을 넘어, 최신 WAF 우회 기법, 멀티스레딩 기반의 고속 데이터 추출, 그리고 **인증 체계 무력화** 엔진을 탑재하고 있습니다.

---

## 🔥 핵심 업데이트 및 탑재 기술

### 1. Authentication Bypass (로그인 우회) - NEW
- **논리 조작**: `OR '1'='1'` 등의 논리적 참(True) 상태를 유도하여 ID/PW 검증 절차를 무력화합니다.
- **주석 기법**: `--`, `#` 등을 활용하여 백엔드 DB의 비밀번호 확인 쿼리를 강제로 주석 처리합니다.



### 2. HTTP Parameter Pollution (HPP) 우회
- **메커니즘**: 동일한 파라미터 키를 중복 전송(`?id=35&id=PAYLOAD`)하여 보안 장비(WAF)의 검사를 우회합니다.
- **StealthNet**: `requests` 라이브러리의 튜플 리스트 구조를 활용하여 백엔드 DB만 공격 페이로드를 인식하게 설계되었습니다.

### 3. 하이퍼 스피드 Blind 엔진 (Multi-threading)
- **이진 탐색(Binary Search)**: 한 문자당 최대 7번의 요청으로 모든 ASCII 문자를 판별합니다.
- **병렬 처리**: `ThreadPoolExecutor`를 통해 8개 이상의 비트를 동시에 탐색하여 추출 시간을 획기적으로 단축했습니다.

### 4. 실시간 제어 인터럽트 (Ctrl+X)
- **추출 스킵**: Blind 추출 도중 `Ctrl+X` 입력 시 현재 테이블/데이터 추출을 즉시 중단하고 다음 타겟으로 안전하게 제어권을 넘깁니다.
- **권한 필요**: 키보드 인터럽트 감지를 위해 실행 환경의 관리자 권한이 권장됩니다.

---

## 🛠 공격 모드 상세 가이드

```text
1. Union-Based: 컬럼 수 자동 탐색 및 Hex 인코딩을 통한 광속 데이터 덤프
2. Error-Based: XPath(ExtractValue) 문법 에러 유도를 통한 정밀 추출
3. Blind (Boolean): 응답 본문의 참/거짓 지표(True Indicator) 기반 추론
4. Blind (Time): SLEEP 함수를 이용한 응답 지연 기반 추론 (강력한 은신 공격)
5. Auth-Bypass: 아이디/비밀번호 없이 관리자 계정 권한 탈취
```

---

## 📋 설치 및 실행 환경 구축

```bash
# 1. 필수 라이브러리 설치
pip install requests tabulate keyboard

# 2. 실행 (관리자 권한 권장)
python Total_Exploit.py
```

---

## 📂 프로젝트 구조 명세

```python
# 주요 엔진 구성
class StealthNet:           # HPP 및 User-Agent 로테이션 처리
class DiagnosticEngine:     # 3대 SQLi 취약점 자동 판별
class AuthBypassEngine:     # 로그인 인증 우회 특화 모듈 (v6.0)
class StealthUnionEngine:   # Hex-wrapped Union 공격 모듈
class ErrorBasedEngine:     # XPath Error Induction 모듈
class BlindExploitEngine:   # Multi-thread + Ctrl+X 인터럽트 엔진
class IntegratedExploit:    # 사용자 인터페이스 및 통합 제어 로직
```

---

## ⚠️ 법적 면책 조항 (Disclaimer)

본 도구는 오직 **교육적 목적 및 인가된 보안 진단**을 위해 제작되었습니다. 승인되지 않은 대상에 대한 사용은 엄격히 금지되며, 이로 인해 발생하는 모든 법적 책임은 사용자 본인에게 있습니다.

---

**Last Updated**: 2025-12-24 (Enterprise Edition)  
**Developer**: Gemini (Strategic Partner)
