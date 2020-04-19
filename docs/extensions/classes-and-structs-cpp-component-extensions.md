---
title: ref class と ref struct (C++/CLI および C++/CX)
ms.date: 05/16/2019
ms.topic: reference
f1_keywords:
- ref class
helpviewer_keywords:
- ref class keyword [C++]
- value class keyword [C++]
- value struct keyword [C++]
- ref struct keyword [C++]
ms.assetid: 5c360764-b229-49c6-9357-66213afbc372
ms.openlocfilehash: 9c993b134d6d359d0bc756f5e79d2f9cc137c9cf
ms.sourcegitcommit: bc1b14f29a02685f97c7ef5c098d16db6eaf369f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/16/2019
ms.locfileid: "65788782"
---
# <a name="ref-class-and-ref-struct--ccli-and-ccx"></a>ref class と ref struct (C++/CLI および C++/CX)

**ref class** または **ref struct** 拡張機能は、その*オブジェクトの有効期間*が自動的に管理されるクラスまたは構造体を宣言します。 オブジェクトがアクセスできなくなるかスコープ外になると、そのメモリが解放されます。

## <a name="all-runtimes"></a>すべてのランタイム

### <a name="syntax"></a>構文

```cpp
      class_access
      ref class
      name
      modifier :  inherit_accessbase_type {};
class_accessref structnamemodifier :  inherit_accessbase_type {};
class_accessvalue classnamemodifier :  inherit_accessbase_type {};
class_accessvalue structnamemodifier :  inherit_accessbase_type {};
```

### <a name="parameters"></a>パラメーター

*class_access*<br/>
(省略可能) アセンブリの外部にあるクラスまたは構造体のアクセシビリティ。 使用可能な値は **public** と **private** です (既定値は **private** です)。 入れ子になったクラスまたは構造体には *class_access* 指定子を指定できません。

*name*<br/>
クラスまたは構造体の名前。

*modifier*<br/>
(省略可能) 有効な修飾子は、[abstract](abstract-cpp-component-extensions.md) と [sealed](sealed-cpp-component-extensions.md) です。

*inherit_access*<br/>
(省略可能) *base_interface* のアクセシビリティ。 許可されるアクセシビリティは **public** のみです (既定値は **public** です)。

*base_type*<br/>
(省略可能) 基本型。 ただし、値型を基本型として使用することはできません。

詳細については、Windows ランタイムと共通言語ランタイムに関するセクションで、このパラメーターの言語別の説明を参照してください。

### <a name="remarks"></a>解説

**ref class** または **value class** で宣言されたオブジェクトの既定のメンバーのアクセシビリティは **private** です。 また、**ref struct** または **value struct** で宣言されたオブジェクトの既定のメンバーのアクセシビリティは **public** です。

参照型が別の参照型から継承される場合、基底クラスの仮想関数は ([override](override-cpp-component-extensions.md) を使用して) 明示的にオーバーライドするか、([new (vtable の新しいスロット)](new-new-slot-in-vtable-cpp-component-extensions.md) を使用して) 非表示にする 必要があります。 派生クラスの関数も、明示的に **virtual** とマークする必要があります。

コンパイル時に、型が **ref class**、**ref struct**、**value class**、または **value struct** であるかを検出するには、`__is_ref_class (type)`、`__is_value_class (type)`、または `__is_simple_value_class (type)` を使用します。 詳細については、「[型の特徴のコンパイラ サポート](compiler-support-for-type-traits-cpp-component-extensions.md)」を参照してください。

クラスと構造体の詳細については、以下のページを参照してください。

- [クラスと構造体のインスタンス化](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md)

- [参照型の C++ スタック セマンティクス](../dotnet/cpp-stack-semantics-for-reference-types.md)

- [クラス、構造体、および共用体](../cpp/classes-and-structs-cpp.md)

- [デストラクターとファイナライザー (方法: クラスと構造体の定義と使用 (C++/CLI))](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)

- [ユーザー定義の演算子 (C++/CLI)](../dotnet/user-defined-operators-cpp-cli.md)

- [ユーザー定義変換 (C++/CLI)](../dotnet/user-defined-conversions-cpp-cli.md)

- [方法: ネイティブ クラスを C# で使用できるようにラップする](../dotnet/how-to-wrap-native-class-for-use-by-csharp.md)

- [ジェネリック クラス (C++/CLI)](generic-classes-cpp-cli.md)

## <a name="windows-runtime"></a>Windows ランタイム

### <a name="remarks"></a>解説

[Ref クラスと構造体](../cppcx/ref-classes-and-structs-c-cx.md)と「[値クラスと構造体](https://msdn.microsoft.com/library/windows/apps/hh699861.aspx)」を参照してください。

### <a name="parameters"></a>パラメーター

*base_type*<br/>
(省略可能) 基本型。 **ref class** または **ref struct** は、0 個以上のインターフェイスと 0 個または 1 個の **ref** 型から継承できます。 **value class** または **value struct** は、ゼロ個以上のインターフェイスからのみ継承できます。

**ref class** または **ref struct** キーワードを使用してオブジェクトを宣言する場合、オブジェクトに対するハンドル (オブジェクトへの参照カウンター ポインター) を使用してオブジェクトにアクセスします。 宣言された変数がスコープ外になると、コンパイラは自動的に基になるオブジェクトを削除します。 そのオブジェクトが呼び出しのパラメーターとして使用されているか、変数に格納されている場合は、実際にそのオブジェクトのハンドルが渡されるか格納されます。

**value class** または **value struct** キーワードを使用してオブジェクトを宣言すると、宣言されたオブジェクトのオブジェクト有効期間は監視されません。 このオブジェクトは、C++ の他の標準のクラスや構造体と同様です。

### <a name="requirements"></a>要件

コンパイラ オプション: `/ZW`

## <a name="common-language-runtime"></a>共通言語ランタイム

### <a name="remarks"></a>解説

次の表に、「**すべてのランタイム**」セクションに示されている構文の C++/CLI に固有の違いを示します。

### <a name="parameters"></a>パラメーター

*base_type*<br/>
(省略可能) 基本型。 **ref class** または **ref struct** は、0 個以上のマネージド インターフェイスと 0 個または 1 個の ref 型から継承できます。 **ref class** または **ref struct** は、ゼロ個以上のマネージド インターフェイスからのみ継承できます。

**ref class** キーワードと **ref struct** キーワードを指定すると、コンパイラはクラスまたは構造体をヒープに割り当てます。 そのオブジェクトが呼び出しのパラメーターとして使用されているか、変数に格納されている場合は、実際にそのオブジェクトへの参照が渡されるか格納されます。

**value class** キーワードと **value struct** キーワードを指定すると、コンパイラは、割り当てられたクラスまたは構造体の値を関数に渡すか、メンバーに格納します。

### <a name="requirements"></a>要件

コンパイラ オプション: `/clr`

## <a name="see-also"></a>関連項目

[.NET および UWP でのコンポーネント拡張](component-extensions-for-runtime-platforms.md)