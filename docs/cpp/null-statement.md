---
title: Null ステートメント
ms.date: 11/04/2016
helpviewer_keywords:
- expressions [C++], null
- null statement
- null values, expressions
ms.assetid: 606f5953-55f0-40c8-ae03-3ee3a819b851
ms.openlocfilehash: 2797937b184bebe0e29f8e5eae428f601c824811
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62245181"
---
# <a name="null-statement"></a>Null ステートメント

「Null ステートメント」は、式ステートメントを*式*がありません。 言語の構文でステートメントが必要でも、式の評価が不要な場合に便利です。 1 つのセミコロンで構成されます。

null ステートメントは、イテレーション ステートメントのプレースホルダーや、複合ステートメントまたは関数の最後でラベルを付けるステートメントとしてよく使用されます。

次のコードは、ある文字列を別の文字列にコピーする方法を示しており、null ステートメントが組み込まれています。

```cpp
// null_statement.cpp
char *myStrCpy( char *Dest, const char *Source )
{
    char *DestStart = Dest;

    // Assign value pointed to by Source to
    // Dest until the end-of-string 0 is
    // encountered.
    while( *Dest++ = *Source++ )
        ;   // Null statement.

    return DestStart;
}

int main()
{
}
```

## <a name="see-also"></a>関連項目

[式ステートメント](../cpp/expression-statement.md)