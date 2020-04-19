---
title: カスタム ビルド ステップまたはビルド イベントの出力の書式設定
ms.date: 08/27/2018
helpviewer_keywords:
- builds [C++], build events
- custom build steps [C++], output format
- events [C++], build
- build events [C++], output format
- build steps [C++], output format
- builds [C++], custom build steps
ms.assetid: 92ad3e38-24d7-4b89-90e6-5a16f5f998da
ms.openlocfilehash: b0e9a7514704742524f97e55c06ef47c7b36631b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62195369"
---
# <a name="formatting-the-output-of-a-custom-build-step-or-build-event"></a>カスタム ビルド ステップまたはビルド イベントの出力の書式設定

カスタム ビルド ステップまたはビルド イベントの出力形式が正しい場合、ユーザーには次の利点があります。

- 警告とエラーが、**[出力]** ウィンドウにカウントされます。

- 出力が、**[タスク一覧]** ウィンドウに表示されます。

- **[出力]** ウィンドウの出力をクリックすると、該当するトピックが表示されます。

- **[タスク一覧]** ウィンドウまたは **[出力]** ウィンドウでは、F1 キーの操作を使用できます。

出力形式は、次のとおりです。

> {<em>filename</em>**(**<em>line#</em> \[**,** <em>column#</em>]**)** &#124; *toolname*} **:** \[ <em>any text</em> ] {**error** &#124; **warning**} <em>code+number</em>**:**<em>localizable string</em> \[ <em>any text</em> ]

この場合、

- {*a* &#124; *b*} には、*a* または *b* を選択します。

- \[<em>項目</em>] は任意の文字列またはパラメーターです。

- **太字**はリテラルを表します。

例:

> C:\\*sourcefile.cpp*(134) : エラー C2143: 構文エラー: ';' が '}' の前にありません
>
> LINK : 致命的なエラー LNK1104: '*somelib.lib*' を開くことができません。

## <a name="see-also"></a>関連項目

[カスタム ビルド ステップとビルド イベントについて](understanding-custom-build-steps-and-build-events.md)