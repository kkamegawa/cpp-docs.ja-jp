---
title: Platform::Type クラス
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Type::GetTypeCode
- VCCORLIB/Platform::Type::FullName
helpviewer_keywords:
- Platform::Type Class
ms.assetid: d6b03f1e-b240-49b9-a08e-53a460030475
ms.openlocfilehash: 456dbff652c8f1b800308ff757930b425616a83f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62183004"
---
# <a name="platformtype-class"></a>Platform::Type クラス

型に関するランタイム情報 (文字列名と型コード) を含みます。 呼び出すことによって取得[object::gettype](../cppcx/platform-object-class.md#gettype)任意のオブジェクトでまたはを使用して、 [typeid](../extensions/typeid-cpp-component-extensions.md)演算子はクラスまたは構造体の名前にします。

## <a name="syntax"></a>構文

```cpp
public ref class Platform::Type :
    Platform::Object, Platform::Details::IEquatable,
    Platform::Details::IPrintable
```

### <a name="remarks"></a>Remarks

`Type` クラスは、オブジェクトの実行時の型に基づいて分岐する `if` ステートメントまたは `switch` ステートメントを使用して処理を指示する必要があるアプリケーションで役に立ちます。 使用して型のカテゴリを説明する型コードを取得、 [type::gettypecode](#gettypecode)メンバー関数。

## <a name="public-methods"></a>パブリック メソッド

|||
|-|-|
|[Type::GetTypeCode メソッド](#gettypecode)|オブジェクトの [Platform::TypeCode 列挙](../cppcx/platform-typecode-enumeration.md) 値を返します。|
|[Type::ToString メソッド](#tostring)|そのメタデータで指定されている型の名前を返します。|

## <a name="public-properties"></a>パブリック プロパティ

|||
|-|-|
|[Type::FullName](#fullname)|返します、 [platform::string Class](../cppcx/platform-string-class.md)^ 型の完全修飾名を表し、を使用している。 (ドット) を区切り記号としてできません:: (二重のコロン) — たとえば、`MyNamespace.MyClass`します。|

## <a name="conversion-operators"></a>変換演算子

|||
|-|-|
|[Type^ 演算子](../cppcx/operator-type-hat.md)|`Windows::UI::Xaml::Interop::TypeName` から `Platform::Type`への変換を有効にします。|
|[Windows::UI::Xaml::Interop::TypeName 演算子](../cppcx/operator-windows-ui-xaml-interop-typename.md)|`Platform::Type` から `Windows::UI::Xaml::Interop::TypeName`への変換を有効にします。|

### <a name="requirements"></a>必要条件

**最小値には、クライアントがサポートされています。** Windows 8

**最小値には、サーバーがサポートされています。** Windows Server 2012

**名前空間:** プラットフォーム

**メタデータ:** platform.winmd

## <a name="fullname"></a> Type::FullName プロパティ

フォームの現在の型の完全修飾名を取得`Namespace.Type`します。

### <a name="syntax"></a>構文

```cpp
String^ FullName();
```

### <a name="return-value"></a>戻り値

型の名前。
### <a name="example"></a>例

```

//  namespace is TestApp
MainPage::MainPage()
{
    InitializeComponent();
    Type^ t = this->GetType();
    auto s = t->FullName; // returns "TestApp.MainPage"
    auto s2 = t->ToString(); //also returns "TestApp.MainPage"
}
```

## <a name="gettypecode"></a> Type::GetTypeCode メソッド

組み込み型の数値型カテゴリを取得します。

### <a name="syntax"></a>構文

```cpp
Platform::TypeCode GetTypeCode();
```

### <a name="return-value"></a>戻り値

Platform::TypeCode 列挙値のいずれか。

### <a name="remarks"></a>Remarks

`typeid` プロパティが GetTypeCode() メンバー メソッドに相当します。

## <a name="tostring"></a> Type::ToString メソッド

取得する型の名前。

### <a name="syntax"></a>構文

```cpp
Platform::String^ ToString();
```

### <a name="return-value"></a>戻り値

そのメタデータで指定されている型の名前。

## <a name="see-also"></a>関連項目

[プラットフォーム名前空間](../cppcx/platform-namespace-c-cx.md)
