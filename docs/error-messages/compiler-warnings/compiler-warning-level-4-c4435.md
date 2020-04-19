---
title: コンパイラの警告 (レベル 4) C4435
ms.date: 11/04/2016
f1_keywords:
- C4435
helpviewer_keywords:
- C4435
ms.assetid: a04524af-2b71-4ff9-9729-d9d1d1904ed7
ms.openlocfilehash: 0ff545d3de3ef173cdbfd99d7714890e8631ce7a
ms.sourcegitcommit: 8762a3f9b5476b4dee03f0ee8064ea606550986e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/04/2019
ms.locfileid: "74810668"
---
# <a name="compiler-warning-level-4-c4435"></a>コンパイラの警告 (レベル 4) C4435

'class1': /vd2 下のオブジェクトのレイアウトは仮想ベース 'class2' により変更されます。

既定では、この警告はオフに設定されています。 詳細については、「 [既定で無効になっているコンパイラ警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 」を参照してください。

/Vd1 の既定のコンパイルオプションでは、派生クラスには、指定された仮想ベースの `vtordisp` フィールドがありません。  /Vd2 または `#pragma vtordisp(2)` が有効になっている場合は、`vtordisp` のフィールドが表示され、オブジェクトのレイアウトが変更されます。  これにより、相互作用モジュールが異なる `vtordisp` 設定でコンパイルされると、バイナリ互換性の問題が発生する可能性があります。

## <a name="example"></a>使用例

次の例では、C4435 が生成されます。

```cpp
// C4435.cpp
// compile with: /c /W4
#pragma warning(default : 4435)
class A
{
public:
    virtual ~A() {}
};

class B : public virtual A  // C4435
{};
```

## <a name="see-also"></a>参照

[vtordisp](../../preprocessor/vtordisp.md)<br/>
[/vd (ディスプレイスメントの無効化)](../../build/reference/vd-disable-construction-displacements.md)