---
title: ATL (Active Template Library) の概念
ms.date: 05/06/2019
helpviewer_keywords:
- ATL, about ATL
ms.assetid: a3960991-4d76-4da5-9568-3fa7fde53ff4
ms.openlocfilehash: a7b6a40eaed05462f3aa5c877a1c4da3e19c0b03
ms.sourcegitcommit: a10c9390413978d36b8096b684d5ed4cf1553bc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2019
ms.locfileid: "65836999"
---
# <a name="active-template-library-atl-concepts"></a>ATL (Active Template Library) の概念

Active Template Library (ATL) は、小さくて高速のコンポーネント オブジェクト モデル (COM) オブジェクトを作成できる、テンプレートに基づく C++ クラスのセットです。 ストックの実装、デュアル インターフェイス、標準 COM 列挙子インターフェイス、接続ポイント、ティアオフ インターフェイス、ActiveX コントロールなど、COM の重要な機能が特別にサポートされています。

ATL プログラミングを多用する場合は、COM プログラミングが簡単になるように設計されている COM と .NET の属性について、さらに詳しく学習する必要があります。 詳しくは、[Attributed Programming (属性付きプログラミング)](../windows/attributed-programming-concepts.md) に関するページをご覧ください。 (COM および .NET の属性を、C++ 標準\[\[attribute]] 機能と混同しないでください。)

## <a name="in-this-section"></a>このセクションの内容

[COM と ATL の概要](../atl/introduction-to-com-and-atl.md)<br/>
コンポーネント オブジェクト モデル (COM) の背後にある主要な概念について説明します。 ここでは、ATL とはどのようなもので、どういうときに使う必要があるかについても簡単に説明します。

[ATL COM オブジェクトの基礎](../atl/fundamentals-of-atl-com-objects.md)<br/>
さまざまな ATL クラスの間の関係と、それらのクラスを実装する方法について説明します。

[デュアル インターフェイスと ATL](../atl/dual-interfaces-and-atl.md)<br/>
ATL の観点からデュアル インターフェイスについて説明します。

[ATL のコレクションと列挙子](../atl/atl-collections-and-enumerators.md)<br/>
ATL でのコレクションと列挙子の実装および作成について説明します。

[複合コントロールの基本](../atl/atl-composite-control-fundamentals.md)<br/>
複合コントロールを作成する詳細な手順について説明します。 複合コントロールは、他の ActiveX コントロールまたは Windows コントロールを含むことができる ActiveX コントロールの種類です。

[ATL コントロール コンテインメント : Q & A 集](../atl/atl-control-containment-faq.md)<br/>
ATL でのコントロールのホストに関連する基本的な質問について説明します。

[ATL COM プロパティ ページ](../atl/atl-com-property-pages.md)<br/>
COM プロパティ ページを指定および実装する方法を示します。

[DHTML コントロールの ATL サポート](../atl/atl-support-for-dhtml-controls.md)<br/>
DHTML コントロールを作成する詳細な手順について説明します。

[ATL コネクション ポイント](../atl/atl-connection-points.md)<br/>
接続ポイントの概要と ATL での実装方法について説明します。

[イベント処理と ATL](../atl/event-handling-and-atl.md)<br/>
ATL の [IDispEventImpl](../atl/reference/idispeventimpl-class.md) および [IDispEventSimpleImpl](../atl/reference/idispeventsimpleimpl-class.md) クラスを使って COM イベントを処理するために必要な手順について説明します。

[ATL とフリー スレッド マーシャラー](../atl/atl-and-the-free-threaded-marshaler.md)<br/>
独自のクラスでフリー スレッド マーシャラー (FTM) を集計できるようにする ATL シンプル オブジェクト ウィザードのオプションの詳細を説明します。

[プロジェクトのスレッド モデルの指定](../atl/specifying-the-threading-model-for-a-project-atl.md)<br/>
プロジェクトでのスレッドに関連する実行時のパフォーマンスの制御に使用できるマクロについて説明します。

[ATL モジュール クラス](../atl/atl-module-classes.md)<br/>
ATL 7.0 の新しいモジュール クラスについて説明します。 モジュール クラスでは、ATL で必要な基本機能が実装されています。

[ATL サービス](../atl/atl-services.md)<br/>
サービスが実装されるときに発生する一連のイベントについて説明します。 サービスの開発に関連する概念についても説明します。

[ATL ウィンドウ クラス](../atl/atl-window-classes.md)<br/>
ATL でスーパークラス ウィンドウとサブクラス ウィンドウを作成する方法について説明します。 ATL ウィンドウ クラスは COM クラスではありません。

[ATL コレクション クラス](../atl/atl-collection-classes.md)<br/>
ATL で配列とマップを使用する方法について説明します。

[ATL レジストリ コンポーネント (レジストラー)](../atl/atl-registry-component-registrar.md)<br/>
ATL のスクリプト構文と置き換え可能パラメーターについて説明します。 また、レジストラーへの静的リンクを設定する方法も説明します。

[ATL および C ランタイム コードによるプログラミング](../atl/programming-with-atl-and-c-run-time-code.md)<br/>
C ランタイム ライブラリ (CRT) への静的または動的なリンクの利点について説明します。

[CComBSTR を使用したプログラミング](../atl/programming-with-ccombstr-atl.md)<br/>
`CComBSTR` でプログラミングするときに注意する必要のあるいくつかの状況について説明します。

[エンコーディングのリファレンス](../atl/atl-encoding-reference.md)<br/>
atlenc.h の uuencode、hexadecimal、UTF8 など、一般的なインターネット標準でのエンコードをサポートする関数とマクロを提供します。

[ユーティリティのリファレンス](../atl/atl-utilities-reference.md)<br/>
[CPathT](../atl/reference/cpatht-class.md) および [CUrl](../atl/reference/curl-class.md) の形式のパスと URL を操作するためのコードを提供します。 スレッド プール [CThreadPool](../atl/reference/cthreadpool-class.md) を独自のアプリケーションで使用できます。 このコードは、atlpath.h および atlutil.h に含まれます。

## <a name="related-sections"></a>関連項目

[ATL チュートリアル](../atl/active-template-library-atl-tutorial.md)<br/>
コントロールの作成手順について説明し、プロセスでの ATL の基本を示します。

[ATL のサンプル](../overview/visual-cpp-samples.md)<br/>
ATL のサンプル プログラムの説明とリンクを提供します。

[ATL プロジェクトの作成](../atl/reference/creating-an-atl-project.md)<br/>
ATL プロジェクト ウィザードについての説明が含まれます。

[ATL コントロール ウィザード](../atl/reference/atl-control-wizard.md)<br/>
クラスを追加する方法について説明します。

[属性付きプログラミング](../windows/attributed-programming-concepts.md)<br/>
属性を使って COM プログラミングを簡単にする方法の概要を説明し、さらに詳細なトピックへのリンクを提供します。

[ATL のクラスの概要](../atl/atl-class-overview.md)<br/>
ATL クラスに関する参照情報とリンクを提供します。
