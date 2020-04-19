---
title: LIB の入力ファイル
ms.date: 11/04/2016
f1_keywords:
- Lib
helpviewer_keywords:
- input files, LIB
ms.assetid: e1236f0d-cd90-446b-b900-f311f456085c
ms.openlocfilehash: 648871464dbc99972b8ca40579046347727e81cf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62269389"
---
# <a name="lib-input-files"></a>LIB の入力ファイル

LIB で想定されている入力ファイルは、次の表に示すように、モードによって異なります。

|モード|入力|
|----------|-----------|
|既定値 (構築またはライブラリの変更)|COFF オブジェクト (.obj) ファイル、32 ビット omf オブジェクト モデルの形式 (です) のオブジェクト (.obj) ファイルである COFF ライブラリ (.lib)|
|/EXTRACT でメンバーの抽出|COFF ライブラリ (.lib)|
|ファイルし、/DEF ライブラリをインポート、エクスポートの構築|モジュール定義 (.def) ファイル、COFF オブジェクト (.obj) ファイル、COFF ライブラリ (.lib)、32 ビット OMF オブジェクト (.obj) ファイル|

> [!NOTE]
>  16 ビット版の LIB によって作成された OMF ライブラリは、LIB の 32 ビット バージョンへの入力として使用できません。

## <a name="see-also"></a>関連項目

[LIB の概要](overview-of-lib.md)
