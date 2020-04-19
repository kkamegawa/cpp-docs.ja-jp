---
title: コンパイラの警告 (レベル 1) C4251
ms.date: 11/04/2016
f1_keywords:
- C4251
helpviewer_keywords:
- C4251
ms.assetid: a9992038-f0c2-4fc4-a9be-4509442cbc1e
ms.openlocfilehash: d2fff1d2f30c4ac80af6d5b9ca452fa5f30f5a15
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62207358"
---
# <a name="compiler-warning-level-1-c4251"></a>コンパイラの警告 (レベル 1) C4251

'identifier': クラス 'type' を 'type2' のクラスのクライアントで使用される dll のインターフェイスを持っている必要があります

持つクラスをエクスポートするときに、データ破損の可能性を最小限に抑える[方式](../../cpp/dllexport-dllimport.md)、いることを確認します。

- すべての静的データは、DLL からエクスポートされた関数を使用してアクセスします。

- クラスのインライン メソッドは静的データを変更できません。

- クラスのメソッドがインライン展開が CRT 関数を使用しないまたはその他のライブラリ関数を使用して、静的データ (を参照してください[潜在的なエラーを渡す境界を越えて CRT オブジェクト DLL](../../c-runtime-library/potential-errors-passing-crt-objects-across-dll-boundaries.md)詳細については)。

- クラスのメソッドがありません (に関係なくインライン展開) EXE および DLL でインスタンス化の静的データの相違点のある型を使用できます。

クラスのインスタンスを作成する仮想関数を持つクラスを定義し、機能する DLL を呼び出すことができますを定義して、型のオブジェクトを削除してエクスポートを回避できます。  仮想関数を型でだけ呼び出すことができます、します。

内の型から派生した場合に無視できる C4251、C++標準ライブラリは、コンパイル、デバッグ リリース (**/MTd**)、コンパイラのエラー メッセージは _Container_base を指します。

```cpp
// C4251.cpp
// compile with: /EHsc /MTd /W2 /c
#include <vector>
using namespace std;
class Node;
class __declspec(dllimport) VecWrapper : vector<Node *> {};   // C4251
```