---
title: extern ストレージ クラス指定子
ms.date: 07/10/2018
helpviewer_keywords:
- extern keyword [C]
- storage class specifiers, extern
- extern keyword [C], storage class specifier
- external linkage, storage-class specifiers
- external linkage, extern modifier
ms.assetid: 6e16d927-291f-49e4-986c-9d91a482a441
ms.openlocfilehash: 6bbae7c778f5196ac0dca387265499b27119a367
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2019
ms.locfileid: "56151391"
---
# <a name="extern-storage-class-specifier"></a>extern ストレージ クラス指定子

ストレージ クラス指定子 **extern** を使用して宣言された変数は、別のソース ファイルで定義されている同じ名前の変数への参照となります。 これは、外部レベル変数の定義を可視化するために使用されます。 **extern** として宣言された変数自体に記憶域は割り当てられません。これは単なる名前です。

## <a name="example"></a>例

この例では、内部および外部レベルの宣言を示しています。

```c

// Source1.c

int i = 1;

// Source2. c

#include <stdio.h>

// Refers to the i that is defined in Source1.c:
extern int i;

void func(void);

int main()
{
    // Prints 1:
    printf_s("%d\n", i);
    func();
    return;
}

void func(void)
{
    // Address of global i assigned to pointer variable:
    static int *external_i = &i;

    // This definition of i hides the global i in Source.c:
    int i = 16;

    // Prints 16, 1:
    printf_s("%d\n%d\n", i, *external_i);
}
```

この例では、変数 `i` は Source1.c 内で、初期値 1 として定義されます。 Source2.c 内での **extern** 宣言は、そのファイル内で 'i' を可視化します。

`func` 関数では、**static** ポインター変数 `external_i` を初期化するために、グローバル変数 `i` のアドレスが使用されます。 グローバル変数の有効期間が **static** である、つまりプログラム実行中にアドレスが変わることがないので、これは機能します。 次に、変数 `i` は、`func` のスコープ内で、初期値 16 のローカル変数として定義されます。 この定義は、外部レベルの `i` の値には影響しません。この値は、ローカル変数用にその名前を使用することで隠されています。 ここでグローバルな `i` の値にアクセスするには、`external_i` ポインターを使用するしかありません。

## <a name="see-also"></a>関連項目

[内部レベル宣言のストレージ クラス指定子](../c-language/storage-class-specifiers-for-internal-level-declarations.md)
