---
title: LIB の出力ファイル
ms.date: 11/04/2016
f1_keywords:
- Lib
helpviewer_keywords:
- output files, LIB
ms.assetid: e73d2f9b-a42d-402b-b7e3-3a94bebb317e
ms.openlocfilehash: d7a6352665f12307bfa54025a32f9f7b84311dac
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62269701"
---
# <a name="lib-output-files"></a>LIB の出力ファイル

LIB によって生成された出力ファイルは、次の表に示すように、モードによって異なります。

|モード|出力|
|----------|------------|
|既定値 (構築またはライブラリの変更)|COFF ライブラリ (.lib)|
|/EXTRACT でメンバーの抽出|オブジェクト (.obj) ファイル|
|ファイルし、/DEF ライブラリをインポート、エクスポートの構築|ライブラリ (.lib) とエクスポート (.exp) ファイルをインポートします。|

## <a name="see-also"></a>関連項目

[LIB の概要](overview-of-lib.md)
