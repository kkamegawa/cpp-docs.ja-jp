---
title: コレクション
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, collections
- arrays [MFC], classes
- MFC collection classes
- shapes, collection
- collection classes [MFC], MFC
- collections, about collections
- array templates [MFC]
- collection classes [MFC], template-based
- collection classes [MFC], about collection classes
- collection classes [MFC], maps
- collection classes [MFC], arrays
- shapes
- collection classes [MFC], lists
- collection classes [MFC], shapes
ms.assetid: 02586e4c-851d-41d0-a722-feb11c17c74c
ms.openlocfilehash: f3dea68deaae73313fe389be49e8bbed7da3c93a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383848"
---
# <a name="collections"></a>コレクション

Microsoft Foundation Class ライブラリは、オブジェクトのグループを管理するコレクション クラスを提供します。 これらのクラスは、2 種類のことです。

- [C++ テンプレートから作成されたコレクション クラス](#_core_the_template_based_collection_classes)

- [コレクション クラスをテンプレートから作成されません。](#_core_the_collection_classes_not_based_on_templates)

> [!NOTE]
>  コードが既に非テンプレート コレクション クラスを使用する場合は、それらを使用する続行することができます。 独自のデータ型の新しいタイプ セーフなコレクション クラスを記述する場合は、新しいテンプレート ベースのクラスを使用することをお勧めします。

##  <a name="_core_collection_shapes"></a> コレクションの形状

コレクション クラスは、その要素の種類とその「形状」によって特徴付けられます。 図形は、オブジェクトが編成され、コレクションに格納する方法を参照します。 MFC には、次の 3 つの基本的なコレクションの形状が用意されています。 リスト、配列、および (ディクショナリとも呼ばれます) をマップします。 特定のプログラミングの問題に最も適したコレクションの形状を選択できます。

指定されたコレクションの 3 つの図形のそれぞれについては、このトピックの後半について簡単に説明します。 これは、プログラムの最適な決定に役立つ図形の機能を比較するを参照してください。[コレクション クラスの選択に関する推奨事項](../mfc/recommendations-for-choosing-a-collection-class.md)します。

- リスト

   List クラスはダブルリンク リストとして実装されている要素の順序付けられたインデックスなしのリストを提供します。 一覧は、"head"と"tail"と、要素を削除、先頭または末尾、または挿入または削除、中間の要素を追加または高速です。

- 配列

   Array クラスは、オブジェクトの配列を動的にサイズ変更、順序付けられたや整数インデックスを提供します。

- マップ (ディクショナリとも呼ばれます)

   マップは、キー オブジェクトを値オブジェクトに関連付けられるコレクションです。

##  <a name="_core_the_template_based_collection_classes"></a> テンプレート ベースのコレクション クラス

任意の型のオブジェクトを格納するタイプ セーフなコレクションを実装する最も簡単な方法では、テンプレート ベースの MFC クラスのいずれかを使用します。 これらのクラスの例については、MFC のサンプルを参照してください。[収集](../overview/visual-cpp-samples.md)します。

次の表では、MFC のテンプレート ベースのコレクション クラスを示します。

### <a name="collection-template-classes"></a>テンプレートのコレクション クラス

|コレクションの内容|配列|表示内容|マップ|
|-------------------------|------------|-----------|----------|
|任意の型のオブジェクトのコレクション|`CArray`|`CList`|`CMap`|
|任意の型のオブジェクトへのポインターのコレクション|`CTypedPtrArray`|`CTypedPtrList`|`CTypedPtrMap`|

##  <a name="_core_the_collection_classes_not_based_on_templates"></a> テンプレートに基づいていないコレクション クラス

アプリケーションで既に MFC 非テンプレート クラスを使用する場合は、それらを使用する続行することができます。 ただし、新しいコレクションの場合は、テンプレート ベースのクラスを使用することを勧めします。 次の表では、テンプレートに基づいていない MFC コレクション クラスを示します。

### <a name="nontemplate-collection-classes"></a>非テンプレート コレクション クラス

|配列|表示内容|マップ|
|------------|-----------|----------|
|`CObArray`|`CObList`|`CMapPtrToWord`|
|`CByteArray`|`CPtrList`|`CMapPtrToPtr`|
|`CDWordArray`|`CStringList`|`CMapStringToOb`|
|`CPtrArray`||`CMapStringToPtr`|
|`CStringArray`||`CMapStringToString`|
|`CWordArray`||`CMapWordToOb`|
|`CUIntArray`||`CMapWordToPtr`|

MFC コレクション クラスの特性がテーブルに[コレクション クラスの選択に関する推奨事項](../mfc/recommendations-for-choosing-a-collection-class.md)これらの特性 (形状) 以外の観点からの MFC コレクション クラスについて説明します。

- クラスで C++ テンプレートを使用しているかどうか

- コレクションに格納されている要素をシリアル化できるかどうか

- コレクションに格納されている要素を診断用にダンプできるかどうか

- タイプ セーフなコレクションかどうか

### <a name="what-do-you-want-to-do"></a>どうしたいんですか

#### <a name="general-collection-class-tasks"></a>コレクション クラスの一般的なタスク

- [コレクション クラスの選択に関する推奨事項](../mfc/recommendations-for-choosing-a-collection-class.md)

- [方法: タイプ セーフなコレクションを作成する](../mfc/how-to-make-a-type-safe-collection.md)

- [スタック コレクションとキュー コレクションの作成](../mfc/creating-stack-and-queue-collections.md)

- [CArray::Add](../mfc/reference/carray-class.md#add)

#### <a name="template-based-collection-class-tasks"></a>テンプレート ベースのコレクション クラスの操作

- [テンプレート ベースのクラス](../mfc/template-based-classes.md)

#### <a name="accessing-the-members-of-a-collection-template-based-or-not"></a>コレクションのメンバーにアクセスする (テンプレートに基づくかどうか)

- [コレクションの全メンバーへのアクセス](../mfc/accessing-all-members-of-a-collection.md)

- [CObject コレクションの全オブジェクトの削除](../mfc/deleting-all-objects-in-a-cobject-collection.md)

## <a name="see-also"></a>関連項目

[概念](../mfc/mfc-concepts.md)<br/>
[MFC の一般的なトピック](../mfc/general-mfc-topics.md)
