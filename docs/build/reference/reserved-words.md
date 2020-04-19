---
title: 予約語
ms.date: 11/04/2016
f1_keywords:
- code
- CONFORMING
- DISCARDABLE
- Description
- base
- APPLOADER
- Data
- DYNAMIC
- DEV386
helpviewer_keywords:
- .def files [C++], reserved words
- def files [C++], reserved words
- linker [C++], reserved words
- reserved words [C++]
ms.assetid: 9b9f49e5-0739-45ab-a37e-81e3915ceb25
ms.openlocfilehash: 7d51f599dfb81dfa860e1bdba86c4372e80379fb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62319422"
---
# <a name="reserved-words"></a>予約語

次の単語は、リンカーによって予約されています。 これらの名前を引数として使用できる[モジュール定義ステートメント](module-definition-dot-def-files.md)名前が二重引用符で囲まれている場合にのみ ("")。

||||
|-|-|-|
|**APPLOADER**<sup>1</sup>|**INITINSTANCE**<sup>2</sup>|**事前読み込み**|
|**ベース**|**に対しては IOPL**|**プライベート**|
|**コード**|**ライブラリ**<sup>1</sup>|**PROTMODE**<sup>2</sup>|
|**準拠**|**LOADONCALL**<sup>1</sup>|**純粋な**<sup>1</sup>|
|**データ**|**LONGNAMES**<sup>2</sup>|**READONLY**|
|**説明**|**移動可能な**<sup>1</sup>|**READWRITE**|
|**DEV386**|**MOVEABLE**<sup>1</sup>|**リアルモード**<sup>1</sup>|
|**破棄できます。**|**複数**|**常駐**|
|**DYNAMIC**|**NAME**|**RESIDENTNAME**<sup>1</sup>|
|**EXECUTE-ONLY**|**NEWFILES**<sup>2</sup>|**セクション**|
|**EXECUTEONLY**|**NODATA**<sup>1</sup>|**セグメント**|
|**読み取り**|**NOIOPL**<sup>1</sup>|**共有**|
|**EXETYPE**|**NONAME**|**1 つ**|
|**エクスポート**|**準拠していない**<sup>1</sup>|**スタックサイズ**|
|**固定**<sup>1</sup>|**NONDISCARDABLE**|**スタブ**|
|**関数**<sup>2</sup>|**NONE**|**バージョン**|
|**ヒープサイズ**|**非共有**|**WINDOWAPI**|
|**インポート**|**NOTWINDOWCOMPAT**<sup>1</sup>|**WINDOWCOMPAT**|
|**非純粋**<sup>1</sup>|**オブジェクト**|**WINDOWS**|
|**含める**<sup>2</sup>|**古い**<sup>1</sup>||

<sup>1</sup>この用語を見つけたときに、リンカーは (「無視」)、警告を生成します。 ただし、単語は予約されたままです。

<sup>2</sup>リンカーは、この単語を無視しますが、警告は出力されません。

## <a name="see-also"></a>関連項目

- [MSVC リンカーのリファレンス](linking.md)
- [MSVC リンカー オプション](linker-options.md)