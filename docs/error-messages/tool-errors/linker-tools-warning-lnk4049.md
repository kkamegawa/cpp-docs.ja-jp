---
title: リンカー ツールの警告 LNK4049
ms.date: 04/15/2019
f1_keywords:
- LNK4049
helpviewer_keywords:
- LNK4049
ms.assetid: 5fd5fb24-c860-4149-a557-0ac26a65d97c
ms.openlocfilehash: b527d15310dba70c1bae21e601db17db2900e219
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410240"
---
# <a name="linker-tools-warning-lnk4049"></a>リンカー ツールの警告 LNK4049

> シンボル '*シンボル*'で定義されている'*<filename.obj>*' をインポート

[_declspec](../../cpp/dllexport-dllimport.md)が指定されました*シンボル*オブジェクト ファイルでシンボルが定義されている場合でも *<filename.obj>* で同じイメージ。 削除、`__declspec(dllimport)`修飾子をこの警告を解決します。

## <a name="remarks"></a>Remarks

1 つのオブジェクト ファイルにシンボルの定義を使用して参照するときに、この警告がリンカーによって生成された、`__declspec(dllimport)`別の修飾子を宣言します。

警告 LNK4049 は一般的なバージョンの[リンカー ツールの警告 LNK4217](linker-tools-warning-lnk4217.md)します。 関数またはオブジェクト ファイルには、インポートされたシンボルが参照されていることを判断できない場合の警告 LNK4049 リンカーが生成されます。

LNK4049 が LNK4217 の代わりに生成される一般的なケースは次のとおりです。

- 使用する場合、 [/incremental](../../build/reference/incremental-link-incrementally.md)オプション。

- 使用する場合、 [/LTCG](../../build/reference/ltcg-link-time-code-generation.md)オプション。

LNK4049 を解決するには、次の手順のいずれかを試してください。

- 削除、 `__declspec(dllimport)` LNK4049 をトリガーしたシンボルの事前宣言の修飾子。 使用してバイナリ イメージ内のシンボルを検索する、 **DUMPBIN**ユーティリティ。 **DUMPBIN/SYMBOLS**スイッチには、イメージの COFF シンボル テーブルが表示されます。 詳細については、 **DUMPBIN**ユーティリティを参照してください[DUMPBIN リファレンス](../../build/reference/dumpbin-reference.md)します。

- インクリメンタル リンクとプログラム全体の最適化を一時的に無効にします。 再コンパイルすると、アプリケーションは、インポートされたシンボルを参照する関数の名前を含む警告 LNK4217 を生成します。 削除、`__declspec(dllimport)`インポートされたシンボルとインクリメンタル リンクを再度有効にまたは必要に応じてプログラム全体の最適化から修飾子を宣言します。

最終的に生成されたコードが正しく動作しますが、インポートされた関数の呼び出しに生成されたコードは、関数を直接呼び出すよりも非効率です。 使用してコンパイルするときに、この警告は表示されない、 [/clr](../../build/reference/clr-common-language-runtime-compilation.md)オプション。

詳細については、インポートし、データの宣言をエクスポートを参照してください。 [dllexport、dllimport](../../cpp/dllexport-dllimport.md)します。

## <a name="example"></a>例

次の 2 つのモジュールをリンクすると、LNK4049 が生成されます。 最初のモジュールは、1 つのエクスポートされた関数を含むオブジェクト ファイルを生成します。

```cpp
// LNK4049a.cpp
// compile with: /c

__declspec(dllexport) int func()
{
   return 3;
}
```

2 番目のモジュール内でこの関数を呼び出すと、最初のモジュールでエクスポートされた関数を事前宣言を含むオブジェクト ファイルの生成、`main`関数。 このモジュールを最初のモジュールをリンクすると、LNK4049 が生成されます。 削除、`__declspec(dllimport)`警告を解決するのには、宣言から修飾子。

```cpp
// LNK4049b.cpp
// compile with: /link /WX /LTCG LNK4049a.obj
// LNK4049 expected

__declspec(dllimport) int func();
// try the following line instead
// int func();

int main()
{
   return func();
}
```

## <a name="see-also"></a>関連項目

[リンカー ツールの警告 LNK4217](linker-tools-warning-lnk4217.md) \
[リンカー ツールの警告 LNK4286](linker-tools-warning-lnk4286.md) \
[dllexport、dllimport](../../cpp/dllexport-dllimport.md)