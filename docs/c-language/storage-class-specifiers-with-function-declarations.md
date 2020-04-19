---
title: 関数宣言内でのストレージ クラス指定子の使用
ms.date: 11/04/2016
helpviewer_keywords:
- function specifiers, storage class
- declaring functions, specifiers
- external declarations
- specifiers, function
- external linkage, function declarations
- external linkage, storage-class specifiers
ms.assetid: 801d7df2-efa9-4924-a725-274a5654cfd4
ms.openlocfilehash: 69d6fa2b17523f2bb4068cd05a11265d91750021
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152262"
---
# <a name="storage-class-specifiers-with-function-declarations"></a>関数宣言内でのストレージ クラス指定子の使用

関数宣言では、**static** または `extern` のストレージ クラス指定子のいずれかを使用できます。 関数には常にグローバル有効期間があります。

**Microsoft 固有の仕様**

内部レベルでの関数宣言は、外部レベルでの関数宣言と同じ意味になります。 これは、関数がローカル スコープで宣言されていても、その宣言位置から翻訳単位の残り全体で可視になることを意味しています。

**Microsoft 固有の仕様はここまで**

関数の表示規則は、次のように、変数の規則とは若干異なります。

- **static** として宣言された関数は、定義されているソース ファイル内でのみ表示されます。 同じソース ファイル内の関数は **static** 関数を呼び出すことができますが、他のソース ファイルの関数は名前で static 関数に直接アクセスすることはできません。 異なるソース ファイルにある同じ名前の別の **static** 関数は、競合することなく宣言できます。

- `extern` として宣言された関数は、(後で **static** のような関数を再宣言しない場合) プログラムのすべてのソース ファイルで参照されます。 どの関数も `extern` 関数を呼び出すことができます。

- ストレージ クラスの指定子を省略する関数宣言は既定で `extern` です。

**Microsoft 固有の仕様**

Microsoft では、**静的**として `extern` ID を再定義できます。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[C ストレージ クラス](../c-language/c-storage-classes.md)
