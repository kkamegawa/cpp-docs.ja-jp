---
title: spectre
ms.date: 01/23/2018
f1_keywords:
- spectre_cpp
- spectre
- nomitigation
helpviewer_keywords:
- __declspec keyword (C++), spectre
- spectre __declspec keyword
ms.openlocfilehash: 40eee25dec867ae3fce7a6b2d4715f0be81bfe76
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926369"
---
# <a name="spectre"></a>spectre

**Microsoft 固有の仕様**

関数の Spectre variant 1 予測実行バリア命令を挿入しないようコンパイラに指示します。

## <a name="syntax"></a>構文

> **__declspec( spectre(nomitigation) )**

## <a name="remarks"></a>Remarks

[/Qspectre](../build/reference/qspectre.md)コンパイラオプションを指定すると、コンパイラは予測実行バリア命令を挿入します。 これらは挿入されます。分析では、Spectre variant 1 セキュリティ脆弱性が存在することを示します。 出力される具体的な手順は、プロセッサによって異なります。 これらの手順は、コードのサイズやパフォーマンスに最小限の影響を与える必要がありますが、コードが脆弱性の影響を受けない場合や、最大限のパフォーマンスが必要な場合もあります。

専門家による分析では、Spectre variant 1 の境界確認のバイパスの欠陥から、関数が安全であると判断する場合があります。 その場合は、関数宣言にを適用`__declspec(spectre(nomitigation))`することによって、関数内で軽減コードを生成しないようにすることができます。

> [!CAUTION]
> **/Qspectre**予測実行バリアの指示は、重要なセキュリティ保護を提供し、パフォーマンスにわずかに影響を与えます。 したがって、関数のパフォーマンスが重視され、関数が安全であることが判明しているまれなケースを除き、チェックを抑制しないことをお勧めします。

## <a name="example"></a>例

`__declspec(spectre(nomitigation))`の使用例を次のコードに示します。

```cpp
// compile with: /c /Qspectre
static __declspec(spectre(nomitigation))
int noSpectreIssues() {
    // No Spectre variant 1 vulnerability here
    // ...
    return 0;
}

int main() {
    noSpectreIssues();
    return 0;
}
```

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[__declspec](../cpp/declspec.md)<br/>
[キーワード](../cpp/keywords-cpp.md)<br/>
[/Qspectre](../build/reference/qspectre.md)
