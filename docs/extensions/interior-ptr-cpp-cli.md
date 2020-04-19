---
title: interior_ptr (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- stdcli::language::interior_ptr
- interior_ptr_cpp
- interior_ptr
helpviewer_keywords:
- interior_ptr keyword [C++]
ms.assetid: 25160f74-569e-492d-9e3c-67ece7486baa
ms.openlocfilehash: 0fba04efeaa634f5e21600768297aee0d999d1c6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "65515697"
---
# <a name="interiorptr-ccli"></a>interior_ptr (C++/CLI)

"*内部ポインター*" は、参照型の内部へのポインターを宣言しますが、オブジェクト自体へのポインターは宣言しません。 内部ポインターは、参照ハンドル、値の型、ボックス化された型のハンドル、マネージ型のメンバーまたは、マネージ配列の要素を指すことができます。

## <a name="all-runtimes"></a>すべてのランタイム

(この言語機能にはランタイムに適用される特記事項がありません。)

## <a name="windows-runtime"></a>Windows ランタイム

(この言語機能には Windows ランタイムのみに適用される特記事項がありません。)

### <a name="requirements"></a>要件

コンパイラ オプション: `/ZW`

## <a name="common-language-runtime"></a>共通言語ランタイム

次の構文例では、内部ポインターを示します。

### <a name="syntax"></a>構文

```cpp
cli::interior_ptr<cv_qualifier type> var = &initializer;
```

### <a name="parameters"></a>パラメーター

*cv_qualifier*<br/>
**const** または **volatile** 修飾子。

*type*<br/>
*initializer* の型。

*var*<br/>
**interior_ptr** 変数の名前。

*initializer*<br/>
参照型のメンバー、マネージ配列の要素、またはネイティブ ポインターに割り当てることができるその他のオブジェクト。

### <a name="remarks"></a>解説

ガベージ コレクション コレクターによるオブジェクトのインスタンスの移動によってマネージ ヒープ上の位置が変わるため、ネイティブ ポインターでは項目を追跡することはできません。 ポインターがインスタンスを正しく参照するように、ランタイムで、新しく配置されたオブジェクトにポインターを更新する必要があります。

**interior_ptr** は、ネイティブ ポインターの機能のスーパーセットを表します。  そのため、ネイティブ ポインターに割り当てることができるものは、すべて **interior_ptr** にも割り当てることができます。  内部ポインターは、比較演算やポインター演算など、ネイティブ ポインターと同じ一連の操作を実行できます。

内部ポインターは、スタックでのみ宣言できます。  クラスのメンバーとして、内部ポインターを宣言することはできません。

内部ポインターはスタックにのみ存在するため、内部ポインターのアドレスを取得すると、アンマネージ ポインターが発生します。

**interior_ptr** には**bool** への暗黙的な変換があり、これにより、条件付きステートメントで使用することができます。

ガベージ コレクション ヒープ上に移動できないオブジェクトを指す内部ポインターを宣言する方法については、[pin_ptr](pin-ptr-cpp-cli.md) を参照してください。

**interior_ptr** は cli 名前空間に存在します。  詳細については、「[Platform, default, and cli Namespaces (プラットフォーム、既定、および cli 名前空間)](platform-default-and-cli-namespaces-cpp-component-extensions.md)」を参照してください。

内部ポインターの詳細については、以下を参照してください。

- [方法: 内部ポインターおよびマネージド配列を宣言および使用する (C++/CLI)](how-to-declare-and-use-interior-pointers-and-managed-arrays-cpp-cli.md)

- [方法: interior_ptr キーワードを含む値型を宣言する (C++/CLI)](how-to-declare-value-types-with-the-interior-ptr-keyword-cpp-cli.md)

- [方法: 内部ポインターとネイティブ ポインターを使用して関数をオーバーロードする (C++/CLI)](how-to-overload-functions-with-interior-pointers-and-native-pointers-cpp-cli.md)

- [方法: const キーワードを含む内部ポインターを宣言する (C++/CLI)](how-to-declare-interior-pointers-with-the-const-keyword-cpp-cli.md)

### <a name="requirements"></a>要件

コンパイラ オプション: `/clr`

### <a name="examples"></a>使用例

次の例では、参照型への内部ポインターを宣言して使用する方法を示します。

```cpp
// interior_ptr.cpp
// compile with: /clr
using namespace System;

ref class MyClass {
public:
   int data;
};

int main() {
   MyClass ^ h_MyClass = gcnew MyClass;
   h_MyClass->data = 1;
   Console::WriteLine(h_MyClass->data);

   interior_ptr<int> p = &(h_MyClass->data);
   *p = 2;
   Console::WriteLine(h_MyClass->data);

   // alternatively
   interior_ptr<MyClass ^> p2 = &h_MyClass;
   (*p2)->data = 3;
   Console::WriteLine((*p2)->data);
}
```

```Output
1
2
3
```

## <a name="see-also"></a>関連項目

[.NET および UWP でのコンポーネント拡張](component-extensions-for-runtime-platforms.md)