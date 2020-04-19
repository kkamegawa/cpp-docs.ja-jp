---
title: プラットフォーム、既定、および cli 名前空間 (C++/CLI および C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- lang
- cli
helpviewer_keywords:
- lang namespace
- cli namespace
ms.assetid: 9d38bd1e-dc78-47d1-a84b-9b4683e52c9c
ms.openlocfilehash: a7599e2987d27626e6f5c9d049d9a3bd4509c3ff
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "65516517"
---
# <a name="platform-default-and-cli-namespaces--ccli-and-ccx"></a>プラットフォーム、既定、および cli 名前空間 (C++/CLI および C++/CX)

言語要素の名前は名前空間によって修飾されるため、それ以外は同じである名前と、ソース コードの別の部分で競合することはありません。 たとえば、名前が競合すると、コンパイラで[状況依存キーワード](context-sensitive-keywords-cpp-component-extensions.md)を認識できなくなります。 名前空間はコンパイラによって使用されますが、コンパイルされたアセンブリでは保持されません。

## <a name="all-runtimes"></a>すべてのランタイム

Visual Studio では、プロジェクトの作成時に、既定の名前空間がプロジェクトに与えられます。 名前空間の名前は手動で変更できますが、C++/CX では、.winmd ファイルの名前が、ルート名前空間の名前と一致している必要があります。

## <a name="windows-runtime"></a>Windows ランタイム

詳細については、「[名前空間と型の参照範囲 (C++/CX)](https://msdn.microsoft.com/library/windows/apps/hh969551.aspx)」を参照してください。

### <a name="requirements"></a>要件

コンパイラ オプション: `/ZW`

## <a name="common-language-runtime"></a>共通言語ランタイム

### <a name="syntax"></a>構文

```cpp
using namespace cli;
```

### <a name="remarks"></a>解説

C++CLI では、**cli** 名前空間がサポートされています。 `/clr` を指定してコンパイルする場合、Syntax セクションで **using** ステートメントが使用されているとみなされます。

**cli** 名前空間には、次の言語機能が含まれます。

- [配列](arrays-cpp-component-extensions.md)

- [interior_ptr (C++/CLI)](interior-ptr-cpp-cli.md)

- [pin_ptr (C++/CLI)](pin-ptr-cpp-cli.md)

- [safe_cast](safe-cast-cpp-component-extensions.md)

### <a name="requirements"></a>要件

コンパイラ オプション: `/clr`

### <a name="examples"></a>使用例

次のコード例では、**cli** 名前空間のシンボルを、ユーザー定義シンボルとして自分のコードで使用できることを示します。  ただし、これを行った場合は、同じ名前の **cli** 言語要素への参照を、明示的または暗黙的に修飾する必要があります。

```cpp
// cli_namespace.cpp
// compile with: /clr
using namespace cli;
int main() {
   array<int> ^ MyArray = gcnew array<int>(100);
   int array = 0;

   array<int> ^ MyArray2 = gcnew array<int>(100);   // C2062

   // OK
   cli::array<int> ^ MyArray2 = gcnew cli::array<int>(100);
   ::array<int> ^ MyArray3 = gcnew ::array<int>(100);
}
```

## <a name="see-also"></a>関連項目

[.NET および UWP でのコンポーネント拡張](component-extensions-for-runtime-platforms.md)