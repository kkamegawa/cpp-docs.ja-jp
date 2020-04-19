---
title: CArchive オブジェクトを作成する 2 つの方法
ms.date: 11/04/2016
f1_keywords:
- CArchive
helpviewer_keywords:
- CArchive class [MFC], closing CArchive objects
- CArchive objects [MFC], closing
- I/O [MFC], creating CArchive objects
- serialization [MFC], CArchive class
- CArchive objects [MFC]
- storage [MFC], CArchive class [MFC]
- data storage [MFC], CArchive class
- CArchive class [MFC], constructor
ms.assetid: aefa28ce-b55c-40dc-9e42-5f038030985d
ms.openlocfilehash: 80e3e73840bce53691c3f5fdafb62c60bdb8f832
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62181511"
---
# <a name="two-ways-to-create-a-carchive-object"></a>CArchive オブジェクトを作成する 2 つの方法

作成する 2 つの方法がある、`CArchive`オブジェクト。

- [フレームワークを使用して CArchive オブジェクトを暗黙的に作成](#_core_implicit_creation_of_a_carchive_object_via_the_framework)

- [CArchive オブジェクトの明示的な作成](#_core_explicit_creation_of_a_carchive_object)

##  <a name="_core_implicit_creation_of_a_carchive_object_via_the_framework"></a> フレームワークを使用して CArchive オブジェクトを暗黙的に作成

最も一般的な簡単な方法は、フレームワークの作成には、`CArchive`保存、名前を付けて保存および開くコマンド ファイル メニューで、ドキュメントのオブジェクト。

フレームワークが、アプリケーションのユーザーがファイル メニューから名前を付けて保存コマンドを発行するときに次に示します。

1. 表示、**名前を付けて保存** ダイアログ ボックスし、ユーザーから、ファイル名を取得します。

1. ユーザーがという名前のファイルを開き、`CFile`オブジェクト。

1. 作成、`CArchive`これが指すオブジェクト`CFile`オブジェクト。 作成する、`CArchive`オブジェクト、フレームワークは、「保存」するモードを設定 (作成、シリアル化)、"load"ではなく (読み取り、逆シリアル化) します。

1. 呼び出し、`Serialize`関数で定義されている、 `CDocument`-派生クラスでへの参照を渡して、`CArchive`オブジェクト。

ドキュメントの`Serialize`関数にデータを書き込みます、`CArchive`オブジェクトを説明します。 戻り時に、`Serialize`関数の場合、フレームワークの破棄、`CArchive`オブジェクトをクリックし、`CFile`オブジェクト。

そのため、フレームワークに作成できるようにする場合、`CArchive`行う必要があるすべては実装するドキュメントのドキュメントのオブジェクト`Serialize`との間のアーカイブを読み書きする関数。 実装しなければ`Serialize`は`CObject`-派生オブジェクトをドキュメントの`Serialize`関数は、直接または間接的にさらにシリアル化します。

##  <a name="_core_explicit_creation_of_a_carchive_object"></a> CArchive オブジェクトの明示的な作成

フレームワークを使用してドキュメントをシリアル化以外にもする必要があります、`CArchive`オブジェクト。 によって表される、クリップボードからデータをシリアル化するなど、`CSharedFile`オブジェクト。 または、フレームワークによって提供されるものとは異なるファイルを保存するためのユーザー インターフェイスを使用したい場合があります。 この場合は、明示的に作成できます、`CArchive`オブジェクト。 これを行う同様、framework では、次の手順を使用します。

#### <a name="to-explicitly-create-a-carchive-object"></a>CArchive オブジェクトを明示的に作成するには

1. 構築、`CFile`から派生したオブジェクトまたはオブジェクト`CFile`します。

1. 渡す、`CFile`オブジェクトのコンス トラクターを`CArchive`次の例のように。

   [!code-cpp[NVC_MFCSerialization#5](../mfc/codesnippet/cpp/two-ways-to-create-a-carchive-object_1.cpp)]

   2 番目の引数、`CArchive`コンス トラクターは、ファイルの格納またはデータの読み込みのアーカイブを使用するかどうかを指定する列挙値。 `Serialize`オブジェクトの関数が呼び出すことによってこの状態をチェック、`IsStoring`アーカイブ オブジェクトの関数。

格納するかからのデータの読み込みが完了したら、`CArchive`オブジェクトを閉じます。 ただし、 `CArchive` (と`CFile`) アーカイブ (およびファイル) のオブジェクトが自動的に閉じ、エラーからの復旧に簡単には、明示的にそのためことをお勧めします。 エラー処理の詳細については、記事を参照してください。[例外。キャッチと削除例外](../mfc/exceptions-catching-and-deleting-exceptions.md)します。

#### <a name="to-close-the-carchive-object"></a>CArchive オブジェクトを閉じる

1. 次の例では、終了する方法を示しています、`CArchive`オブジェクト。

   [!code-cpp[NVC_MFCSerialization#6](../mfc/codesnippet/cpp/two-ways-to-create-a-carchive-object_2.cpp)]

## <a name="see-also"></a>関連項目

[シリアル化: オブジェクトのシリアル化](../mfc/serialization-serializing-an-object.md)
