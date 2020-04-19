---
title: リンカ ツール エラー LNK1179
ms.date: 11/04/2016
f1_keywords:
- LNK1179
helpviewer_keywords:
- LNK1179
ms.assetid: 4b1536d7-0d3d-4f29-a9c1-6fa5cf6cb665
ms.openlocfilehash: 71aba1f20cfaf5b6b9ec33d43ebde594e381921f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391414"
---
# <a name="linker-tools-error-lnk1179"></a>リンカ ツール エラー LNK1179

ファイルが無効または壊れています: COMDAT 'filename' が重複しています

オブジェクト モジュールには、同じ名前の 2 つ以上の Comdat が含まれています。

使用してこのエラーは発生する[/H](../../build/reference/h-restrict-length-of-external-names.md)、外部名の長さを制限して[/Gy](../../build/reference/gy-enable-function-level-linking.md)関数を Comdat にパッケージします。

## <a name="example"></a>例

次のコードで`function1`と`function2`最初の 8 文字でも同じです。 使用してコンパイル **/Gy**と **/H8**リンク エラーが生成されます。

```
void function1(void);
void function2(void);

int main() {
    function1();
    function2();
}

void function1(void) {}
void function2(void) {}
```