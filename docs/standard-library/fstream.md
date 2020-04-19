---
title: '&lt;fstream&gt;'
ms.date: 11/04/2016
f1_keywords:
- <fstream>
helpviewer_keywords:
- fstream header
ms.assetid: 660de351-0489-41df-b239-40e0cdcab46b
ms.openlocfilehash: 1f85367b9ae527c9387d085acc1496bfbbf7cc9e
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688036"
---
# <a name="ltfstreamgt"></a>&lt;fstream&gt;

外部ファイルに格納されているシーケンスの iostream の操作をサポートする複数のクラスを定義します。

## <a name="syntax"></a>構文

```cpp
#include <fstream>
```

### <a name="typedefs"></a>Typedef

|型名|説明|
|-|-|
|[filebuf](../standard-library/fstream-typedefs.md#filebuf)|**Char**テンプレートパラメーターに特化された型 `basic_filebuf`。|
|[fstream](../standard-library/fstream-typedefs.md#fstream)|**Char**テンプレートパラメーターに特化された型 `basic_fstream`。|
|[ifstream](../standard-library/fstream-typedefs.md#ifstream)|**Char**テンプレートパラメーターに特化された型 `basic_ifstream`。|
|[ofstream](../standard-library/fstream-typedefs.md#ofstream)|**Char**テンプレートパラメーターに特化された型 `basic_ofstream`。|
|[wfstream](../standard-library/fstream-typedefs.md#wfstream)|**Wchar_t**テンプレートパラメーターに特殊化された型 `basic_fstream`。|
|[wifstream](../standard-library/fstream-typedefs.md#wifstream)|**Wchar_t**テンプレートパラメーターに特殊化された型 `basic_ifstream`。|
|[wofstream](../standard-library/fstream-typedefs.md#wofstream)|**Wchar_t**テンプレートパラメーターに特殊化された型 `basic_ofstream`。|
|[wfilebuf](../standard-library/fstream-typedefs.md#wfilebuf)|**Wchar_t**テンプレートパラメーターに特殊化された型 `basic_filebuf`。|

### <a name="classes"></a>クラス

|インスタンス|説明|
|-|-|
|[basic_filebuf](../standard-library/basic-filebuf-class.md)|クラステンプレートは、`Elem` 型の要素の転送を制御するストリームバッファーを記述します。これは、文字の特徴がクラス `Tr` によって決定され、外部ファイルに格納されている要素のシーケンスとの間で決まります。|
|[basic_fstream](../standard-library/basic-fstream-class.md)|クラステンプレートは、要素とエンコードされたオブジェクトの挿入と抽出を制御するオブジェクトを記述します。これは、クラス[basic_filebuf](../standard-library/basic-filebuf-class.md) \<**Elem**, **Tr**> のストリームバッファーを使用し、その文字を `Elem` 型の要素と共に使用します。特徴は `Tr` クラスによって決定されます。|
|[basic_ifstream](../standard-library/basic-ifstream-class.md)|クラステンプレートは、要素とエンコードされたオブジェクトの抽出を制御するオブジェクトを記述します。これは、クラス[basic_filebuf](../standard-library/basic-filebuf-class.md) \<**Elem**, **Tr**> のストリームバッファーから、型 `Elem` の要素を使用して、その文字特性がクラス `Tr` によって決定されます。|
|[basic_ofstream](../standard-library/basic-ofstream-class.md)|クラステンプレートは、要素とエンコードされたオブジェクトのストリームバッファーへの挿入を制御するオブジェクトを記述します。このオブジェクトは、文字の特徴が決定される `Elem` 型の要素を使用して、 [basic_filebuf](../standard-library/basic-filebuf-class.md) \<**Elem**, **Tr**> クラスのストリームバッファーに格納します。クラス `Tr`。|

## <a name="see-also"></a>関連項目

[ヘッダー ファイル リファレンス](../standard-library/cpp-standard-library-header-files.md)\
[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream プログラミング](../standard-library/iostream-programming.md)\
[iostreams の規則](../standard-library/iostreams-conventions.md)
