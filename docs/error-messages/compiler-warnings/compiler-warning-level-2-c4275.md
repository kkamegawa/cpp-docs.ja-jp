---
title: コンパイラの警告 (レベル 2) C4275
ms.date: 02/08/2019
f1_keywords:
- C4275
helpviewer_keywords:
- C4275
ms.assetid: 18de967a-0a44-4dbc-a2e8-fc4c067ba909
ms.openlocfilehash: 6e0e80d465d77bd4fe99fbcaa98e289b8a4c8b63
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62349686"
---
# <a name="compiler-warning-level-2-c4275"></a>コンパイラの警告 (レベル 2) C4275

> 非 DLL インターフェイス クラスの*class_1*'DLL インターフェイス クラスのベースとして使用される'*class_2*'

エクスポートするクラスがエクスポートされなかったクラスから派生します。

持つクラスをエクスポートするときに、データ破損の可能性を最小限に抑える[方式](../../cpp/dllexport-dllimport.md)、ことを確認します。

- すべての静的データは、DLL からエクスポートされた関数を使用してアクセスします。

- クラスのインライン メソッドは静的データを変更できません。

- CRT 関数または静的データを使用するその他のライブラリ関数を使用して、クラスのメソッドがインライン化、ありません。

- クラスのインライン関数を使用していない CRT 関数、またはその他のライブラリ関数では、静的データをアクセスします。

- クラスのメソッドがありません (に関係なくインライン展開) EXE および DLL でインスタンス化の静的データの相違点のある型を使用できます。

クラスのインスタンスを作成する仮想関数を持つクラスを定義し、機能する DLL を呼び出すことができますを定義して、型のオブジェクトを削除してエクスポートを回避できます。  仮想関数を型でだけ呼び出すことができます、します。

デバッグのリリースをコンパイルする C++ 標準ライブラリ内の型から派生する場合は、Visual C で C4275 を無視できます (**/MTd**) と、コンパイラのエラー メッセージが指す`_Container_base`します。

```cpp
// C4275.cpp
// compile with: /EHsc /MTd /W2 /c
#include <vector>
using namespace std;
class Node;
class __declspec(dllimport) VecWrapper : vector<Node *> {};   // C4275
```