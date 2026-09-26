# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

`top`（Anfini AIXポータル）は元々GitHub Pagesで配信していた単一の静的ページ（`index.html`）だが、`anfini-aix.com/lineup` というルートドメイン配下のパスで配信する必要があるため、Cloudflare Workerとして配信するように変更した（GitHub Pagesのカスタムドメインはドメイン/サブドメイン単位でしか設定できず、パス単位では配信できないため）。`top.js` が実際にデプロイされる単一ファイルWorker本体で、`index.html` の中身をそのまま `PAGE_HTML` として埋め込み、`/lineup` と `/lineup/` にだけ応答する。`index.html` 自体は編集用のソースとして残しているが、**編集したら必ず `top.js` 側の `PAGE_HTML` にも反映すること**（自動同期はない）。

`wrangler.toml` の `[[routes]]` で `anfini-aix.com/lineup*` にルートを絞っており、ルートドメインの他のパスには一切関与しない。Deploys go through Cloudflare Workers Builds connected to this repo's `main` branch.

## Working conventions

- All comments and user-facing strings are in Japanese; match that when editing.
- `index.html` を直接編集した場合は、バックティック(`` ` ``)と `${` をエスケープした上で `top.js` の `PAGE_HTML` テンプレートリテラルに反映する（`index.html` 内の既存のJSテンプレートリテラルと、`top.js` 自身のテンプレートリテラルが衝突しないようにするため）。
- 他のアプリ（recruitment-dashboard・contract-creation・personal-message-generator・event-participant-management）へのリンクは、それぞれの `anfini-aix.com` サブドメインを指すこと。
