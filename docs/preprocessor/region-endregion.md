---
title: region プラグマ、endregion プラグマ
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.endregion
- endregion_CPP
- region_CPP
- vc-pragma.region
helpviewer_keywords:
- pragmas, region
- pragmas, endregion
- endregion pragma
- region pragma
ms.assetid: c697f807-622f-4796-851b-68a42bbecd84
ms.openlocfilehash: 4a01e04582ac81d678aa0702945c62ee974a4428
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222384"
---
# <a name="region-endregion-pragmas"></a>region プラグマ、endregion プラグマ

`#pragma region`Visual Studio Code エディターの[アウトライン機能](/visualstudio/ide/outlining)を使用して展開または折りたたむことができるコードブロックを指定できます。

## <a name="syntax"></a>構文

> **#pragma リージョン** *名前*\
> **#pragma endregion** *コメント*

### <a name="parameters"></a>パラメーター

*関する*\
Optionalコードエディターに表示するコメント。

*指定*\
Optional領域の名前。 この名前はコードエディターに表示されます。

## <a name="remarks"></a>Remarks

`#pragma endregion``#pragma region`ブロックの終了をマークします。

ブロック`#region`は、 `#pragma endregion`ディレクティブで終了する必要があります。

## <a name="example"></a>例

```cpp
// pragma_directives_region.cpp
#pragma region Region_1
void Test() {}
void Test2() {}
void Test3() {}
#pragma endregion Region_1

int main() {}
```

## <a name="see-also"></a>関連項目

[プラグマディレクティブと __ プラグマキーワード](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
