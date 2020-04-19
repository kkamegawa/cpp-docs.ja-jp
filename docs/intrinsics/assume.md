---
title: __assume
ms.date: 09/02/2019
f1_keywords:
- __assume
- _assume
- __assume_cpp
helpviewer_keywords:
- __assume keyword [C++]
ms.assetid: d8565123-b132-44b1-8235-5a8c8bff85a7
ms.openlocfilehash: f3f847b5268605bdc5df90a8bbc6a88c78431864
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216966"
---
# <a name="__assume"></a>__assume

**Microsoft 固有の仕様**

オプティマイザーにヒントを渡します。

## <a name="syntax"></a>構文

```C
__assume(
   expression
)
```

### <a name="parameters"></a>パラメーター

*条件*\
評価が true になると想定される式。

## <a name="remarks"></a>Remarks

オプティマイザーでは、`expression` で表される条件は、このキーワードが指定された時点で true であり、`expression` が変更されるまで (変数への代入などにより) true のままであると想定します。 `__assume` がオプティマイザーに渡すヒントを選択的に使用することで、より優れた最適化を行うことができます。

`__assume` ステートメントが否定 (常に false に評価される式) として記述された場合は、常に `__assume(0)` として処理されます。 コードが期待どおりに動作しない場合は、前述のとおり、定義した `expression` が有効かつ true であることを確認してください。 想定される `__assume(0)` の動作の詳細については、以降の解説を参照してください。

> [!WARNING]
>  プログラムの到達可能なパスには、無効な `__assume` ステートメントを含めないでください。 コンパイラが無効な `__assume` ステートメントに到達することがあると、予測できない、悪影響のある動作がプログラムで発生するおそれがあります。

`__assume` は正規の組み込みではありません。 これは関数として宣言する必要がなく、また `#pragma intrinsic` ディレクティブ内では使用できません。 コードは生成されませんが、オプティマイザーが生成するコードには影響を与えます。

アサート`__assume`が復旧できない場合にのみ、[アサート](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)でを使用します。 コンパイラがエラー処理コードを最適化する場合があるため、後続のエラー回復コードを含むアサートに `__assume` を使用しないでください。

`__assume(0)` このステートメントは特殊なケースです。 到達できないコード パスを示すために `__assume(0)` を使用します。 次の例では、switch ステートメントの default ケースに到達できないことを示すために `__assume(0)` を使用します。 これは、`__assume(0)` の最も一般的な使用方法です。

以前のバージョンとの互換性を維持するために、 [ \(コンパイラオプションである [言語拡張機能を無効にする](../build/reference/za-ze-disable-language-extensions.md)] が指定されていない場合は、__assume のシノニムであると仮定します。

## <a name="requirements"></a>必要条件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`__assume`|x86、ARM、x64、ARM64|

## <a name="example"></a>例

```cpp
// compiler_intrinsics__assume.cpp
#ifdef DEBUG
# define ASSERT(e)    ( ((e) || assert(__FILE__, __LINE__) )
#else
# define ASSERT(e)    ( __assume(e) )
#endif

void func1(int i)
{
}

int main(int p)
{
   switch(p){
      case 1:
         func1(1);
         break;
      case 2:
         func1(-1);
         break;
      default:
         __assume(0);
            // This tells the optimizer that the default
            // cannot be reached. As so, it does not have to generate
            // the extra code to check that 'p' has a value
            // not represented by a case arm. This makes the switch
            // run faster.
   }
}
```

`__assume(0)` を使用すると、default ケースに到達できないことがオプティマイザーに通知されます。 この例では、`p` には 1 または 2 しか入力されないことをプログラマが認識していることを示しています。 別の値が `p` に渡された場合は、プログラムが無効になり予期しない動作が発生します。

`__assume(0)` ステートメントの結果、コンパイラは case ステートメントで代表されない値が `p` に入るかどうかをテストするコードを生成しません。 このため、`__assume(0)` ステートメントは default ケースの本文の最初のステートメントとする必要があります。

コンパイラでは `__assume` を基にしてコードを生成するため、`__assume` ステートメント内の式が実行時に false となる場合、そのコードは正しく動作しない可能性があります。 実行時に式が常に true となることが確認できない場合は、`assert` 関数を使用するとコードを保護することができます。

```C
#define ASSERT(e)    ( ((e) || assert(__FILE__, __LINE__)), __assume(e) )
```

ただし、このように `assert` を使用すると、このドキュメントで既に説明した default ケースの最適化がコンパイラで実行されなくなります。 代わりに、次のような別のマクロを使用することができます。

```C
#ifdef DEBUG
# define NODEFAULT   ASSERT(0)
#else
# define NODEFAULT   __assume(0)
#endif

   default:
      NODEFAULT;
```

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)\
[キーワード](../cpp/keywords-cpp.md)
