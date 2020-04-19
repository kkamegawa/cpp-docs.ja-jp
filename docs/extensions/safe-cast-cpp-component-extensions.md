---
title: safe_cast (C++/CLI および C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- safe_cast
- safe_cast_cpp
- stdcli::language::safe_cast
helpviewer_keywords:
- safe_cast keyword [C++]
ms.assetid: 4fa688bf-a8ec-49bc-a4c5-f48134efa4f7
ms.openlocfilehash: 199fda710a077998c6b10f101f6ebc15573e675e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "65516637"
---
# <a name="safecast-ccli-and-ccx"></a>safe_cast (C++/CLI および C++/CX)

**safe_cast** 操作は、指定された式を指定した型で返します (成功した場合)。失敗した場合は、`InvalidCastException` をスローします。

## <a name="all-runtimes"></a>すべてのランタイム

(この言語機能にはランタイムに適用される特記事項がありません。)

### <a name="syntax"></a>構文

```cpp
[default]:: safe_cast< type-id >( expression )
```

## <a name="windows-runtime"></a>Windows ランタイム

**safe_cast** を使用して、指定された式の型を変更できます。 変数またはパラメーターを特定の型に問題なく変換できることがわかっている場合、**try-catch** ブロックを使用せずに **safe_cast** を使用して、開発中のプログラミング エラーを検出することができます。 詳細については、「[キャスト (C++/CX)](https://msdn.microsoft.com/library/windows/apps/hh755802.aspx)」を参照してください。

### <a name="syntax"></a>構文

```cpp
[default]:: safe_cast< type-id >( expression )
```

### <a name="parameters"></a>パラメーター

*type-id*<br/>
変換後の *expression* の型。 参照型または値型へのハンドル、値型、参照型または値型への追跡参照。

*expression*<br/>
参照型または値型へのハンドル、値型、参照型または値型への追跡参照として評価される式。

### <a name="remarks"></a>解説

**safe_cast** は、*expression* を *type-id* で指定された型に変換できない場合は、`InvalidCastException` をスローします。`InvalidCastException` をキャッチするには、[/EH (例外処理モデル)](../build/reference/eh-exception-handling-model.md) コンパイラ オプションを指定し、**try/catch** ステートメントを使用します。

### <a name="requirements"></a>要件

コンパイラ オプション: `/ZW`

### <a name="examples"></a>使用例

次のコード例では、Windows ランタイムで **safe_cast** を使用する方法を示します。

```cpp
// safe_cast_ZW.cpp
// compile with: /ZW /EHsc

using namespace default;
using namespace Platform;

interface class I1 {};
interface class I2 {};
interface class I3 {};

ref class X : public I1, public I2 {};

int main(Array<String^>^ args) {
   I1^ i1 = ref new X;
   I2^ i2 = safe_cast<I2^>(i1);   // OK, I1 and I2 have common type: X
   // I2^ i3 = static_cast<I2^>(i1);   C2440 use safe_cast instead
   try {
      I3^ i4 = safe_cast<I3^>(i1);   // Fails because i1 is not derived from I3.
   }
   catch(InvalidCastException^ ic) {
   wprintf(L"Caught expected exception: %s\n", ic->Message);
   }
}
```

```Output
Caught expected exception: InvalidCastException
```

## <a name="common-language-runtime"></a>共通言語ランタイム

**safe_cast** を使用して、式の型を変更し、検証可能な MSIL コードを生成できます。

### <a name="syntax"></a>構文

```cpp
[cli]:: safe_cast< type-id >( expression )
```

### <a name="parameters"></a>パラメーター

*type-id*<br/>
参照型または値型へのハンドル、値型、参照型または値型への追跡参照。

*expression*<br/>
参照型または値型へのハンドル、値型、参照型または値型への追跡参照として評価される式。

### <a name="remarks"></a>解説

式 `safe_cast<`*type-id*`>(`*expression*`)` は、オペランド *expression* を *type-id* 型のオブジェクトに変換します。

コンパイラでは、[safe_cast](../cpp/static-cast-operator.md) を使用できるほとんどの場所で、**safe_cast** を使用できます。  ただし、**safe_cast** では確実に検証可能な MSIL が生成されますが、**static_cast** では検証不可能な MSIL が生成される場合があります。  検証可能なコードの詳細については、「[純粋なコードと検証可能なコード (C++/CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md)」と「[Peverify.exe (PEVerify ツール)](/dotnet/framework/tools/peverify-exe-peverify-tool)」を参照してください。

**static_cast** 同様、**safe_cast** はユーザー定義の変換を呼び出します。

キャストの詳細については、「[キャスト演算子](../cpp/casting-operators.md)」を参照してください。

**safe_cast** は **const_cast** (**const** のキャスト) を適用しません。

**safe_cast** は cli 名前空間に存在します。  詳細については、「[プラットフォーム、既定、および cli 名前空間](platform-default-and-cli-namespaces-cpp-component-extensions.md)」を参照してください。

**safe_cast** の詳細については、以下を参照してください。

- [C スタイル キャストと /clr (C++/CLI)](c-style-casts-with-clr-cpp-cli.md)

- [方法: C++/CLI で safe_cast を使用する](../dotnet/how-to-use-safe-cast-in-cpp-cli.md)

### <a name="requirements"></a>要件

コンパイラ オプション: `/clr`

### <a name="examples"></a>使用例

コンパイラで **static_cast** を使用できないが **safe_cast** を使用できる状況の例の 1 つは、関連していないインターフェイス型の間でのキャストです。  **safe_cast** を使用した場合、コンパイラは変換エラーを生成せず、キャストが可能であるかどうかを実行時に検証します。

```cpp
// safe_cast.cpp
// compile with: /clr
using namespace System;

interface class I1 {};
interface class I2 {};
interface class I3 {};

ref class X : public I1, public I2 {};

int main() {
   I1^ i1 = gcnew X;
   I2^ i2 = safe_cast<I2^>(i1);   // OK, I1 and I2 have common type: X
   // I2^ i3 = static_cast<I2^>(i1);   C2440 use safe_cast instead
   try {
      I3^ i4 = safe_cast<I3^>(i1);   // fail at runtime, no common type
   }
   catch(InvalidCastException^) {
      Console::WriteLine("Caught expected exception");
   }
}
```

```Output
Caught expected exception
```

## <a name="see-also"></a>関連項目

[.NET および UWP でのコンポーネント拡張](component-extensions-for-runtime-platforms.md)
