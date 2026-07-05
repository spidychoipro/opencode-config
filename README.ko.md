<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/spidychoipro/spidychoipro/main/assets/logo-dark.svg">
    <img src="https://opencode.ai/opencode.svg" width="120" alt="opencode logo"/>
  </picture>
</p>

<h1 align="center">🕷️ opencode-config</h1>

<p align="center">
  <strong>프로덕션급 Opencode AI CLI 설정</strong><br>
  <em>bkit PDCA · NSP · Karpathy 가이드라인 · 커스텀 에이전트 · 크로스플랫폼</em>
</p>

<p align="center">
  <a href="#-features"><img src="https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fapi.github.com%2Frepos%2Fspidychoipro%2Fopencode-config&query=%24.stargazers_count&style=flat-square&label=%E2%AD%90%20stars&color=yellow" alt="Stars"></a>
  <a href="https://github.com/spidychoipro/opencode-config/blob/main/README.ko.md"><img src="https://img.shields.io/badge/platform-windows%20%7C%20macos%20%7C%20linux-2f81f7?style=flat-square" alt="Platform"></a>
  <a href="https://opencode.ai"><img src="https://img.shields.io/badge/opencode-1.0%2B-6c5ce7?style=flat-square" alt="opencode"></a>
  <a href="https://github.com/spidychoipro/opencode-config/blob/main/LICENSE"><img src="https://img.shields.io/badge/license-MIT-brightgreen?style=flat-square" alt="License"></a>
  <a href="README.md"><img src="https://img.shields.io/badge/lang-English-blue?style=flat-square" alt="English"></a>
</p>

<br>

## 📋 목차

- [기능](#-기능)
- [시작하기](#-시작하기)
- [포함된 기능](#-포함된-기능)
- [사용법](#-사용법)
- [커스텀 에이전트](#-커스텀-에이전트)
- [스킬 목록](#-스킬-목록)
- [프로젝트 구조](#-프로젝트-구조)
- [커스터마이징](#-커스터마이징)
- [문제 해결](#-문제-해결)
- [라이선스](#-라이선스)

<br>

## ✨ 기능

<table>
  <tr>
    <td width="50%">
      <h3>🧠 bkit PDCA + NSP</h3>
      <p>Plan-Design-Do-Analyze-Report 사이클의 문서 기반 개발. 모든 단계에서 Negative Space Programming으로 하지 말아야 할 것을 정의합니다.</p>
    </td>
    <td width="50%">
      <h3>🎯 Karpathy 가이드라인</h3>
      <p>정밀한 코드 변경, 불필요한 리팩토링 금지, 최소 diff, 읽기-전에-수정 원칙. 모든 작업에 최소한의 변경만 적용합니다.</p>
    </td>
  </tr>
  <tr>
    <td width="50%">
      <h3>🤖 커스텀 에이전트</h3>
      <p>워크플로 관리와 갭 분석을 위한 <code>bkit-pdca</code>, <code>bkit-analyzer</code> 서브에이전트가 미리 구성되어 있습니다.</p>
    </td>
    <td width="50%">
      <h3>🔒 안전 최우선</h3>
      <p>VibeGuard 보호, 권한 규칙, 충돌 해결 우선순위 — 명시적 사용자 요청 > 안전 > NSP > PDCA > Karpathy.</p>
    </td>
  </tr>
  <tr>
    <td width="50%">
      <h3>🖥️ 크로스플랫폼</h3>
      <p>Windows, macOS, Linux에서 동일하게 작동. 플랫폼별 해킹 없음 — 모든 지침이 경로에 독립적입니다.</p>
    </td>
    <td width="50%">
      <h3>📦 10+ 내장 스킬</h3>
      <p>PDCA, 코드 리뷰, 풀스택 개발, 엔터프라이즈 아키텍처, 모바일 앱, 데스크톱 앱, 배포, SEO 등.</p>
    </td>
  </tr>
</table>

<br>

## 🚀 시작하기

### 1. Opencode 설치

플랫폼에 맞게 선택하세요:

<table>
  <tr>
    <th>플랫폼</th>
    <th>명령어</th>
  </tr>
  <tr>
    <td><b>macOS</b></td>
    <td><code>brew install opencode</code></td>
  </tr>
  <tr>
    <td><b>Linux</b></td>
    <td><code>npm install -g @opencode/cli</code></td>
  </tr>
  <tr>
    <td><b>Windows</b></td>
    <td><code>winget install opencode</code> 또는 <code>npm install -g @opencode/cli</code></td>
  </tr>
  <tr>
    <td><b>모든 플랫폼 (npm)</b></td>
    <td><code>npm install -g @opencode/cli</code></td>
  </tr>
</table>

### 2. 이 설정 복제

<details>
<summary><b>macOS / Linux</b></summary>

```bash
# opencode 설정 디렉토리에 직접 복제
git clone https://github.com/spidychoipro/opencode-config.git ~/.config/opencode

# 또는 별도 디렉토리에 복제 후 심볼릭 링크
git clone https://github.com/spidychoipro/opencode-config.git ~/opencode-config
ln -sf ~/opencode-config/opencode.jsonc ~/.config/opencode/opencode.jsonc
```
</details>

<details>
<summary><b>Windows (PowerShell 7+)</b></summary>

```powershell
# 사용자 홈 디렉토리에 복제
git clone https://github.com/spidychoipro/opencode-config.git "$env:USERPROFILE\opencode-config"

# 설정 파일 복사
Copy-Item -Path "$env:USERPROFILE\opencode-config\opencode.jsonc" -Destination "$env:USERPROFILE\.config\opencode\opencode.jsonc"
```
</details>

<details>
<summary><b>Windows (CMD)</b></summary>

```cmd
git clone https://github.com/spidychoipro/opencode-config.git %USERPROFILE%\opencode-config
copy %USERPROFILE%\opencode-config\opencode.jsonc %USERPROFILE%\.config\opencode\opencode.jsonc
```
</details>

### 3. 확인

```bash
opencode --version
# opencode CLI 버전이 표시됩니다
```

끝입니다. 별도 설정이 필요 없습니다 — 모든 에이전트, 스킬, 워크플로가 이미 구성되어 있습니다.

<br>

## 📦 포함된 기능

### 🧭 워크플로 시스템 (PDCA + NSP)

| 단계 | 설명 |
|-------|------|
| 📋 **Plan** | NSP 제약 조건과 함께 계획 문서 작성 |
| 🎨 **Design** | 명시적 경계를 포함한 아키텍처 설계 |
| ⚡ **Do** | Karpathy 정밀 코딩 원칙으로 구현 |
| 🔍 **Analyze** | 설계 대비 갭 분석 + NSP 준수 여부 확인 |
| 📝 **Report** | 일치율이 포함된 완료 보고서 |

모든 단계에서 **Negative Space Programming**을 적용합니다: 하지 말아야 할 것, 피해야 할 안티패턴, 사용하지 말아야 할 기술, 범위 외 항목, 경계, 연기된 엣지 케이스를 정의합니다.

### 🛡️ Karpathy 코딩 표준

| 규칙 | 설명 |
|------|------|
| 📖 먼저 읽기 | 변경 전에 기존 코드를 먼저 확인 |
| 🏗️ 아키텍처 유지 | 명시적 지시 없이 구조 변경 금지 |
| ✂️ 최소 diff | 가장 작은 변경만 — 불필요한 정리 금지 |
| 🔬 추측 금지 | API를 확인하고, 동작을 가정하지 않음 |
| ❓ 모호하면 질문 | 돌이킬 수 없는 결정 전에 명확히 질문 |
| 🎯 집중 유지 | 요청한 작업만 수행, 그 이상 하지 않음 |

<br>

## 🎮 사용법

```bash
# PDCA 세션 시작
opencode

# 세션 내에서 PDCA 명령어 사용:
# $pdca plan     — 계획 문서 작성
# $pdca design   — 설계 문서 작성
# $pdca do       — 구현 시작
# $pdca analyze  — 갭 분석 실행
# $pdca report   — 완료 보고서 생성

# 스킬 직접 사용:
# $skill bkit-rules   — bkit 상세 규칙 참조
# $skill code-review  — 자동화된 코드 리뷰 실행
```

<br>

## 🤖 커스텀 에이전트

이 설정에는 두 개의 사전 구성된 서브에이전트가 포함되어 있습니다:

### `bkit-pdca`
- **모드:** 서브에이전트
- **역할:** 전체 PDCA 사이클 관리자
- **기능:** 기능 계획, 설계, 구현, 분석, 보고
- **NSP 적용:** 모든 단계에 Negative Space Programming 포함

### `bkit-analyzer`
- **모드:** 서브에이전트 (읽기 전용)
- **역할:** 갭 분석 전문가
- **기능:** 설계 문서와 구현을 비교, NSP 위반 감지
- **권한:** 편집 거부 — 분석 전용

<br>

## 🧩 스킬 목록

| 스킬 | 목적 | 사용법 |
|-------|---------|---------|
| `$pdca` | PDCA 사이클 관리 | `$pdca plan`, `$pdca analyze` |
| `$bkit-rules` | bkit 상세 규칙 | `$bkit-rules` |
| `$bkit-templates` | PDCA 문서 템플릿 | `$bkit-templates` |
| `$code-review` | 코드 품질 & 보안 감사 | `$code-review` |
| `$development-pipeline` | 9단계 개발 파이프라인 | `$development-pipeline` |
| `$plan-plus` | 브레인스토밍 강화 계획 | `$plan-plus` |
| `$starter` | 정적 웹 개발 | `$starter` |
| `$dynamic` | 풀스택 BaaS 개발 | `$dynamic` |
| `$enterprise` | 엔터프라이즈 마이크로서비스 | `$enterprise` |
| `$desktop-app` | Electron/Tauri 데스크톱 앱 | `$desktop-app` |
| `$mobile-app` | React Native/Flutter 앱 | `$mobile-app` |
| `$phase-*` | 9단계 파이프라인 스킬 | `$phase-1-schema` ... |

<br>

## 📁 프로젝트 구조

```
~/.config/opencode/
└── opencode.jsonc          # 인라인 지침이 포함된 메인 설정 파일
```

전체 설정이 단일 `opencode.jsonc` 파일에 자체 포함되어 있습니다. 관리할 외부 마크다운 파일이 없습니다.

<br>

## 🎨 커스터마이징

`~/.config/opencode/opencode.jsonc`를 편집하여 다음을 변경할 수 있습니다:

- **플러그인 추가**: `"plugin"` 배열 수정
- **새 에이전트 생성**: `"agent"` 객체에 항목 추가
- **권한 변경**: `"permission"` 섹션 업데이트
- **지침 수정**: `"instructions"` 배열 편집

변경 후 opencode를 다시 시작하면 적용됩니다.

<br>

## 🔧 문제 해결

| 문제 | 해결 방법 |
|---------|----------|
| 설정이 로드되지 않음 | 파일이 OS에 맞는 올바른 경로에 있는지 확인 |
| 에이전트를 찾을 수 없음 | `opencode.jsonc`의 `"agent"` 섹션 확인 |
| 스킬이 작동하지 않음 | `$skill code-review`로 테스트 |
| 권한 거부됨 | 설정의 `"permission"` 섹션 확인 |

<br>

## 📄 라이선스

MIT © [spidychoipro](https://github.com/spidychoipro)

---

<p align="center">
  <sub><a href="https://github.com/spidychoipro">spidychoipro</a>이(가) ❤️와 🕷️로 만들었습니다</sub>
</p>
