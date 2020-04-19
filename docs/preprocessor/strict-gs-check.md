---
title: strict_gs_check プラグマ
ms.date: 08/29/2019
f1_keywords:
- strict_gs_check
- strict_gs_check_CPP
helpviewer_keywords:
- strict_gs_check pragma
ms.assetid: decfec81-c916-42e0-a07f-8cc26df6a7ce
ms.openlocfilehash: 0b66e87f2280c923d05103fccfcbbc8d32daf3fd
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216587"
---
# <a name="strict_gs_check-pragma"></a>strict_gs_check プラグマ

このプラグマは、強化されたセキュリティ チェックを提供します。

## <a name="syntax"></a>構文

> **#pragma strict_gs_check (** **[プッシュ,]** { **on** | **off** } **)** \
> **#pragma strict_gs_check (pop)**

## <a name="remarks"></a>Remarks

コンパイラが関数スタックにランダム クッキーを挿入し、スタック ベースのバッファー オーバーランのカテゴリの検出に役立つように指示します。 既定では`/GS` 、(バッファーセキュリティチェック) コンパイラオプションでは、すべての関数の cookie は挿入されません。 詳細については、「[/GS (バッファーのセキュリティ チェック)](../build/reference/gs-buffer-security-check.md)」を参照してください。

を使用`/GS`してコンパイルし、 **strict_gs_check**を有効にします。

このプラグマは、有害なデータに対して公開される可能性があるコード モジュールで使用してください。 **strict_gs_check**はアグレッシブなプラグマであり、この防御を必要としない可能性がある関数に適用されますが、結果のアプリケーションのパフォーマンスへの影響を最小限に抑えるように最適化されています。

このプラグマを使用した場合でも、安全なコードを記述する必要があります。 つまり、コードにバッファーオーバーランがないことを確認してください。 **strict_gs_check**は、コード内に残っているバッファーオーバーランからアプリケーションを保護する可能性があります。

## <a name="example"></a>例

このサンプルでは、配列をローカル配列にコピーするときに、バッファーオーバーランが発生します。 このコードをで`/GS`コンパイルする場合、配列のデータ型はポインターであるため、スタックにクッキーは挿入されません。 **Strict_gs_check**プラグマを追加すると、スタッククッキーが関数スタックに強制されます。

```cpp
// pragma_strict_gs_check.cpp
// compile with: /c

#pragma strict_gs_check(on)

void ** ReverseArray(void **pData,
                     size_t cData)
{
    // *** This buffer is subject to being overrun!! ***
    void *pReversed[20];

    // Reverse the array into a temporary buffer
    for (size_t j = 0, i = cData; i ; --i, ++j)
        // *** Possible buffer overrun!! ***
            pReversed[j] = pData[i];

    // Copy temporary buffer back into input/output buffer
    for (size_t i = 0; i < cData ; ++i)
        pData[i] = pReversed[i];

    return pData;
}
```

## <a name="see-also"></a>関連項目

[プラグマディレクティブと __ プラグマキーワード](../preprocessor/pragma-directives-and-the-pragma-keyword.md)\
[/GS (バッファーセキュリティチェック)](../build/reference/gs-buffer-security-check.md)
