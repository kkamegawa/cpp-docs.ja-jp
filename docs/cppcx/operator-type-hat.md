---
title: Type^ 演算子
ms.date: 12/30/2016
ms.assetid: b24ffc83-0780-4f9a-8ee0-f5725db339d1
ms.openlocfilehash: 180efcac76b7f51291a47ee68508e7444a6c069c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62161811"
---
# <a name="operator-type"></a>Type^ 演算子

[Windows::UI::Xaml::Interop::TypeName](/uwp/api/windows.ui.xaml.interop.typename) から `Platform::Type`への変換を有効にします。

## <a name="syntax"></a>構文

```cpp
Operator Type^(Windows::UI::Xaml::Interop::TypeName typeName);
```

### <a name="return-value"></a>戻り値

`Platform::Type` Windows::UI::Xaml::Interop::TypeName [が指定されると、](/uwp/api/windows.ui.xaml.interop.typename)を返します。

### <a name="remarks"></a>Remarks

`TypeName` は、型情報を表すための、言語に依存しない Windows ランタイムの構造体です。 [Platform::Type](../cppcx/platform-type-class.md) は C++ に固有で、アプリケーション バイナリ インターフェイス (ABI: Application Binary Interface) を通じて渡すことはできません。 `TypeName`Navigate [関数での](/uwp/api/windows.ui.xaml.controls.frame.navigate) の使用例を次に示します。

```
rootFrame->Navigate(TypeName(MainPage::typeid), e->Arguments);
```

### <a name="example"></a>例

次に、 `TypeName` と `Type`の間の変換方法を示します。

```

// Convert from Type to TypeName
TypeName tn = TypeName(MainPage::typeid);

// Convert back from TypeName to Type
Type^ tx2 = (Type^)(tn);
```

## <a name="net-framework-equivalent"></a>同等の .NET Framework 関数

.NET framework プログラム プロジェクト`TypeName`として <xref:System.Type>

### <a name="requirements"></a>必要条件

## <a name="see-also"></a>関連項目

[Windows::UI::Xaml::Interop::TypeName 演算子](../cppcx/operator-windows-ui-xaml-interop-typename.md)<br/>
[Platform::Type クラス](../cppcx/platform-type-class.md)
