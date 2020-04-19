---
title: naked 関数の規則と制限
ms.date: 11/04/2016
helpviewer_keywords:
- naked functions [C++]
ms.assetid: ff203858-2dd3-4a76-8a57-d0d06817adef
ms.openlocfilehash: ec5c7d635dbbb63af7177395c5ad08356e1a26f0
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857308"
---
# <a name="rules-and-limitations-for-naked-functions"></a>naked 関数の規則と制限

**Microsoft 固有の仕様**

次の規則と制約が naked 関数に適用されます。

- **return**ステートメントは許可されていません。

- 構造化例外処理コンストラクトと C++ の例外処理コンストラクトは、スタック フレームを越えてアンワインドする必要があるため許可されていません。

- 同じ理由で、`setjmp` の形式は禁止されています。

- `_alloca` 関数の使用は禁止されています。

- プロローグ シーケンスの前にローカル変数の初期化コードが出現しないように、初期化されたローカル変数は関数のスコープ内では許可されません。 特に、C++ オブジェクトの宣言は関数のスコープでは許可されません。 ただし、入れ子になったスコープ内には初期化されたデータが含まれる場合があります。

- フレーム ポインター最適化 (/Oy コンパイラ オプション) は推奨されていませんが、naked 関数に対しては自動的に抑制されます。

- 関数の構文スコープでは C++ クラス オブジェクトを宣言できません。 ただし、入れ子になったブロックではオブジェクトを宣言できます。

- [/Clr](../build/reference/clr-common-language-runtime-compilation.md)を使用してコンパイルする場合、**生**のキーワードは無視されます。

- [__Fastcall](../cpp/fastcall.md)の生関数の場合、レジスタ引数のいずれかにC++ C/コードで参照があるたびに、プロローグコードはそのレジスタの値をその変数のスタック位置に格納する必要があります。 例:

```cpp
// nkdfastcl.cpp
// compile with: /c
// processor: x86
__declspec(naked) int __fastcall  power(int i, int j) {
   // calculates i^j, assumes that j >= 0

   // prolog
   __asm {
      push ebp
      mov ebp, esp
      sub esp, __LOCAL_SIZE
     // store ECX and EDX into stack locations allocated for i and j
     mov i, ecx
     mov j, edx
   }

   {
      int k = 1;   // return value
      while (j-- > 0)
         k *= i;
      __asm {
         mov eax, k
      };
   }

   // epilog
   __asm {
      mov esp, ebp
      pop ebp
      ret
   }
}
```

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>参照

[naked 関数呼び出し](../cpp/naked-function-calls.md)