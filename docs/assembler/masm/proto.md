---
title: PROTO
ms.date: 12/06/2019
f1_keywords:
- PROTO
helpviewer_keywords:
- PROTO directive
ms.assetid: 0487ee16-9dc7-43d1-9445-cd1601f5a080
ms.openlocfilehash: 3963fa29050653d1706222d33734c4b5f2a17919
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75318645"
---
# <a name="proto"></a>PROTO

関数またはプロシージャをプロトタイプします。 [INVOKE](invoke.md)ディレクティブを使用して、PROTO ディレクティブでプロトタイプ宣言された関数を呼び出すことができます。

## <a name="syntax"></a>構文

> *label* **PROTO** ⟦*distance*⟧⟦*language-type*⟧⟦ __,__ ⟦*parameter*⟧ __:__ *tag* ...⟧

### <a name="parameters"></a>パラメーター

*ラベル*の\
プロトタイプ宣言された関数の名前。

*distance* (32 ビット MASM のみ)\
Optional16ビットメモリモデルで、既定値をオーバーライドし、 **NEAR**または**FAR**呼び出しを示すために使用されます。

*言語の種類*(32 ビット MASM のみ)\
Optionalプロシージャとパブリックシンボルの呼び出し規則と名前付け規則を設定します。 サポートされている規則は次のとおりです。

- 32-ビット**フラット**モデル: **C**、 **STDCALL**

- 16ビットモデル: **C**、 **BASIC**、 **FORTRAN**、 **PASCAL**、 **SYSCALL**、 **STDCALL**

*パラメーター*\
関数パラメーターの省略可能な名前です。

*タグ*\
関数パラメーターの型。

*パラメーター*と*タグ*のパラメーターは、渡された引数ごとに1回、複数回出現する場合があります。

## <a name="example"></a>使用例

このサンプルでは、`addup3` という名前の関数の**PROTO**宣言を示します。この関数は、 **NEAR**呼び出しを使用してプロシージャ呼び出しの16ビットモデルの既定値をオーバーライドし、スタックパラメーターと戻り値に**C**呼び出し規約を使用します。 2つの引数 (**単語**と**VARARG**) を受け取ります。

```MASM
addup3 PROTO NEAR C, argcount:WORD, arg1:VARARG
```

## <a name="see-also"></a>関連項目

[ディレクティブリファレンス](directives-reference.md)\
[.モデル参照](dot-model.md)\
[MASM BNF 文法](masm-bnf-grammar.md)
