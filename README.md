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
  "bundle": {
    "path": "feed-directory.json",
    "bytes": 982918,
    "sha256": "cc75954d9cc071bb1f645d72d2e22da3ae11d29f81fdc5881808763e14aae333"
  }
}
```

앱은 작은 `manifest.json` 만 주기적으로 폴링하고, `bundle.sha256` 가 바뀌었을 때만
`feed-directory.json` 전체를 내려받습니다. (대역폭 절약 — manifest-poll 패턴)

## 🔄 Updates

- GitHub Actions가 **하루 1회** 자동 수집·검증 후, 내용이 바뀐 경우에만 이 저장소를 갱신합니다.
- 게시 URL:
  - **raw**: `https://raw.githubusercontent.com/genkino/gatherly-feed-directory/main/feed-directory.json`
  - **CDN (jsDelivr)**: `https://cdn.jsdelivr.net/gh/genkino/gatherly-feed-directory@main/feed-directory.json`
  - manifest: 위 URL에서 파일명만 `manifest.json` 으로 교체

## 📜 License

- **데이터(피드 목록)**: [CC0 1.0 Universal](LICENSE) (퍼블릭 도메인 헌정) — 자유롭게 사용 가능.
- 단, 각 피드가 제공하는 **콘텐츠의 저작권은 원저작자에게 있습니다.** 이 저장소는 공개된
  RSS/Atom 피드 URL과 그 메타데이터의 모음만 제공합니다.

> **Data (the feed list)** is released under [CC0 1.0](LICENSE). Copyright of the content
> served by each feed remains with its original authors. This repository only aggregates
> publicly available RSS/Atom feed URLs and their metadata.
