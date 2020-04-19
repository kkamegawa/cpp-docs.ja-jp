---
title: 文字列変換マクロ
ms.date: 11/04/2016
f1_keywords:
- atlconv/ATL::DEVMODEA2W
- atlconv/ATL::TEXTMETRICA2W
- atlconv/ATL::DEVMODEOLE2T
- atlconv/ATL::TEXTMETRICOLE2T
- atlconv/ATL::DEVMODET2OLE
- atlconv/ATL::TEXTMETRICT2OLE
- atlconv/ATL::DEVMODEW2A
- atlconv/ATL::TEXTMETRICW2A
ms.assetid: 2ff7c0b6-2bde-45fe-897f-6128e18e0c27
ms.openlocfilehash: f7d9548fc5710e8d3d5d668dff230a60e7a291a1
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495189"
---
# <a name="string-conversion-macros"></a>文字列変換マクロ

これらのマクロは、文字列変換機能を提供します。

##  <a name="atl_and_mfc_string_conversion_macros"></a>ATL および MFC 文字列変換マクロ

ここで説明する文字列変換マクロは、ATL と MFC の両方に対して有効です。 MFC 文字列変換の詳細については[、「テクニカルノート 59:Mfc の MBCS/Unicode 変換マクロ](../../mfc/tn059-using-mfc-mbcs-unicode-conversion-macros.md)と[mfc マクロおよび mfc](../../mfc/reference/mfc-macros-and-globals.md)を使用します。

##  <a name="devmode_and_textmetric_string_conversion_macros"></a>DEVMODE および TEXTMETRIC 文字列変換マクロ

これらのマクロは、 [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea)または[textmetric](/windows/win32/api/wingdi/ns-wingdi-textmetricw)構造体のコピーを作成し、新しい構造体内の文字列を新しい文字列型に変換します。 マクロは、新しい構造体のスタックにメモリを割り当て、新しい構造体へのポインターを返します。

```cpp
MACRONAME( address_of_structure )
```

### <a name="remarks"></a>Remarks

例えば:

[!code-cpp[NVC_ATL_Utilities#128](../../atl/codesnippet/cpp/string-conversion-macros_1.cpp)]

および

[!code-cpp[NVC_ATL_Utilities#129](../../atl/codesnippet/cpp/string-conversion-macros_2.cpp)]

マクロ名では、ソース構造内の文字列型が左 (たとえば) であり、変換先構造体の文字列型が右側にあります (たとえば、 **W**)。 **は**LPSTR を表し、 **OLE**は LPOLESTR、 **T**は LPTSTR を表し、 **W**は LPWSTR を表します。

したがって、DEVMODEA2W は`DEVMODE` 、LPSTR 文字列を含む構造`DEVMODE`体を LPWSTR `TEXTMETRIC`文字列を含む構造体にコピーします。 TEXTMETRICOLE2T `TEXTMETRIC`は、LPOLESTR 文字列を含む構造体を、LPTSTR 文字列を含む構造体にコピーします。

`DEVMODE`構造体で変換される2つの文字列は、`dmDeviceName`デバイス名 () とフォーム`dmFormName`名 () です。 文字列`DEVMODE`変換マクロでは、構造体のサイズ`dmSize`() も更新されます。

`TEXTMETRIC`構造体で変換された4つの文字列は`tmFirstChar`、最初の文字 ()`tmLastChar`、最後の文字 ()`tmDefaultChar`、既定の文字 ()、`tmBreakChar`および改行文字 () です。

`DEVMODE` および`TEXTMETRIC`文字列変換マクロの動作は、有効なコンパイラディレクティブ (存在する場合) によって異なります。 ソースの型とターゲットの型が同じである場合、変換は実行されません。 コンパイラディレクティブは、次のように**T**と**OLE**を変更します。

|有効なコンパイラ ディレクティブ|T の変更後|OLE の変更後|
|----------------------------------|---------------|-----------------|
|none|**A**|**W**|
|**\_対応**|**W**|**W**|
|**OLE2ANSI**|**A**|**A**|
|UNICODE と**OLE2ANSI**  **\_**|**W**|**A**|

次の表に、 `DEVMODE`および`TEXTMETRIC`文字列変換マクロの一覧を示します。

|||
|-|-|
|DEVMODEA2W|TEXTMETRICA2W|
|DEVMODEOLE2T|TEXTMETRICOLE2T|
|DEVMODET2OLE|TEXTMETRICT2OLE|
|DEVMODEW2A|TEXTMETRICW2A|

## <a name="see-also"></a>関連項目

[[マクロ]](../../atl/reference/atl-macros.md)
