# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

`top`（Anfini AIXポータル）は静的な単一ページ（`lineup/index.html`）で、他の社内アプリへのリンク集を表示する。**Cloudflare Pages**でホストしており、このリポジトリのフォルダ構造がそのままURLパスに対応する（`lineup/index.html` → `/lineup`）。カスタムドメインはルートドメイン `anfini-aix.com` そのものに設定してあるため、`https://anfini-aix.com/lineup` で配信される。ビルドコマンドは無し（静的ファイルをそのまま配信）。Deploys go through Cloudflare Pages connected to this repo's `main` branch — pushing to `main` ships to production（プレビューデプロイも自動で作られる）。

以前はGitHub Pagesで配信していたが、GitHub Pagesはドメイン/サブドメイン単位でしかカスタムドメインを設定できず、`anfini-aix.com` 直下の `/lineup` というパスだけに配信することができなかったため、Cloudflare Pagesに移行した。

## Working conventions

- All comments and user-facing strings are in Japanese; match that when editing.
- 新しいページ・ツールを `anfini-aix.com` 直下の別パスに追加したくなったら、`lineup/` と同じ要領でリポジトリ直下に新しいフォルダを作りその中に `index.html` を置けば、Cloudflare Pages側の追加設定なしにそのパスで配信される。
- 他のアプリ（recruitment-dashboard・contract-creation・personal-message-generator・event-participant-management）へのリンクは、それぞれの `anfini-aix.com` サブドメインを指すこと。
