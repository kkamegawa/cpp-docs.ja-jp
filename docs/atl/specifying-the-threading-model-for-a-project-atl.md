---
title: プロジェクトのスレッド モデルの指定 (ATL)
ms.date: 11/04/2016
helpviewer_keywords:
- _ATL_FREE_THREADED macro
- _ATL_APARTMENT_THREADED macro
- ATL, multithreading
- threading [ATL], models
- _ATL_SINGLE_THREADED macro
ms.assetid: 6b571078-521c-4f3e-9f08-482aa235a822
ms.openlocfilehash: 69c1c80bba0b09ce69e0b9b9b27296ef2508e60b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62275218"
---
# <a name="specifying-the-threading-model-for-a-project-atl"></a>プロジェクトのスレッド モデルの指定 (ATL)

次のマクロは、ATL プロジェクトのスレッド モデルを指定できます。

|マクロ|使用に関するガイドライン|
|-----------|--------------------------|
|_ATL_SINGLE_THREADED|場合 1 つのスレッド処理モデルを使用して、すべてのオブジェクトを定義します。|
|_ATL_APARTMENT_THREADED|アパートメント スレッドを使用して 1 つまたは複数のオブジェクトの場合を定義します。|
|_ATL_FREE_THREADED|無料またはニュートラル スレッドを使用して 1 つまたは複数のオブジェクトの場合を定義します。 既存のコードは同等のマクロへの参照を含めることができます[_ATL_MULTI_THREADED](reference/compiler-options-macros.md#_atl_multi_threaded)します。|

プロジェクトのこれらのマクロのいずれかを定義しない場合は、_ATL_FREE_THREADED が有効になります。

マクロは、次のように実行時のパフォーマンスに影響します。

- プロジェクト内のオブジェクトに対応するマクロを指定すると、実行時のパフォーマンスが向上することができます。

- 高いレベルのスレッドですべてのオブジェクトが 1 つ _ATL_APARTMENT_THREADED を指定した場合の例については、マクロを指定すると、実行時のパフォーマンスが若干低下します。

- _ATL_SINGLE_THREADED ときに 1 つを指定するか、またはとフリー スレッドのアパートメント スレッドを使用して、オブジェクトの場合、マクロなどの下位レベルを指定すると、アプリケーションが実行時に失敗する可能性があります。

参照してください[オプション、ATL シンプル オブジェクト ウィザード](../atl/reference/options-atl-simple-object-wizard.md)ATL オブジェクトをモデル化については、スレッド処理します。

## <a name="see-also"></a>関連項目

[概念](../atl/active-template-library-atl-concepts.md)
