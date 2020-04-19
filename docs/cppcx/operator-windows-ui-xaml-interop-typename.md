---
title: Windows::UI::Xaml::Interop::TypeName 演算子
ms.date: 12/30/2016
ms.assetid: a65a105e-7e3a-452f-932f-2cdaf00fbba5
ms.openlocfilehash: 5acf17b7c87a71259dba6579d8ee69e0eea86fa5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62161590"
---
# <a name="operator-windowsuixamlinteroptypename"></a>Windows::UI::Xaml::Interop::TypeName 演算子

`Platform::Type` から [Windows::UI::Xaml::Interop::TypeName](/uwp/api/windows.ui.xaml.interop.typename)変換できるようになります。

## <a name="syntax"></a>構文

```cpp
Operator TypeName(Platform::Type^ type);
```

### <a name="return-value"></a>戻り値

[が指定されていると、](/uwp/api/windows.ui.xaml.interop.typename) Windows::UI::Xaml::Interop::TypeName `Platform::Type^`が返されます。

### <a name="remarks"></a>Remarks

`TypeName` は、型情報を表すための、言語に依存しない Windows ランタイムの構造体です。 [Platform::Type](../cppcx/platform-type-class.md) は C++ に固有で、アプリケーション バイナリ インターフェイス (ABI: Application Binary Interface) を通じて渡すことはできません。 `TypeName`Navigate [関数での](/uwp/api/windows.ui.xaml.controls.frame.navigate) の使用例を次に示します。

```
rootFrame->Navigate(TypeName(MainPage::typeid), e->Arguments);
```

### <a name="example"></a>例

次に、 `TypeName` と `Type`の間の変換方法を示します。

```

// Convert from Type to TypeName
Windows::UI::Xaml::Interop::TypeName tn = TypeName(MainPage::typeid);

// Convert back from TypeName to Type
Type^ tx2 = (Type^)(tn);
```

## <a name="net-framework-equivalent"></a>同等の .NET Framework 関数

.NET framework プログラム プロジェクト`TypeName`として[System.Type](assetId:///System.Type?qualifyHint=False&autoUpgrade=True)します。

### <a name="requirements"></a>必要条件

## <a name="see-also"></a>関連項目

[Windows::UI::Xaml::Interop::TypeName 演算子](../cppcx/operator-windows-ui-xaml-interop-typename.md)<br/>
[Platform::Type クラス](../cppcx/platform-type-class.md)
