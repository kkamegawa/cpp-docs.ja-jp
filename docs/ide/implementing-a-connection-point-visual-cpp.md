---
title: コネクション ポイントを実装する
ms.date: 05/14/2019
helpviewer_keywords:
- connection points [C++], implementing
- implement connection point wizard [C++]
ms.assetid: 5b37e4f9-73c9-4bef-b26d-365bc0662260
ms.openlocfilehash: 8a75a5fbbabd20f4591e3a119c175d68cdfb1f90
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "66182602"
---
# <a name="implement-a-connection-point"></a>コネクション ポイントを実装する

接続ポイントの実装ウィザードを使用してコネクション ポイントを実装するには、ATL COM アプリケーションとしてか、ATL サポートを含む MFC アプリケーションとしてプロジェクトを作成しておく必要があります。 ATL アプリケーションを作成するか、[ATL オブジェクトを MFC アプリケーションに追加して](../mfc/reference/adding-atl-support-to-your-mfc-project.md) MFC アプリケーションの ATL サポートを実装するには、[ATL プロジェクト ウィザード](../atl/reference/atl-project-wizard.md)を利用できます。

> [!NOTE]
> MFC プロジェクトのコネクション ポイントを実装する方法の詳細については、「[コネクション ポイント](../mfc/connection-points.md)」を参照してください。

プロジェクトを作成したら、コネクション ポイントを実装するためには、最初に ATL オブジェクトを追加する必要があります。 ATL プロジェクトにオブジェクトを追加するウィザードの一覧が必要であれば、[ATL プロジェクトにオブジェクトとコントロールを追加する](../atl/reference/adding-objects-and-controls-to-an-atl-project.md)方法に関するページを参照してください。

> [!NOTE]
> このウィザードは、ATL ダイアログ、ATL Server で作成した XML Web サービス、パフォーマンス オブジェクト、パフォーマンス カウンターに対応していません。

接続可能なオブジェクト (ソース) は、その発信インターフェイスごとにコネクション ポイントを表示できます。 各発信インターフェイスは、オブジェクト上のクライアント (シンク) によって実装できます。 詳細については、「[ATL コネクション ポイント](../atl/atl-connection-points.md)」を参照してください。

**コネクション ポイントを実装するには:**

1. クラス ビューで、ATL オブジェクトのクラス名を右クリックします。

1. ショートカット メニューの **[追加]** を選択し、 **[接続ポイントの追加]** を選択して [[接続ポイントの実装ウィザード]](#implement-connection-point-wizard) を表示します。

1. 該当するタイプ ライブラリから実装するコネクション ポイント インターフェイスを選択し、 **[完了]** を選択します。

1. クラス ビューで、コネクション ポイントごとに作成されたプロキシ クラスを確認します。 クラスは CProxy*InterfaceName*\<T> のように表示されます。クラスは [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md) から派生します。

1. コネクション ポイント クラスをダブルクリックすると、コネクション ポイントのクラスの定義が表示されます。

   - 独自のプロジェクトのインターフェイスに対してコネクション ポイントを実装する場合、次の定義が表示されます。

     ```cpp
     template< class T >
     class CProxyInterfaceName :
     public IConnectionPointImpl< T, &IID_InterfaceName >
     {
     public:
     };
     ```

   - ローカル インターフェイスを実装する場合、メソッドとプロパティがクラス本体に表示されます。

   - 別のインターフェイスに対してコネクション ポイントを実行する場合、定義にはインターフェイスのメソッドが含まれます。それぞれ、先頭に `Fire_` が付きます。

## <a name="in-this-section"></a>このセクションの内容

- [接続ポイントの実装ウィザード](#implement-connection-point-wizard)

## <a name="implement-connection-point-wizard"></a>接続ポイントの実装ウィザード

このウィザードでは、COM オブジェクトの接続ポイントを実装できます。 接続可能なオブジェクト (ソース) は、独自のインターフェイスまたは任意の発信インターフェイスの接続ポイントを表示できます。 MSVC と Windows の両方に、発信インターフェイスがあるタイプ ライブラリがあります。 各発信インターフェイスは、オブジェクト上のクライアント (シンク) によって実装できます。

詳細については、「[ATL コネクション ポイント](../atl/atl-connection-points.md)」を参照してください。

- **[Available type libraries]\(使用可能なタイプ ライブラリ\)**

  接続ポイントを実装できるインターフェイスの定義を含む使用可能なタイプ ライブラリを表示します。 省略記号ボタンを選択すると、使用するタイプ ライブラリを含むファイルを見つけることができます。

- **場所**

  **[Available type libraries]\(使用可能なタイプ ライブラリ\)** リストで現在選択されているタイプ ライブラリの場所を表示します。

- **インターフェイス**

  **[使用できるタイプ ライブラリ]** ボックスで現在選択されているタイプ ライブラリに定義が含まれているインターフェイスを表示します。

  |転送ボタン|説明|
  |---------------------|-----------------|
  |**>**|**[Implement connection points]\(接続ポイントを実装する\)** リストに、現在 **[インターフェイス]** リストで選択されているインターフェイス名を追加します。|
  |**>>**|**[Implement connection points]\(接続ポイントを実装する\)** リストに、 **[インターフェイス]** リストで使用可能なすべてのインターフェイス名を追加します。|
  |**\<**|現在 **[Implement connection points]\(接続ポイントを実装する\)** リストで選択されているインターフェイス名を削除します。|
  |**\<\<**|現在 **[Implement connection points]\(接続ポイントを実装する\)** リストに表示されているすべてのインターフェイス名を削除します。|

- **Implement connection points\(接続ポイントを実装する\)**

  **[完了]** を選択したときに接続ポイントを実装する、インターフェイス名を表示します。
