---
title: ランタイム クラス情報へのアクセス方法
ms.date: 11/04/2016
helpviewer_keywords:
- CObject class [MFC], and RTTI
- CObject class [MFC], using IsKindOf method [MFC]
- run time [MFC], class information
- RUNTIME_CLASS macro [MFC]
- CObject class [MFC], using RUNTIME_CLASS macro [MFC]
- RTTI compiler option [MFC]
- CObject class [MFC], accessing run-time class information
- run time [MFC]
- IsKindOf method method [MFC]
- run-time class [MFC], accessing information
- classes [MFC], run-time class information
- run-time class [MFC]
- RUNTIME_CLASS macro, using
ms.assetid: 3445a9af-0bd6-4496-95c3-aa59b964570b
ms.openlocfilehash: 2e4f8685033fc7a8a2f49dafa7ef4e4e019d8989
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392948"
---
# <a name="accessing-run-time-class-information"></a>ランタイム クラス情報へのアクセス方法

この記事では、実行時にオブジェクトのクラスに関する情報にアクセスする方法について説明します。

> [!NOTE]
>  MFC を使わない、[実行時型情報](../cpp/run-time-type-information.md)Visual C 4.0 で導入された (RTTI) のサポート。

クラスを派生する場合[CObject](../mfc/reference/cobject-class.md)ために使用して、 **DECLARE**_**動的**と`IMPLEMENT_DYNAMIC`、`DECLARE_DYNCREATE`と`IMPLEMENT_DYNCREATE`、または、 `DECLARE_SERIAL`と`IMPLEMENT_SERIAL`マクロは、情報の記事で説明されている[CObject からクラスを派生する](../mfc/deriving-a-class-from-cobject.md)、`CObject`クラスには、実行時にオブジェクトの正確なクラスを特定する機能。

この機能は、特別な型チェック関数の引数が必要なとき、およびオブジェクトのクラスに基づく特殊なコードを記述する必要がありますに最も便利です。 ただし、この実習は、通常は推奨されませんので、仮想関数の機能を複製します。

`CObject`メンバー関数は`IsKindOf`特定のオブジェクトが、指定されたクラスに属している場合、または特定のクラスから派生される場合を判断するために使用できます。 引数に`IsKindOf`は、`CRuntimeClass`オブジェクトを使用して取得したことができます、`RUNTIME_CLASS`マクロをクラスの名前。

### <a name="to-use-the-runtimeclass-macro"></a>RUNTIME_CLASS マクロを使用するには

1. 使用`RUNTIME_CLASS`クラスには、ここに示すように、クラスの名前を持つ`CObject`:

   [!code-cpp[NVC_MFCCObjectSample#4](../mfc/codesnippet/cpp/accessing-run-time-class-information_1.cpp)]

ランタイム クラスのオブジェクトに直接アクセスする必要はほとんどありません。 一般的な使用がランタイム クラスのオブジェクトを渡すには、`IsKindOf`関数は、次の手順で示すようにします。 `IsKindOf`関数は、特定のクラスに属しているかどうかに表示するオブジェクトをテストします。

#### <a name="to-use-the-iskindof-function"></a>IsKindOf 関数を使用するには

1. このクラスには、ランタイム クラスのサポートを確認します。 つまり、クラスは、する必要がありますが派生されている直接的または間接的にから`CObject`ために使用して、 **DECLARE**_**動的**と`IMPLEMENT_DYNAMIC`、`DECLARE_DYNCREATE`と`IMPLEMENT_DYNCREATE`、または、 `DECLARE_SERIAL`と`IMPLEMENT_SERIAL`マクロは、情報の記事で説明されている[CObject からクラスを派生する](../mfc/deriving-a-class-from-cobject.md)します。

1. 呼び出す、 `IsKindOf` 、そのクラスのオブジェクトのメンバー関数を使用して、`RUNTIME_CLASS`を生成するマクロ、`CRuntimeClass`引数は、次のように。

   [!code-cpp[NVC_MFCCObjectSample#2](../mfc/codesnippet/cpp/accessing-run-time-class-information_2.h)]

   [!code-cpp[NVC_MFCCObjectSample#5](../mfc/codesnippet/cpp/accessing-run-time-class-information_3.cpp)]

    > [!NOTE]
    >  IsKindOf 返します**TRUE**オブジェクトまたは指定したクラスから派生したクラスの指定したクラスのメンバーである場合。 `IsKindOf` 必要に応じて、派生 Microsoft Foundation classes の多重継承を使用できますに複数の継承または仮想基底クラスをサポートしません。

ランタイム クラス情報の用途の 1 つが、オブジェクトの動的に作成します。 このプロセスが、記事で説明した[オブジェクトの動的生成](../mfc/dynamic-object-creation.md)します。

ランタイム クラス情報とシリアル化についての詳細を記事をご覧ください。 [MFC のファイル](../mfc/files-in-mfc.md)と[シリアル化](../mfc/serialization-in-mfc.md)します。

## <a name="see-also"></a>関連項目

[CObject の使い方](../mfc/using-cobject.md)
