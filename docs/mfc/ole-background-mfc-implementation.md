---
title: OLE の背景知識:MFC における実装
ms.date: 11/04/2016
f1_keywords:
- IMarshall
- IMoniker
helpviewer_keywords:
- MFC libraries, implementing
- OLE MFC library implementation
- OLE IMarshal interface
- IMoniker interface, MFC
- IMarshall class [MFC]
- OLE, compound files
- OLE IMoniker interface
- OLE IUnknown
ms.assetid: 2b67016a-d78e-4d60-925f-c28ec8fb6180
ms.openlocfilehash: f793c7d7303a49057e46c32eb658ea7eea8e9ccc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62186730"
---
# <a name="ole-background-mfc-implementation"></a>OLE の背景知識:MFC における実装

サイズと生 OLE API の複雑さは、OLE アプリケーションを作成するには、直接呼び出す非常に時間がかかることができます。 OLE の Microsoft Foundation Class ライブラリの実装の目的は、すべての機能を OLE 対応のアプリケーションを作成するために必要な作業の量を削減します。

この記事では、MFC の内部に実装されていない OLE API の各部分について説明します。 ディスカッションでは、Windows SDK の OLE セクションに実装されますがマップする方法についても説明します。

##  <a name="_core_portions_of_ole_not_implemented_by_the_class_library"></a> クラス ライブラリで実装されていない OLE の部分

いくつかのインターフェイスと OLE の機能は直接提供されません MFC で。 これらの機能を使用する場合は、OLE API を直接呼び出すことができます。

IMoniker インターフェイス、`IMoniker`インターフェイス、クラス ライブラリによって実装されます (たとえば、`COleServerItem`クラス)、プログラマが既に公開されていないが、します。 このインターフェイスの詳細については、OLE モニカーでの実装、Windows SDK の OLE セクションを参照してください。 ただし、参照クラス[CMonikerFile](../mfc/reference/cmonikerfile-class.md)と[CAsyncMonikerFile](../mfc/reference/casyncmonikerfile-class.md)します。

IUnknown と IMarshal インターフェイス、`IUnknown`インターフェイス、クラス ライブラリによって実装されますが、プログラマは公開されません。 `IMarshal`インターフェイスはクラス ライブラリによって実装されていませんが、内部的に使用されます。 既にクラス ライブラリを使用して作成したオートメーション サーバーがある機能が組み込まれたをマーシャ リングします。

Docfiles (複合ファイル) 複合ファイルは、クラス ライブラリによって部分的にサポートします。 ファイルの作成以外の複合を直接操作する関数のサポートされていません。 MFC クラスを使用して`COleFileStream`ファイルの標準的な関数を含むストリームの操作をサポートします。 詳細については、この記事を参照してください。[コンテナー。複合ファイル](../mfc/containers-compound-files.md)します。

インプロセス サーバー、およびオブジェクト ハンドラーのプロセスでサーバーおよびオブジェクト ハンドラーは、ビジュアルのデータを編集またはダイナミック リンク ライブラリ (DLL) で完全なコンポーネント オブジェクト モデル (COM) オブジェクトの実装を使用できます。 これを行うには、OLE API を直接呼び出すことによって、DLL を実装できます。 ただし、オートメーション サーバーを作成しているユーザー インターフェイスを持っていない場合は、サーバー、プロセスでサーバーにし、DLL に完全に配置する AppWizard を使用できます。 これらのトピックの詳細については、次を参照してください。[オートメーション サーバー](../mfc/automation-servers.md)します。

> [!TIP]
>  オートメーション サーバーを実装する最も簡単な方法では、DLL に配置します。 MFC には、このアプローチがサポートされています。

Microsoft Foundation OLE クラスが OLE インターフェイスを実装する方法の詳細については、MFC テクニカル ノートを参照してください。 [38](../mfc/tn038-mfc-ole-iunknown-implementation.md)、 [39](../mfc/tn039-mfc-ole-automation-implementation.md)、および[40](../mfc/tn040-mfc-ole-in-place-resizing-and-zooming.md)します。

## <a name="see-also"></a>関連項目

[OLE の背景知識](../mfc/ole-background.md)<br/>
[OLE の背景知識: 実装戦略](../mfc/ole-background-implementation-strategies.md)
