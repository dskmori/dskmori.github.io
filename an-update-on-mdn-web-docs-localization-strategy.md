これは、Mozilla Hacks に 2020 年 12 月 8 日に投稿された [An update on MDN Web Docs’ localization strategy](https://hacks.mozilla.org/2020/12/an-update-on-mdn-web-docs-localization-strategy/) の翻訳です。

---

以前の投稿 — [MDN Web Docs evolves! Lowdown on the upcoming new platform](https://hacks.mozilla.org/2020/10/mdn-web-docs-evolves-lowdown-on-the-upcoming-new-platform/) — で、2020 年 12 月 14 日にリリースする新しい MDN Web Docs プラットフォームの多くの特徴について解説しました。この投稿では、さらに詳しいもう 1 つの特徴 — 今後のローカライズの扱い — を紹介します。以前の投稿以後、我々の思考がどのように変化していったかを説明し、最新のアクションについても詳説します。

# 最新のアクション
コミュニティからのフィードバックに基づいて、追加調査を行い確固たる道のりを決定しました。

まず、新しいプラットフォームのリリースを先導することに明確な焦点を当てます。そして、システム全体がスムーズに動作することを確認します。これは、リリース後も既存のすべてのロケールで翻訳を表示する計画であることを意味します。しかし、最初はすべて凍結 — 読み取り専用で編集不可 — されています。

また、今後の主要な手段として、自動翻訳を検討して _いました_。鍵となる問題は、欧州地域の言語への自動翻訳は甘受できる一方で、[CJK](https://en.wikipedia.org/wiki/CJK_characters) 言語は理想とはかけ離れているものということでした。CJK 言語は、英語や欧州地域の言語とまったく異なる構造を持つことに加え、多くの欧州人は必要に応じて英語で読む力が十分にあるのに対し、CJK コミュニティは英語を通常使用しないという問題があります。

私が会話した多くの人は、自動翻訳は CJK 言語では受け入れられないといいました。また、受け入れの基準に満たないだけでなく、MDN Web Docs コミュニティの多くが文書を翻訳しています。手動翻訳の手段を破棄した場合、これらの精力的なコミュニティもどこかへ行ってしまうでしょう。これは、我々が避けなくてはならないことです。

そのため、制約付きの手動翻訳を今後の手段とすることにして、新しいプラットフォームのリリース後可能な限り早く、主要なロケールの凍結を解除するつもりです。

# 制約付きの手動翻訳
厳格なテストを終え、メインのビルドプロセスの一部として、翻訳されたコンテンツをビルドできるようになっています。ロケールを 2 つの Tier に分け、どれを凍結解除し、どれを凍結維持するか決定しました。

- Tier 1 ロケールは、凍結を解除して、pull request により手動編集を行えるようになります。これらのロケールは、コミュニティを牽引する代表者が **少なくとも** 1 人必須です。コミュニティメンバーは、ローカライズされたページを適時確認し、英語バージョンが変更されたら主要コンテンツの翻訳を更新、レビューなどを行う責任があります。
- Tier 2 ロケールは、凍結され、pull request も受け付けられません。そのため、コミュニティによる維持は行われません。

凍結解除が行われる Tier 1 ロケールは、まずは以下のものとなります:

- 簡体中国語 (zh-CN)
- 繁体中国語 (zh-TW)
- フランス語 (fr)
- 日本語 (ja)

Tier 2 ロケールを凍結解除したい場合、そのロケールに関する作業に関してアクティブなチームが責任を持つ証拠とともに我々に [要求を出してください](https://developer.mozilla.org/en-US/docs/MDN/Contribute/Getting_started#Step_4_Ask_for_help)。この場合に限り、そのロケールは Tier 1 に昇格し、作業を行えるようになります。

Tier 1 ロケールは監視され、コミュニティによる維持が行われていない場合、一定期間の後、Tier 2 に降格します。そして、再び凍結されます。

新しいシステムの適度な妥協点であると考えています — コミュニティが MDN の翻訳作業を続けられて、ロケールの維持ができて、コンテンツが古くならない方法を提供しています。多くのロケールが維持されておらず、変更に対するレビューが効果的に行われていませんでした。また、そのロケールにおける読み手側も、英語との差異に混乱していました。これは、結果として最悪なものです。

# レビュープロセス
レビュープロセスはとても単純です。

- Tier 1 ロケールは個別の repo 内で管理されます。
- repo 内で PR (pull request) が行われるとローカライズコミュニティにレビュー依頼が通知されます。
- コンテンツがレビューされると、MDN 管理者に変更のマージ依頼が通知されます。このプロセスは自動で行われるようにシステムを設計する必要があります。
- Github の https://github.com/mdn/sprints/issues に登録されたコンテンツに関するバグも同様に各ロケールの repo で管理されるようになります。優先順位付けされた “sprints” の issues は、適切なローカライズチームに割り当てられますが、その issues の取り扱いは各 repo で責任を負うことになります。

# 機械翻訳と手動翻訳について
新しいローカライズプロセスの拡張として機械翻訳の可能性について話しました。我々はまだそれを忘れたわけではありませんが、システムの初期段階としてシンプルにすることにしました。2021 年の第 1四半期のステップで、機械翻訳を効果的に使用する方法を探し始めます。進捗があれば、同四半期中にお知らせします。

---
Content available under a [Creative Commons license](https://creativecommons.org/licenses/by-sa/3.0/deed.ja) that the original content follows.