---
title: _ITERATOR_DEBUG_LEVEL
ms.date: 11/04/2016
f1_keywords:
- _ITERATOR_DEBUG_LEVEL
helpviewer_keywords:
- _ITERATOR_DEBUG_LEVEL
ms.assetid: 718549cd-a9a9-4ab3-867b-aac00b321e67
ms.openlocfilehash: 7b573127518969accdfdcc4a25a50269dd6aa002
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456402"
---
# <a name="iteratordebuglevel"></a>_ITERATOR_DEBUG_LEVEL

チェックを行う[反復子](../standard-library/checked-iterators.md)と[デバッグ反復子のサポート](../standard-library/debug-iterator-support.md)を有効にするかどうかを制御する (_s)。 このマクロは、以前の _SECURE_SCL マクロとデバッグマクロの機能を置き換え、その機能を組み合わせたものです。

## <a name="macro-values"></a>マクロの値

次の表に、使用可能な値をまとめます。

|コンパイル モード|マクロの値|説明|
|----------------------|----------------|-----------------|
|**Debug**|||
||0|チェックを行う反復子を無効にし、反復子のデバッグを無効にします。|
||1|チェックを行う反復子を有効にし、反復子のデバッグを無効にします。|
||2 (既定値)|反復子のデバッグを有効にします。チェックを行う反復子は関連しません。|
|**Release**|||
||0 (既定値)|チェックを行う反復子を無効にします。|
||1|チェックを行う反復子を有効にします。反復子のデバッグは関連しません。|

リリースモードでは、[レベル] を2に指定すると、コンパイラによってエラーが生成されます。

## <a name="remarks"></a>Remarks

チェックを行う[反復子](../standard-library/checked-iterators.md)を有効にするかどうかを制御するマクロ (_s) を制御します。デバッグモードでは、[デバッグ反復子のサポート](../standard-library/debug-iterator-support.md)が有効かどうかを制御します。 レベルが1または2と定義されている場合、チェックを行う反復子は、コンテナーの境界が上書きされないようにします。 デバッグレベルが0の場合、反復子はチェックされません。 デバッグレベルが1と定義されている場合、安全ではない反復子の使用によってランタイムエラーが発生し、プログラムが終了します。 レベルを2として定義した場合、アンセーフ反復子の使用により、アサートと、デバッガーを中断するランタイムエラーダイアログが生成されます。

_SECURE_SCL マクロは、デバッグマクロと同様の機能をサポートしているため、特定の状況で使用するマクロとマクロの値がわからない場合があります。 混乱を防ぐために、このマクロを使用することをお勧めします。 次の表では、_SECURE_SCL のさまざまな値に使用する同等のレベルのマクロ値と、既存のコードでのデバッグを行います (_d)。

|**_ITERATOR_DEBUG_LEVEL** |**_SECURE_SCL** |**_HAS_ITERATOR_DEBUGGING**|
|---|---|---|
|0 (リリースの既定値)|0 (無効)|0 (無効)|
|1|1 (有効)|0 (無効)|
|2 (デバッグの既定値)|(関連性なし)|1 (デバッグ モードで有効)|

チェックを行う反復子に関する警告を無効にする方法の詳細については、「[_SCL_SECURE_NO_WARNINGS](../standard-library/scl-secure-no-warnings.md)」を参照してください。

### <a name="example"></a>例

このマクロの値を指定するには、 [/d](../build/reference/d-preprocessor-definitions.md)コンパイラオプションを使用してコマンドラインで定義します。または、 `#define` C++標準ライブラリヘッダーがソースファイルに含まれる前にを使用します。 たとえば、コマンドラインで、デバッグモードで*サンプル .cpp*をコンパイルし、デバッグ反復子のサポートを使用するには、次のように指定します。

`cl /EHsc /Zi /MDd /D_ITERATOR_DEBUG_LEVEL=1 sample.cpp`

ソース ファイルで、反復子を定義する標準ライブラリ ヘッダーの前にマクロを指定します。

```cpp
// sample.cpp

#define _ITERATOR_DEBUG_LEVEL 1

#include <vector>

// ...
```

## <a name="see-also"></a>関連項目

[チェックを行う反復子](../standard-library/checked-iterators.md)\
[反復子のデバッグのサポート](../standard-library/debug-iterator-support.md)\
[安全なライブラリ: C++ 標準ライブラリ](../standard-library/safe-libraries-cpp-standard-library.md)
