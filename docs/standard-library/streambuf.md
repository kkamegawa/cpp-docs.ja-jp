---
title: '&lt;streambuf&gt;'
ms.date: 11/04/2016
f1_keywords:
- <streambuf>
helpviewer_keywords:
- streambuf header
ms.assetid: 4365b25c-5831-488b-b9c2-867bfe961b89
ms.openlocfilehash: ca5f53d67bb32e59c20d1d440879144f0a617c66
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72686020"
---
# <a name="ltstreambufgt"></a>&lt;streambuf&gt;

Iostreams の標準ヘッダー \<streambuf > をインクルードして、iostreams クラスの操作の基本であるクラステンプレート[basic_streambuf](../standard-library/basic-streambuf-class.md)を定義します。 通常、このヘッダーは別の iostream ヘッダーにインクルードされているため、ユーザーが直接インクルードする必要はありません。

## <a name="syntax"></a>構文

```cpp
#include <streambuf>
```

### <a name="typedefs"></a>Typedef

|型名|説明|
|-|-|
|[streambuf](../standard-library/streambuf-typedefs.md#streambuf)|テンプレートパラメーターとして**char**を使用する特殊な `basic_streambuf`。|
|[wstreambuf](../standard-library/streambuf-typedefs.md#wstreambuf)|**Wchar_t**をテンプレートパラメーターとして使用する `basic_streambuf` の特殊化。|

### <a name="classes"></a>クラス

|インスタンス|説明|
|-|-|
|[basic_streambuf クラス](basic-streambuf-class.md)|クラステンプレートは、ストリームの特定の表現との間での要素の伝送を制御する、ストリームバッファーを派生させるための抽象基本クラスを記述します。|

## <a name="see-also"></a>関連項目

[ヘッダー ファイル リファレンス](../standard-library/cpp-standard-library-header-files.md)\
[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream プログラミング](../standard-library/iostream-programming.md)\
[iostreams の規則](../standard-library/iostreams-conventions.md)
