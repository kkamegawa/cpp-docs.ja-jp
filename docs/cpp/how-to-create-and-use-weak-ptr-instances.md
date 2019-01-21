---
title: '方法: 作成して、weak_ptr インスタンスを使用'
ms.custom: how-to
ms.date: 07/12/2018
ms.topic: conceptual
ms.assetid: 8dd6909b-b070-4afa-9696-f2fc94579c65
ms.openlocfilehash: 1a0e2880e97a77a0c9975553631a6024072745f0
ms.sourcegitcommit: a1fad0a266b20b313364a74b16c9ac45d089b1e9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/11/2019
ms.locfileid: "54220323"
---
# <a name="how-to-create-and-use-weakptr-instances"></a>方法: 作成して、weak_ptr インスタンスを使用

オブジェクトには、参照カウントをインクリメントせずに `shared_ptr` の基になるオブジェクトにアクセスする方法を格納する必要が生じることがあります。 通常、この状況は `shared_ptr` インスタンス間に循環参照がある場合に発生します。

最適なデザインとして、可能な場合は必ずポインターの共有所有権を避けてください。 ただし、`shared_ptr` インスタンスの共有所有権が必要な場合、それらのインスタンス間の循環参照が発生しないようにします。 循環参照を回避できない場合や、何らかの場合で循環参照が必要とされる場合でも、`weak_ptr` を使用して 1 人以上の所有者に別の `shared_ptr` への弱い参照を与えてください。 `weak_ptr` を使用すると、関連するインスタンスの既存のセットに結合される `shared_ptr` を作成できますが、基になるメモリ リソースがまだ有効な場合のみです。 `weak_ptr` 自体は、参照カウントに参加しないため、参照カウントが 0 になるのを防止することはできません。 ただし、`weak_ptr` を使用して、初期化に使用された `shared_ptr` の新しいコピーの取得を試みることはできます。 メモリが既に削除された場合、`bad_weak_ptr`例外がスローされます。 メモリがまだ有効である場合は、新しい共有ポインターが参照カウントをインクリメントし、`shared_ptr` の変数がスコープ内に入っている限りメモリが有効であることを保証します。

## <a name="example"></a>例

次のコード例は、`weak_ptr` を使用して循環依存関係を持つオブジェクトの削除を確証するケースを示しています。 例を調べる際は、代替ソリューションについて検討した後のみ作成されたと見なしてください。 `Controller` オブジェクトは、コンピューター プロセスのいくつかの側面を表しており、独立して動作します。 各コントローラーは、他のコントローラーのステータスのクエリをいつでも実行できる必要があるため、この目的でそれぞれのコントローラーにプライベート `vector<weak_ptr<Controller>>` が含まれています。 各ベクターには循環参照が含まれているため、`weak_ptr` の代わりに `shared_ptr` インスタンスが使用されます。

[!code-cpp[stl_smart_pointers#222](../cpp/codesnippet/CPP/how-to-create-and-use-weak-ptr-instances_1.cpp)]

```Output
Creating Controller0
Creating Controller1
Creating Controller2
Creating Controller3
Creating Controller4
push_back to v[0]: 1
push_back to v[0]: 2
push_back to v[0]: 3
push_back to v[0]: 4
push_back to v[1]: 0
push_back to v[1]: 2
push_back to v[1]: 3
push_back to v[1]: 4
push_back to v[2]: 0
push_back to v[2]: 1
push_back to v[2]: 3
push_back to v[2]: 4
push_back to v[3]: 0
push_back to v[3]: 1
push_back to v[3]: 2
push_back to v[3]: 4
push_back to v[4]: 0
push_back to v[4]: 1
push_back to v[4]: 2
push_back to v[4]: 3
use_count = 1
Status of 1 = On
Status of 2 = On
Status of 3 = On
Status of 4 = On
use_count = 1
Status of 0 = On
Status of 2 = On
Status of 3 = On
Status of 4 = On
use_count = 1
Status of 0 = On
Status of 1 = On
Status of 3 = On
Status of 4 = On
use_count = 1
Status of 0 = O
nStatus of 1 = On
Status of 2 = On
Status of 4 = On
use_count = 1
Status of 0 = On
Status of 1 = On
Status of 2 = On
Status of 3 = On
Destroying Controller0
Destroying Controller1
Destroying Controller2
Destroying Controller3
Destroying Controller4
Press any key
```

テストとして、ベクター `others` を `vector<shared_ptr<Controller>>` に変更した後、出力で、`TestRun` が返されたときにデストラクターが呼び出されないことを確認してください。

## <a name="see-also"></a>関連項目

[スマート ポインター (Modern C++)](../cpp/smart-pointers-modern-cpp.md)
