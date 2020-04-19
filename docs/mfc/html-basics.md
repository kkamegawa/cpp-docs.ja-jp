---
title: HTML の基礎
ms.date: 11/04/2016
helpviewer_keywords:
- HTML [MFC], about HTML
ms.assetid: aab8ea9f-12d4-4bdd-a585-ac3124081a2a
ms.openlocfilehash: 63a866786abc3b1eaa87a06492b43b1c9e354882
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62262997"
---
# <a name="html-basics"></a>HTML の基礎

ほとんどのブラウザーを参照するページの HTML ソースを調べるの機能があります。 HTML (ハイパー テキスト マークアップ言語) のタグ数が表示されます、ソースを表示するときに、山かっこ (<)、テキストが混在してで囲まれます。

以下の手順では、単純な Web ページを構築するのに HTML タグを使用します。 次の手順でメモ帳でファイルにプレーン テキストを入力、いくつかの変更を加える、ファイルを保存し、変更を確認するには、ブラウザーでページを再読み込みします。

#### <a name="to-create-an-html-file"></a>HTML ファイルを作成するには

1. メモ帳または任意のプレーン テキスト エディターを開きます。

1. **ファイル**] メニューの [選択**新規**します。

1. 次の行を入力します。

```
<HTML>
<HEAD>
<TITLE>Top HTML Tags</TITLE>
</HEAD>
</HTML>
```

1. **ファイル**] メニューの [選択**保存**、c:\webpages\First.htm としてファイルを保存します。 ファイルをエディターで開いたままにしておきます。

1. ブラウザーとの間の切り替え、**ファイル**] メニューの [選択**オープン**、または型*file://C:/webpages/first.htm*ブラウザーの URL の編集ボックス。 「最上位の HTML タグ」ウィンドウのキャプションを空白のページを参照する必要があります。

   タグは、ペアになるし、山かっこ内に含まれることを確認します。 タグは大文字小文字が区別されませんが、大文字と小文字はタグを目立たによく使用されます。

   タグ\<HTML >、ドキュメントとタグの開始\</HTML > で終了します。 (必須では常にではありません)、終了タグは、開始タグと同じですが、タグの前にスラッシュ (/) です。 山かっこ (<) と、タグの先頭のスペースいけません。

1. メモ帳に戻ると、後のスイッチ、 \</head > 行に、入力します。

```
<BODY>
    HTML is swell.
    Life is good.
</BODY>
```

1. **ファイル**] メニューの [選択**保存**します。

1. お使いのブラウザーに戻り、ページを更新します。

   ブラウザーのウィンドウのクライアント領域内の単語が表示されます。 キャリッジ リターンは無視されることに注意してください。 改行がある場合は、する必要があります、`<BR>`最初の行の後にタグ。

   すべての手順に従って、任意の場所の間でテキストを挿入する\<本文 > と \< /BODY >、ドキュメントの本文に追加します。

9. ヘッダーを追加します。

```
<H3>Here's the big picture</H3>
```

10. ページと同じディレクトリに保存されている .gif ファイルを使用して、イメージを追加します。

```
<IMG src="yourfile.gif">
```

11. 一覧を追加します。

```
<UL>Make me an unordered list.
<LI>One programmer</LI>
<LI>Ten SDKs</LI>
<LI>Great Internet Apps</LI>
</UL>
```

12. 番号のリストの代わりを使用して、ペアになっている\<OL > と\</OL > タグの代わりに、 \<UL > と\</UL > タグです。

作業を開始するを取得する必要があります。 Web ページで、優れた機能を表示する場合、HTML ソースを調べることによって作成されたかを確認できます。 Microsoft フロント ページなどの HTML エディターは、単純かつ高度なページの作成に使用できます。

HTML ソースを構築してきたファイル全体を次に示します。

```
<HTML>
<HEAD>
<TITLE>Top HTML Tags</TITLE>
</HEAD>
<BODY>
HTML is swell.<BR>
Life is good.
<H3>Here's the big picture</H3>
<IMG src="yourfile.gif">
<UL>Make me an unordered list.
<LI>One programmer</LI>
<LI>Ten SDKs</LI>
<LI>Great Internet Apps</LI>
</UL>
</BODY>
</HTML>
```

タグ、属性、および拡張機能の詳細については、ハイパー テキスト マークアップ言語 (HTML) 仕様を参照してください。

[公開された最新バージョンの HTML](https://www.w3.org/TR/html/) W3C.org にします。

## <a name="see-also"></a>関連項目

[MFC インターネット プログラミングの基礎](../mfc/mfc-internet-programming-basics.md)
