---
title: コンパイラ エラー C2482
ms.date: 09/15/2017
f1_keywords:
- C2482
helpviewer_keywords:
- C2482
ms.assetid: 98c87da2-625c-4cc2-9bf7-78d15921e779
ms.openlocfilehash: 481920fa2d8c32bc872e7b8805188cc674e6fe28
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62375055"
---
# <a name="compiler-error-c2482"></a>コンパイラ エラー C2482

>'*識別子*': 'thread' のデータ管理/WinRT コードでは使用できませんの動的な初期化

## <a name="remarks"></a>Remarks

マネージまたは WinRT のコードを使用して宣言された変数、 [_declspec](../../cpp/thread.md)ストレージ クラス修飾子の属性または[thread_local](../../cpp/storage-classes-cpp.md#thread_local)式では、ストレージ クラス指定子を初期化できません実行時に評価が必要です。 静的な式が初期化に必要な`__declspec(thread)`または`thread_local`これらのランタイム環境でのデータ。

## <a name="example"></a>例

次のサンプルの生成 C2482 で管理されている (**/clr**) と WinRT (**/ZW**) コード。

```cpp
// C2482.cpp
// For managed example, compile with: cl /EHsc /c /clr C2482.cpp
// For WinRT example, compile with: cl /EHsc /c /ZW C2482.cpp
#define Thread __declspec( thread )
Thread int tls_i1 = tls_i1;   // C2482

int j = j;   // OK in C++; C error
Thread int tls_i2 = sizeof( tls_i2 );   // Okay in C and C++
```

この問題を解決するには、定数を使用してスレッド ローカル ストレージを初期化します。 **constexpr**、または静的な式。 別に、スレッド固有の初期化を実行します。