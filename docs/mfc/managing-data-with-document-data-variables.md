---
title: ドキュメント データ変数を使ったデータ管理
ms.date: 11/04/2016
helpviewer_keywords:
- documents [MFC], data storage
- friend classes [MFC]
- classes [MFC], friend
- data [MFC]
- data [MFC], documents
- collection classes [MFC], used by document object
- document data [MFC]
- member variables [MFC], document class [MFC]
ms.assetid: e70b87f4-8c30-49e5-8986-521c2ff91704
ms.openlocfilehash: dc21bd4b3dbe7609a33af4b4f93f15a3f5c9a64e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62151996"
---
# <a name="managing-data-with-document-data-variables"></a>ドキュメント データ変数を使ったデータ管理

ドキュメント クラスのメンバー変数としては、ドキュメントのデータを実装します。 たとえば、Scribble プログラムは型のデータ メンバーを宣言します。 `CObList` — へのポインターを格納するためのリンクされたリスト`CObject`オブジェクト。 この一覧を使用して、フリーハンド線画を構成する点の配列を格納します。

ドキュメントのメンバー データを実装する方法は、アプリケーションの性質によって異なります。 アウトするために、MFC には「コレクション クラス」のグループ-配列、リスト、および C++ テンプレートに基づくコレクションを含むマップ (辞書)、-など、さまざまな一般的なデータ型をカプセル化するクラスと共に`CString`、 `CRect`、 `CPoint`、 `CSize`、および`CTime`します。 これらのクラスの詳細については、次を参照してください。、[クラス ライブラリの概要](../mfc/class-library-overview.md)で、 *MFC リファレンス*します。

ドキュメントのメンバー データを定義するときに設定しデータの項目を取得し、それらの他の便利な操作を実行するには、ドキュメント クラスには、通常のメンバー関数を追加します。

ビュー、ビューの作成時にインストールされているドキュメントに、ビューのポインターを使用して、ドキュメント オブジェクトにアクセスします。 このビューのメンバー関数ポインターを取得するには呼び出すことによって、`CView`メンバー関数は`GetDocument`します。 独自のドキュメントの種類には、このポインターにキャストしてください。 ポインターを通じてパブリック ドキュメントのメンバーにアクセスすることができます。

データ転送を頻繁には、直接アクセスが必要です、またはドキュメント クラスの非パブリック メンバーを使用する、クラスのドキュメント クラスのフレンド (C++ の用語) で、ビューに変更したい場合があります。

## <a name="see-also"></a>関連項目

[ドキュメントの使い方](../mfc/using-documents.md)
