# Gatherly Feed Directory

iOS 앱 **[Gatherly — 쉬운 RSS 리더](https://apps.apple.com/app/id6756641122)** 의 추천 피드 디렉터리입니다.
앱의 Discover 화면에서 보여주는 추천 RSS 피드 목록을 자동으로 갱신·게시합니다.

> The recommended RSS feed directory for **[Gatherly — Easy RSS Reader](https://apps.apple.com/app/id6756641122)**, an iOS app.
> This repository auto-publishes the feed list shown in the app's Discover screen.

## 📱 Gatherly

구독한 피드를 한 곳에서 읽고, 트렌딩 콘텐츠와 새로운 피드를 발견하는 RSS 앱.
URL만 입력하면 자동으로 피드를 찾아 구독합니다. 복잡한 설정이 없어요.

→ **App Store: https://apps.apple.com/app/id6756641122**

## 📂 Files

| 파일 | 설명 |
|---|---|
| [`feed-directory.json`](feed-directory.json) | 추천 피드 전체 번들 (`{ generated_at, feeds[] }`) |
| [`manifest.json`](manifest.json) | 갱신 확인용 메타데이터 (스키마 버전 / 해시 / 생성 시각) |

### `manifest.json`

```json
{
  "schemaVersion": 1,
  "generatedAt": "20260530025815",
  "feedCount": 2893,
  "contentHash": "<sha256 of feeds content, timestamp-independent>",
  "bundle": {
    "path": "feed-directory.json",
    "bytes": 982918,
    "sha256": "<sha256 of feed-directory.json bytes>"
  }
}
```

- **`contentHash`**: 피드 내용만의 해시 (생성 시각 영향 없음). 앱은 이 값이 바뀌었을 때만
  `feed-directory.json` 전체를 내려받습니다. (대역폭 절약 — manifest-poll 패턴)
- **`bundle.sha256`**: 내려받은 파일 바이트의 해시. 다운로드 무결성 검증용.

앱은 작은 `manifest.json` 만 주기적으로 폴링합니다.

## 🔄 Updates

- GitHub Actions가 **하루 1회** 자동 수집·검증 후, 내용이 바뀐 경우에만 이 저장소를 갱신합니다.
- 게시 URL:
  - **권장 CDN (jsDelivr)**: `https://cdn.jsdelivr.net/gh/genkino/gatherly-feed-directory@main/feed-directory.json`
  - **raw GitHub (직접 원본)**: `https://raw.githubusercontent.com/genkino/gatherly-feed-directory/main/feed-directory.json`
  - manifest: 위 URL에서 파일명만 `manifest.json` 으로 교체

## ⚠️ Usage Guidance

- 이 저장소는 **공개 저장소**이므로 누구나 파일을 조회할 수 있습니다.
- 다만 `raw.githubusercontent.com` 원본 URL을 앱이나 서비스에서 대규모로 직접 참조하면,
  트래픽이 원본 호스트에 집중되어 속도·안정성·캐시 효율 측면에서 불리할 수 있습니다.
- **프로덕션 환경에서는 raw GitHub 대신 CDN URL 또는 서비스 운영자가 직접 관리하는 캐시/미러를 사용해 주세요.**
- Gatherly 앱도 원본 저장소를 직접 폴링하지 않고, 캐시 계층을 둔 URL을 통해 디렉터리를 참조합니다.
- `raw.githubusercontent.com` URL은 사람이 내용을 확인하거나, 소규모 테스트/디버깅 용도로만 사용하는 것을 권장합니다.

> This repository is public, but direct high-volume use of `raw.githubusercontent.com`
> is discouraged. For production use, please use a CDN or your own caching layer
> instead of hitting the origin directly.

## 📜 License

- **데이터(피드 목록)**: [CC0 1.0 Universal](LICENSE) (퍼블릭 도메인 헌정) — 자유롭게 사용 가능.
- 단, 각 피드가 제공하는 **콘텐츠의 저작권은 원저작자에게 있습니다.** 이 저장소는 공개된
  RSS/Atom 피드 URL과 그 메타데이터의 모음만 제공합니다.

> **Data (the feed list)** is released under [CC0 1.0](LICENSE). Copyright of the content
> served by each feed remains with its original authors. This repository only aggregates
> publicly available RSS/Atom feed URLs and their metadata.
