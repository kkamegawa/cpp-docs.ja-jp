---
title: ATL クラスと構造体 |Microsoft Docs
ms.date: 05/03/2018
helpviewer_keywords:
- classes [C++], ATL
- ATL, classes
ms.assetid: 7da42e2d-ac84-4506-92bd-502a86d68bdc
ms.openlocfilehash: 2bf13700ada3284b8a32718d21971e89e30e5b76
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498045"
---
# <a name="atl-classes-and-structs"></a>ATL クラスと構造体

Active Template Library (ATL) には、次のクラスと構造体が含まれています。 カテゴリで特定のクラスを検索するには、「 [ATL クラスの概要](../../atl/atl-class-overview.md)」を参照してください。

|クラス/構造体|説明|ヘッダー ファイル|
|-----------|-----------------|-----------------|
|[ATL_DRAWINFO](../../atl/reference/atl-drawinfo-structure.md)|プリンター、メタファイル、ActiveX コントロールなどのさまざまなターゲットにレンダリングするために使用される情報を格納します。|atlctl.h|
|[_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md)|ATL のウィンドウコードにクラスインスタンスデータを格納します。|atlbase. h|
|[_ATL_BASE_MODULE70](../../atl/reference/atl-base-module70-structure.md)|ATL を使用するすべてのプロジェクトで使用されます。|atlbase. h|
|[_ATL_COM_MODULE70](../../atl/reference/atl-com-module70-structure.md)|ATL の COM 関連コードによって使用されます。| atlbase. h|
|[_ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md)|ディスパッチインターフェイスのメソッドまたはプロパティを記述するために使用される型情報を格納します。|atlcom.h|
|[_ATL_MODULE70](../../atl/reference/atl-module70-structure.md)|すべての ATL モジュールで使用されるデータを格納します。|atlbase. h|
|[_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md)|ATL のウィンドウコードによって使用されます。|atlbase. h|
|[CA2AEX](../../atl/reference/ca2aex-class.md)|このクラスは、文字列変換マクロ CA2TEX と CT2AEX、および typedef CA2A によって使用されます。|atlconv.h|
|[CA2CAEX](../../atl/reference/ca2caex-class.md)|このクラスは、文字列変換マクロ CA2CTEX と CT2CAEX、および typedef CA2CA によって使用されます。|atlconv.h|
|[CA2WEX](../../atl/reference/ca2wex-class.md)|このクラスは、文字列変換マクロ CA2TEX、CA2CTEX、CT2WEX、CT2CWEX、および typedef CA2W によって使用されます。|atlconv.h|
|[CAccessToken](../../atl/reference/caccesstoken-class.md)|このクラスは、アクセストークンのラッパーです。|atlsecurity.h|
|[CAcl](../../atl/reference/cacl-class.md)|このクラスは、ACL (アクセス制御リスト) 構造のラッパーです。|atlsecurity.h|
|[CAdapt](../../atl/reference/cadapt-class.md)|このテンプレートは、オブジェクトのアドレス以外の値を返すために、アドレス演算子を再定義するクラスをラップするときに使用されます。|atlcomcli.h|
|[CAtlArray](../../atl/reference/catlarray-class.md)|このクラスは、配列オブジェクトを実装します。|atlcoll.h|
|[CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md)|このクラスは、スレッドプールされたアパートメントモデルの COM サーバーを実装します。|atlbase. h|
|[CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md)|このクラスは、スレッドプールされたアパートメントモデル COM サーバーを実装するためのメソッドを提供します。|atlbase. h|
|[CAtlBaseModule](../../atl/reference/catlbasemodule-class.md)|このクラスは、すべての ATL プロジェクトでインスタンス化されます。|atlcore.h|
|[CAtlComModule](../../atl/reference/catlcommodule-class.md)|このクラスは、COM サーバーモジュールを実装します。|atlbase. h|
|[CAtlDebugInterfacesModule](../../atl/reference/catldebuginterfacesmodule-class.md)|このクラスは、インターフェイスのデバッグをサポートします。|atlbase. h|
|[CAtlDllModuleT](../../atl/reference/catldllmodulet-class.md)|このクラスは、DLL のモジュールを表します。|atlbase. h|
|[CAtlException](../../atl/reference/catlexception-class.md)|このクラスは、ATL 例外を定義します。|atlexcept.h|
|[CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md)|このクラスは、アプリケーションのモジュールを表します。|atlbase. h|
|[CAtlFile](../../atl/reference/catlfile-class.md)|このクラスは、Windows ファイル処理 API のシンラッパーを提供します。|atlfile.h|
|[CAtlFileMapping](../../atl/reference/catlfilemapping-class.md)|このクラスは、 [CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)のメソッドにキャスト演算子を追加して、メモリマップトファイルを表します。|atlfile.h|
|[CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)|このクラスは、メモリマップトファイルを表します。|atlfile.h|
|[CAtlList](../../atl/reference/catllist-class.md)|このクラスには、リストオブジェクトを作成および管理するためのメソッドが用意されています。|atlcoll.h|
|[CAtlMap](../../atl/reference/catlmap-class.md)|このクラスには、マップオブジェクトを作成および管理するためのメソッドが用意されています。|atlcoll.h|
|[CAtlModule](../../atl/reference/catlmodule-class.md)|このクラスは、いくつかの ATL モジュールクラスによって使用されるメソッドを提供します。|atlbase. h|
|[CAtlModuleT](../../atl/reference/catlmodulet-class.md)|このクラスは ATL モジュールを実装します。|atlbase. h|
|[CAtlPreviewCtrlImpl](../../atl/reference/catlpreviewctrlimpl-class.md)|このクラスは、リッチプレビュー用のシェルによって提供されるホストウィンドウに配置されるウィンドウの ATL 実装です。|atlpreviewctrlimpl.h|
|[CAtlServiceModuleT](../../atl/reference/catlservicemodulet-class.md)|このクラスは、サービスを実装します。|atlbase. h|
|[CAtlTemporaryFile](../../atl/reference/catltemporaryfile-class.md)|このクラスには、一時ファイルを作成して使用するためのメソッドが用意されています。|atlfile.h|
|[CAtlTransactionManager](../../atl/reference/catltransactionmanager-class.md)|このクラスは、カーネルトランザクションマネージャー (KTM) 関数のラッパーを提供します。|atltransactionmanager. h|
|[CAtlWinModule](../../atl/reference/catlwinmodule-class.md)|このクラスは、ATL ウィンドウコンポーネントをサポートします。|atlbase. h|
|[CAutoPtr](../../atl/reference/cautoptr-class.md)|このクラスは、スマートポインターオブジェクトを表します。|atlbase. h|
|[CAutoPtrArray](../../atl/reference/cautoptrarray-class.md)|このクラスには、スマートポインターの配列を構築するときに役立つメソッドが用意されています。|atlbase. h|
|[CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md)|このクラスには、スマートポインターのコレクションを作成するときに役立つメソッド、静的関数、および typedef が用意されています。|atlcoll.h|
|[CAutoPtrList](../../atl/reference/cautoptrlist-class.md)|このクラスには、スマートポインターのリストを構築するときに役立つメソッドが用意されています。|atlcoll.h|
|[CAutoVectorPtr](../../atl/reference/cautovectorptr-class.md)|このクラスは、vector new および delete 演算子を使用したスマートポインターオブジェクトを表します。|atlbase. h|
|[CAutoVectorPtrElementTraits](../../atl/reference/cautovectorptrelementtraits-class.md)|このクラスは、vector new および delete 演算子を使用してスマートポインターのコレクションを作成するときに役立つメソッド、静的関数、および typedef を提供します。|atlcoll.h|
|[CAxDialogImpl](../../atl/reference/caxdialogimpl-class.md)|このクラスは、ActiveX コントロールをホストするダイアログボックス (モーダルまたはモードレス) を実装します。|atlwin.h|
|[CAxWindow](../../atl/reference/caxwindow-class.md)|このクラスには、ActiveX コントロールをホストしているウィンドウを操作するためのメソッドが用意されています。|atlwin.h|
|[CAxWindow2T](../../atl/reference/caxwindow2t-class.md)|このクラスは、ActiveX コントロールをホストし、ライセンスされた ActiveX コントロールのホストをサポートするウィンドウを操作するためのメソッドを提供します。|atlwin.h|
|[CBindStatusCallback](../../atl/reference/cbindstatuscallback-class.md)|このクラスは、 `IBindStatusCallback` インターフェイスを実装します。|atlctl.h|
|[CComAggObject](../../atl/reference/ccomaggobject-class.md)|このクラスは、集計されたオブジェクトに対して[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)を実装します。|atlcom.h|
|[CComAllocator](../../atl/reference/ccomallocator-class.md)|このクラスには、COM メモリルーチンを使用してメモリを管理するためのメソッドが用意されています。|atlbase. h|
|[CComApartment](../../atl/reference/ccomapartment-class.md)|このクラスは、スレッドプールされた EXE モジュールでアパートメントを管理するためのサポートを提供します。|atlbase. h|
|[CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md)|このクラスには、クリティカルセクションオブジェクトの所有権を取得および解放するためのメソッドが用意されています。|atlcore.h|
|[CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)|Atl 7.0 の場合、 `CComAutoThreadModule`は廃止されています。詳細については、「 [atl モジュール](../../atl/atl-module-classes.md)」を参照してください。|atlbase. h|
|[CComBSTR](../../atl/reference/ccombstr-class.md)|このクラスは、Bstr のラッパーです。|atlbase. h|
|[CComCachedTearOffObject](../../atl/reference/ccomcachedtearoffobject-class.md)|このクラスは、ティアオフインターフェイスの[IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown)を実装します。|atlcom.h|
|[CComClassFactory](../../atl/reference/ccomclassfactory-class.md)|このクラスは、 [IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)インターフェイスを実装します。|atlcom.h|
|[CComClassFactory2](../../atl/reference/ccomclassfactory2-class.md)|このクラスは、 [IClassFactory2](/windows/win32/api/ocidl/nn-ocidl-iclassfactory2)インターフェイスを実装します。|atlcom.h|
|[CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)|このクラスは、 [IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory)インターフェイスを実装し、複数のアパートメントでオブジェクトを作成できるようにします。|atlcom.h|
|[CComClassFactorySingleton](../../atl/reference/ccomclassfactorysingleton-class.md)|このクラスは、 [CComClassFactory](../../atl/reference/ccomclassfactory-class.md)から派生し、 [CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)を使用して1つのオブジェクトを構築します。|atlcom.h|
|[CComCoClass](../../atl/reference/ccomcoclass-class.md)|このクラスには、クラスのインスタンスを作成し、そのプロパティを取得するためのメソッドが用意されています。|atlcom.h|
|[CComCompositeControl](../../atl/reference/ccomcompositecontrol-class.md)|このクラスは、複合コントロールを実装するために必要なメソッドを提供します。|atlctl.h|
|[CComContainedObject](../../atl/reference/ccomcontainedobject-class.md)|このクラスは、所有者オブジェクトの`IUnknown`に委任することによって [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) を実装します。|atlcom.h|
|[CComControl](../../atl/reference/ccomcontrol-class.md)|このクラスには、ATL コントロールを作成および管理するためのメソッドが用意されています。|atlctl.h|
|[CComControlBase](../../atl/reference/ccomcontrolbase-class.md)|このクラスには、ATL コントロールを作成および管理するためのメソッドが用意されています。|atlctl.h|
|[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)|このクラスには、クリティカルセクションオブジェクトの所有権を取得および解放するためのメソッドが用意されています。|atlcore.h|
|[CComCritSecLock](../../atl/reference/ccomcritseclock-class.md)|このクラスには、クリティカルセクションオブジェクトをロックおよびロック解除するためのメソッドが用意されています。|atlbase. h|
|[CComCurrency](../../atl/reference/ccomcurrency-class.md)|このクラスには、CURRENCY オブジェクトを作成および管理するためのメソッドと演算子が用意されています。|atlcur .h です。|
|[CComDynamicUnkArray](../../atl/reference/ccomdynamicunkarray-class.md)|このクラスは、ポインターの`IUnknown`配列を格納します。|atlcom.h|
|[CComEnum](../../atl/reference/ccomenum-class.md)|このクラスは、配列に基づいて COM 列挙子オブジェクトを定義します。|atlcom.h|
|[CComEnumImpl](../../atl/reference/ccomenumimpl-class.md)|このクラスは、列挙される項目が配列に格納される COM 列挙子インターフェイスの実装を提供します。|atlcom.h|
|[CComEnumOnSTL](../../atl/reference/ccomenumonstl-class.md)|このクラスは、 C++標準ライブラリコレクションに基づいて COM 列挙子オブジェクトを定義します。|atlcom.h|
|[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)|このクラスでは、 [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)と同じメソッドが提供されますが、クリティカルセクションは提供されません。|atlcore.h|
|[CComGITPtr](../../atl/reference/ccomgitptr-class.md)|このクラスには、インターフェイスポインターとグローバルインターフェイステーブル (GIT) を処理するためのメソッドが用意されています。|atlbase. h|
|[CComHeap](../../atl/reference/ccomheap-class.md)|このクラスは、COM メモリ割り当て関数を使用して[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)を実装します。|ATLComMem.h|
|[CComHeapPtr](../../atl/reference/ccomheapptr-class.md)|ヒープポインターを管理するためのスマートポインタークラス。|atlbase. h|
|[CComModule](../../atl/reference/ccommodule-class.md)|Atl 7.0 の場合、 `CComModule`は廃止されています。詳細については、「 [atl モジュール](../../atl/atl-module-classes.md)」を参照してください。|atlbase. h|
|[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)|このクラスは、変数の値をインクリメントおよびデクリメントするためのスレッドセーフなメソッドを提供します。|atlbase. h|
|[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)|このクラスは、クリティカルセクションのロックまたはロック解除機能を使用せずに、変数の値をインクリメントおよびデクリメントするためのスレッドセーフなメソッドを提供します。|atlbase. h|
|[CComObject](../../atl/reference/ccomobject-class.md)|このクラスは`IUnknown` 、非集計オブジェクトに対してを実装します。|atlcom.h|
|[CComObjectGlobal](../../atl/reference/ccomobjectglobal-class.md)|このクラスは、 `Base`オブジェクトを含むモジュールの参照カウントを管理します。|atlcom.h|
|[CComObjectNoLock](../../atl/reference/ccomobjectnolock-class.md)|このクラスは`IUnknown` 、非集計オブジェクトに対してを実装しますが、コンストラクターのモジュールロック数をインクリメントしません。|atlcom.h|
|[CComObjectRoot](../../atl/reference/ccomobjectroot-class.md)|この[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)の typedef は、サーバーの既定のスレッドモデルでテンプレート化されています。|atlcom.h|
|[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)|このクラスは、非集計と集計されたオブジェクトの両方のオブジェクト参照カウント管理を処理するメソッドを提供します。|atlcom.h|
|[CComObjectStack](../../atl/reference/ccomobjectstack-class.md)|このクラスは、一時 COM オブジェクトを作成し、の`IUnknown`スケルトン実装を提供します。|atlcom.h|
|[CComPolyObject](../../atl/reference/ccompolyobject-class.md)|このクラスは`IUnknown` 、集計または非集計オブジェクトに対してを実装します。|atlcom.h|
|[CComPtr](../../atl/reference/ccomptr-class.md)|COM インターフェイスポインターを管理するためのスマートポインタークラス。|atlcomcli.h|
|[CComPtrBase](../../atl/reference/ccomptrbase-class.md)|このクラスは、COM ベースのメモリルーチンを使用するスマートポインタークラスの基礎となります。|atlcomcli.h|
|[CComQIPtr](../../atl/reference/ccomqiptr-class.md)|COM インターフェイスポインターを管理するためのスマートポインタークラス。|atlcomcli.h|
|[CComQIPtrElementTraits](../../atl/reference/ccomqiptrelementtraits-class.md)|このクラスには、COM インターフェイスポインターのコレクションを作成するときに役立つメソッド、静的関数、および typedef が用意されています。|atlcoll.h|
|[CComSafeArray](../../atl/reference/ccomsafearray-class.md)|このクラスは、 `SAFEARRAY Data Type`構造体のラッパーです。|atlsafe.h|
|[CComSafeArrayBound](../../atl/reference/ccomsafearraybound-class.md)|このクラスは、 `SAFEARRAYBOUND`構造体のラッパーです。|atlsafe.h|
|[CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md)|このクラスは、 [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md)クラスのスレッド選択を管理します。|atlbase. h|
|[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)|このクラスには、変数の値をインクリメントおよびデクリメントするためのメソッドが用意されています。|atlbase. h|
|[CComTearOffObject](../../atl/reference/ccomtearoffobject-class.md)|このクラスは、ティアオフインターフェイスを実装します。|atlcom.h|
|[CComUnkArray](../../atl/reference/ccomunkarray-class.md)|このクラスは`IUnknown` 、ポインターを格納し、 [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)テンプレートクラスのパラメーターとして使用するように設計されています。|atlcom.h|
|[CComVariant](../../atl/reference/ccomvariant-class.md)|このクラスは、格納されているデータの型を示すメンバーを提供して、バリアント型をラップします。|atlcomcli.h|
|[CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md)|このクラスは、別のオブジェクト内に含まれるウィンドウを実装します。|atlwin.h|
|[CCRTAllocator](../../atl/reference/ccrtallocator-class.md)|このクラスには、CRT メモリルーチンを使用してメモリを管理するためのメソッドが用意されています。|atlcore.h|
|[CCRTHeap](../../atl/reference/ccrtheap-class.md)|このクラスは、CRT ヒープ関数を使用して[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)を実装します。|atlmem.h|
|[CDacl](../../atl/reference/cdacl-class.md)|このクラスは、DACL (随意アクセス制御リスト) 構造のラッパーです。|atlsecurity.h|
|[CDebugReportHook クラス](../../atl/reference/cdebugreporthook-class.md)|このクラスを使用して、デバッグレポートを名前付きパイプに送信します。|atlutil.h|
|[CDefaultCharTraits](../../atl/reference/cdefaultchartraits-class.md)|このクラスは、文字を大文字に変換するための2つの静的関数を提供します。|atlcoll.h|
|[CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)|このクラスには、既定の要素比較関数が用意されています。|atlcoll.h|
|[CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)|このクラスは、コレクションクラスの既定のメソッドと関数を提供します。|atlcoll.h|
|[CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)|このクラスは、ハッシュ値を計算するための静的関数を提供します。|atlcoll.h|
|[CDialogImpl](../../atl/reference/cdialogimpl-class.md)|このクラスには、モーダルまたはモードレスのダイアログボックスを作成するためのメソッドが用意されています。|atlwin.h|
|[CDynamicChain](../../atl/reference/cdynamicchain-class.md)|このクラスは、メッセージマップの動的チェーンをサポートするメソッドを提供します。|atlwin.h|
|[CElementTraits](../../atl/reference/celementtraits-class.md)|このクラスは、移動、コピー、比較、およびハッシュ操作のためのメソッドと関数を提供するために、コレクションクラスによって使用されます。|atlcoll.h|
|[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)|このクラスは、コレクションクラスの既定のコピーおよび移動メソッドを提供します。|atlcoll.h|
|[CFirePropNotifyEvent](../../atl/reference/cfirepropnotifyevent-class.md)|このクラスは、コントロールプロパティの変更についてコンテナーのシンクに通知するためのメソッドを提供します。|atlctl.h|
|[CGlobalHeap](../../atl/reference/cglobalheap-class.md)|このクラスは、Win32 グローバルヒープ関数を使用して[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)を実装します。|atlmem.h|
|[CHandle](../../atl/reference/chandle-class.md)|このクラスには、handle オブジェクトを作成および使用するためのメソッドが用意されています。|atlbase. h|
|[CHeapPtr](../../atl/reference/cheapptr-class.md)|ヒープポインターを管理するためのスマートポインタークラス。|atlcore.h|
|[CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)|このクラスは、いくつかのスマートヒープポインタークラスの基礎を形成します。|atlcore.h|
|[CHeapPtrElementTraits クラス](../../atl/reference/cheapptrelementtraits-class.md)|このクラスは、ヒープポインターのコレクションを作成するときに便利なメソッド、静的関数、および typedef を提供します。|atlcoll.h|
|[CHeapPtrList](../../atl/reference/cheapptrlist-class.md)|このクラスには、ヒープポインターのリストを構築するときに役立つメソッドが用意されています。|atlcoll.h|
|[CImage](../../atl-mfc-shared/reference/cimage-class.md)|では、JPEG、GIF、BMP、およびポータブルネットワークグラフィックス (PNG) 形式のイメージを読み込んで保存する機能など、ビットマップのサポートが強化されています。|atlimage.h|
|[CInterfaceArray](../../atl/reference/cinterfacearray-class.md)|このクラスには、COM インターフェイスポインターの配列を構築するときに役立つメソッドが用意されています。|atlcoll.h|
|[CInterfaceList](../../atl/reference/cinterfacelist-class.md)|このクラスには、COM インターフェイスポインターのリストを構築するときに役立つメソッドが用意されています。|atlcoll.h|
|[CLocalHeap](../../atl/reference/clocalheap-class.md)|このクラスは、Win32 ローカルヒープ関数を使用して[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)を実装します。|atlmem.h|
|[CMessageMap](../../atl/reference/cmessagemap-class.md)|このクラスを使用すると、オブジェクトのメッセージマップに別のオブジェクトがアクセスできるようになります。|atlwin.h|
|[CNonStatelessWorker クラス](../../atl/reference/cnonstatelessworker-class.md)|は、スレッドプールから要求を受信し、各要求で作成および破棄されたワーカーオブジェクトにそれらを渡します。|atlutil.h|
|[CNoWorkerThread クラス](../../atl/reference/cnoworkerthread-class.md)|動的キャッシュメンテナンスを無効にする場合`MonitorClass`は、このクラスをテンプレートパラメーターキャッシュクラスの引数として使用します。|atlutil.h|
|[CPathT クラス](../../atl/reference/cpatht-class.md)|このクラスは、パスを表します。|atlpath.h|
|[CPrimitiveElementTraits](../../atl/reference/cprimitiveelementtraits-class.md)|このクラスは、プリミティブデータ型で構成されるコレクションクラスの既定のメソッドと関数を提供します。|atlcoll.h|
|[CPrivateObjectSecurityDesc](../../atl/reference/cprivateobjectsecuritydesc-class.md)|このクラスは、プライベートオブジェクトのセキュリティ記述子オブジェクトを表します。|atlsecurity.h|
|[CRBMap](../../atl/reference/crbmap-class.md)|このクラスは、レッドブラックのバイナリツリーを使用して、マッピング構造を表します。|atlcoll.h|
|[CRBMultiMap](../../atl/reference/crbmultimap-class.md)|このクラスは、赤黒のバイナリツリーを使用して、各キーが複数の値に関連付けられるようにするマッピング構造を表します。|atlcoll.h|
|[CRBTree](../../atl/reference/crbtree-class.md)|このクラスは、赤の黒のツリーを作成および利用するためのメソッドを提供します。|atlcoll.h|
|[CRegKey](../../atl/reference/cregkey-class.md)|このクラスには、システムレジストリのエントリを操作するためのメソッドが用意されています。|atlbase. h|
|[CRTThreadTraits](../../atl/reference/crtthreadtraits-class.md)|このクラスは、CRT スレッドの作成関数を提供します。 スレッドが CRT 関数を使用する場合は、このクラスを使用します。|atlbase. h|
|[CSacl](../../atl/reference/csacl-class.md)|このクラスは、SACL (システムアクセス制御リスト) 構造体のラッパーです。|atlsecurity.h|
|[CSecurityAttributes](../../atl/reference/csecurityattributes-class.md)|このクラスは、 `SECURITY_ATTRIBUTES`構造体のシンラッパーです。|atlsecurity.h|
|[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)|このクラスは、 `SECURITY_DESCRIPTOR`構造体のラッパーです。|atlsecurity.h|
|[CSid](../../atl/reference/csid-class.md)|このクラスは、 `SID` (セキュリティ識別子) 構造体のラッパーです。|atlsecurity.h|
|[CSimpleArray](../../atl/reference/csimplearray-class.md)|このクラスには、単純な配列を管理するためのメソッドが用意されています。|atlsimpcoll.h|
|[CSimpleArrayEqualHelper](../../atl/reference/csimplearrayequalhelper-class.md)|このクラスは、 [CSimpleArray](../../atl/reference/csimplearray-class.md)クラスのヘルパーです。|atlsimpcoll.h|
|[CSimpleArrayEqualHelperFalse](../../atl/reference/csimplearrayequalhelperfalse-class.md)|このクラスは、 [CSimpleArray](../../atl/reference/csimplearray-class.md)クラスのヘルパーです。|atlsimpcoll.h|
|[CSimpleDialog](../../atl/reference/csimpledialog-class.md)|このクラスは、基本的なモーダルダイアログボックスを実装します。|atlwin.h|
|[CSimpleMap](../../atl/reference/csimplemap-class.md)|このクラスは、単純なマッピング配列をサポートします。|atlsimpcoll.h|
|[CSimpleMapEqualHelper](../../atl/reference/csimplemapequalhelper-class.md)|このクラスは、 [CSimpleMap](../../atl/reference/csimplemap-class.md)クラスのヘルパーです。|atlsimpcoll.h|
|[CSimpleMapEqualHelperFalse](../../atl/reference/csimplemapequalhelperfalse-class.md)|このクラスは、 [CSimpleMap](../../atl/reference/csimplemap-class.md)クラスのヘルパーです。|atlsimpcoll.h|
|[CSnapInItemImpl](../../atl/reference/csnapinitemimpl-class.md)|このクラスには、スナップインノードオブジェクトを実装するためのメソッドが用意されています。|atlsnap.h|
|[CSnapInPropertyPageImpl](../../atl/reference/csnapinpropertypageimpl-class.md)|このクラスには、スナップインプロパティページオブジェクトを実装するためのメソッドが用意されています。|atlsnap.h|
|[CStockPropImpl](../../atl/reference/cstockpropimpl-class.md)|このクラスには、ストックプロパティ値をサポートするためのメソッドが用意されています。|atlctl.h|
|[CStringElementTraits](../../atl/reference/cstringelementtraits-class.md)|このクラスは、オブジェクトを格納`CString`するコレクションクラスによって使用される静的関数を提供します。|cstringt.h|
|[CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md)|このクラスは、コレクションクラスオブジェクトに格納されている文字列に関連する静的関数を提供します。 これは[Cstringelementtraits](../../atl/reference/cstringelementtraits-class.md)に似ていますが、大文字と小文字を区別しない比較を実行します。|atlcoll.h|
|[CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md)|このクラスは、コレクションクラスオブジェクトに格納されている文字列に関連する静的関数を提供します。 文字列オブジェクトは参照として処理されます。|atlcoll.h|
|[CThreadPool クラス](../../atl/reference/cthreadpool-class.md)|このクラスは、作業項目のキューを処理するワーカースレッドのプールを提供します。|atlutil.h|
|[CTokenGroups](../../atl/reference/ctokengroups-class.md)|このクラスは、 `TOKEN_GROUPS`構造体のラッパーです。|atlsecurity.h|
|[CTokenPrivileges](../../atl/reference/ctokenprivileges-class.md)|このクラスは、 `TOKEN_PRIVILEGES`構造体のラッパーです。|atlsecurity.h|
|[CUrl クラス](../../atl/reference/curl-class.md)|このクラスは、URL を表します。 これにより、既存の URL 文字列を解析するか、文字列をゼロから構築するかどうかに関係なく、URL の各要素を他のユーザーとは独立して操作できます。|atlutil.h|
|[CW2AEX](../../atl/reference/cw2aex-class.md)|このクラスは、文字列変換マクロ CT2AEX、CW2TEX、CW2CTEX、CT2CAEX、および typedef CW2A によって使用されます。|atlconv.h|
|[CW2CWEX](../../atl/reference/cw2cwex-class.md)|このクラスは、文字列変換マクロ CW2CTEX と CT2CWEX、および typedef CW2CW によって使用されます。|atlconv.h|
|[CW2WEX](../../atl/reference/cw2wex-class.md)|このクラスは、文字列変換マクロ CW2TEX と CT2WEX、および typedef CW2W によって使用されます。|atlconv.h|
|[CWin32Heap](../../atl/reference/cwin32heap-class.md)|このクラスは、Win32 ヒープ割り当て関数を使用して[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)を実装します。|atlmem.h|
|[CWindow](../../atl/reference/cwindow-class.md)|このクラスには、ウィンドウを操作するためのメソッドが用意されています。|atlwin.h|
|[CWindowImpl](../../atl/reference/cwindowimpl-class.md)|このクラスには、ウィンドウを作成またはサブクラス化するためのメソッドが用意されています。|atlwin.h|
|[CWinTraits](../../atl/reference/cwintraits-class.md)|このクラスは、ウィンドウオブジェクトの作成時に使用されるスタイルを標準化するためのメソッドを提供します。|atlwin.h|
|[CWinTraitsOR](../../atl/reference/cwintraitsor-class.md)|このクラスは、ウィンドウオブジェクトの作成時に使用されるスタイルを標準化するためのメソッドを提供します。|atlwin.h|
|[CWndClassInfo](../../atl/reference/cwndclassinfo-class.md)|このクラスには、ウィンドウクラスの情報を登録するためのメソッドが用意されています。|atlwin.h|
|[CWorkerThread クラス](../../atl/reference/cworkerthread-class.md)|このクラスは、ワーカースレッドを作成するか、既存のスレッドを使用して1つ以上のカーネルオブジェクトハンドルで待機し、いずれかのハンドルがシグナル状態になったときに、指定されたクライアント関数を実行します。|atlutil.h|
|[IAtlAutoThreadModule](../../atl/reference/iatlautothreadmodule-class.md)|このクラスは、 `CreateInstance`メソッドへのインターフェイスを表します。|atlbase. h|
|[IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)|このクラスは、メモリマネージャーへのインターフェイスを表します。|atlmem.h|
|[IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md)|このインターフェイスは、ホストされるコントロールまたはコンテナーの特性を指定するためのメソッドを提供します。|atlbase .h、ATLIFace|
|[IAxWinAmbientDispatchEx](../../atl/reference/iaxwinambientdispatchex-interface.md)|このインターフェイスは、ホストされるコントロールの追加のアンビエントプロパティを実装します。|atlbase .h、ATLIFace|
|[IAxWinHostWindow](../../atl/reference/iaxwinhostwindow-interface.md)|このインターフェイスには、コントロールとそのホストオブジェクトを操作するためのメソッドが用意されています。|atlbase .h、ATLIFace|
|[IAxWinHostWindowLic](../../atl/reference/iaxwinhostwindowlic-interface.md)|このインターフェイスは、ライセンスされたコントロールとそのホストオブジェクトを操作するためのメソッドを提供します。|atlbase .h、ATLIFace|
|[ICollectionOnSTLImpl](../../atl/reference/icollectiononstlimpl-class.md)|このクラスは、コレクションクラスによって使用されるメソッドを提供します。|atlcom.h|
|[IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md)|このクラスは、 [IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)オブジェクトのコレクションを管理するための接続ポイントコンテナーを実装します。|atlcom.h|
|[IConnectionPointImpl](../../atl/reference/iconnectionpointimpl-class.md)|このクラスは、コネクションポイントを実装します。|atlcom.h|
|[IDataObjectImpl](../../atl/reference/idataobjectimpl-class.md)|このクラスには、Uniform Data Transfer をサポートし、接続を管理するためのメソッドが用意されています。|atlctl.h|
|[IDispatchImpl](../../atl/reference/idispatchimpl-class.md)|このクラスは、デュアルインターフェイスの`IDispatch`一部の既定の実装を提供します。|atlcom.h|
|[IDispEventImpl](../../atl/reference/idispeventimpl-class.md)|このクラスは、 `IDispatch`メソッドの実装を提供します。|atlcom.h|
|[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)|このクラスは、タイプライブラリ`IDispatch`から型情報を取得せずに、メソッドの実装を提供します。|atlcom.h|
|[IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md)|Microsoft HTML 解析およびレンダリングエンジンへのインターフェイスです。|atlbase .h、ATLIFace|
|[IEnumOnSTLImpl](../../atl/reference/ienumonstlimpl-class.md)|このクラスは、 C++標準ライブラリコレクションに基づいて列挙子インターフェイスを定義します。|atlcom.h|
|[IObjectSafetyImpl](../../atl/reference/iobjectsafetyimpl-class.md)|このクラスは、 `IObjectSafety`クライアントがオブジェクトの安全性レベルを取得および設定できるようにするインターフェイスの既定の実装を提供します。|atlctl.h|
|[IObjectWithSiteImpl](../../atl/reference/iobjectwithsiteimpl-class.md)|このクラスは、オブジェクトがそのサイトと通信できるようにするメソッドを提供します。|atlcom.h|
|[IOleControlImpl](../../atl/reference/iolecontrolimpl-class.md)|このクラスは、 `IOleControl`インターフェイスの既定の実装を提供し、を実装`IUnknown`します。|atlctl.h|
|[IOleInPlaceActiveObjectImpl](../../atl/reference/ioleinplaceactiveobjectimpl-class.md)|このクラスは、インプレースコントロールとそのコンテナーとの間の通信を支援するためのメソッドを提供します。|atlctl.h|
|[IOleInPlaceObjectWindowlessImpl](../../atl/reference/ioleinplaceobjectwindowlessimpl-class.md)|このクラスは`IUnknown`を実装し、ウィンドウなしのコントロールがウィンドウメッセージを受信し、ドラッグアンドドロップ操作に参加できるようにするメソッドを提供します。|atlctl.h|
|[IOleObjectImpl](../../atl/reference/ioleobjectimpl-class.md)|このクラスは`IUnknown`を実装し、はコンテナーがコントロールと通信するときに使用するプリンシパルインターフェイスです。|atlctl.h|
|[IPerPropertyBrowsingImpl](../../atl/reference/iperpropertybrowsingimpl-class.md)|このクラスは`IUnknown`を実装し、クライアントがオブジェクトのプロパティページ内の情報にアクセスできるようにします。|atlctl.h|
|[IPersistPropertyBagImpl](../../atl/reference/ipersistpropertybagimpl-class.md)|このクラスは`IUnknown`を実装し、オブジェクトがそのプロパティをクライアントが提供するプロパティバッグに保存できるようにします。|atlcom.h|
|[IPersistStorageImpl](../../atl/reference/ipersiststorageimpl-class.md)|このクラスは、 [IPersistStorage](/windows/win32/api/objidl/nn-objidl-ipersiststorage)インターフェイスを実装します。|atlcom.h|
|[IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md)|このクラスは`IUnknown`を実装し、 [IPersistStreamInit](/windows/win32/api/ocidl/nn-ocidl-ipersiststreaminit)インターフェイスの既定の実装を提供します。|atlcom.h|
|[IPointerInactiveImpl](../../atl/reference/ipointerinactiveimpl-class.md)|このクラスは`IUnknown` 、および[iポインター非アクティブ](/windows/win32/api/ocidl/nn-ocidl-ipointerinactive)インターフェイスメソッドを実装します。|atlctl.h|
|[IPropertyNotifySinkCP](../../atl/reference/ipropertynotifysinkcp-class.md)|このクラスは、接続可能なオブジェクトの送信インターフェイスとして[IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink)インターフェイスを公開します。|atlctl.h|
|[IPropertyPage2Impl](../../atl/reference/ipropertypage2impl-class.md)|このクラスは`IUnknown`を実装し、 [IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)の既定の実装を継承します。|atlctl.h|
|[IPropertyPageImpl](../../atl/reference/ipropertypageimpl-class.md)|このクラスは`IUnknown`を実装し、 [IPropertyPage](/windows/win32/api/ocidl/nn-ocidl-ipropertypage)インターフェイスの既定の実装を提供します。|atlctl.h|
|[IProvideClassInfo2Impl](../../atl/reference/iprovideclassinfo2impl-class.md)|このクラスは、 [IProvideClassInfo](/windows/win32/api/ocidl/nn-ocidl-iprovideclassinfo)メソッドと[は iprovideclassinfo2](/windows/win32/api/ocidl/nn-ocidl-iprovideclassinfo2)メソッドの既定の実装を提供します。|atlcom.h|
|[IQuickActivateImpl](../../atl/reference/iquickactivateimpl-class.md)|このクラスは、コンテナーのコントロールの初期化を1回の呼び出しに結合します。|atlctl.h|
|[IRunnableObjectImpl](../../atl/reference/irunnableobjectimpl-class.md)|このクラスは`IUnknown`を実装し、 [IRunnableObject](/windows/win32/api/objidl/nn-objidl-irunnableobject)インターフェイスの既定の実装を提供します。|atlctl.h|
|[IServiceProviderImpl](../../atl/reference/iserviceproviderimpl-class.md)|このクラスは、 `IServiceProvider`インターフェイスの既定の実装を提供します。|atlcom.h|
|[ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md)|このクラスは`IUnknown`を実装し、 [ISpecifyPropertyPages](/windows/win32/api/ocidl/nn-ocidl-ispecifypropertypages)インターフェイスの既定の実装を提供します。|atlcom.h|
|[ISupportErrorInfoImpl](../../atl/reference/isupporterrorinfoimpl-class.md)|このクラスは、 `ISupportErrorInfo Interface`インターフェイスの既定の実装を提供し、1つのインターフェイスだけがオブジェクトに対してエラーを生成する場合に使用できます。|atlcom.h|
|[IThreadPoolConfig インターフェイス](../../atl/reference/ithreadpoolconfig-interface.md)|このインターフェイスには、スレッドプールを構成するためのメソッドが用意されています。|atlutil.h|
|[IViewObjectExImpl](../../atl/reference/iviewobjecteximpl-class.md)|このクラスは`IUnknown`を実装し、 [iviewobject](/windows/win32/api/oleidl/nn-oleidl-iviewobject)、 [IViewObject2](/windows/win32/api/oleidl/nn-oleidl-iviewobject2)、および[IViewObjectEx](/windows/win32/api/ocidl/nn-ocidl-iviewobjectex)インターフェイスの既定の実装を提供します。|atlctl.h|
|[IWorkerThreadClient インターフェイス](../../atl/reference/iworkerthreadclient-interface.md)|`IWorkerThreadClient`は、 [CWorkerThread](../../atl/reference/cworkerthread-class.md)クラスのクライアントによって実装されるインターフェイスです。|atlutil.h|
|[_U_MENUorID](../../atl/reference/u-menuorid-class.md)|このクラスは、および`CreateWindow` `CreateWindowEx`のラッパーを提供します。|atlwin.h|
|[_U_RECT](../../atl/reference/u-rect-class.md)|この引数アダプタークラスを使用`RECT`すると、ポインターまたは参照を、ポインターの観点から実装された関数に渡すことができます。|atlwin.h|
|[_U_STRINGorID](../../atl/reference/u-stringorid-class.md)|この引数アダプタークラスを使用すると、リソース名 (LPCTSTRs) またはリソース Id (UINTs) を関数に渡すことができます。呼び出し元は、MAKEINTRESOURCE マクロを使用して、ID を文字列に変換する必要はありません。|atlwin.h|
|[Win32ThreadTraits](../../atl/reference/win32threadtraits-class.md)|このクラスは、Windows スレッドの作成関数を提供します。 スレッドが CRT 関数を使用しない場合は、このクラスを使用します。|atlbase. h|

## <a name="see-also"></a>関連項目

[ATL COM デスクトップ コンポーネント](../../atl/atl-com-desktop-components.md)<br/>
[関数](../../atl/reference/atl-functions.md)<br/>
[グローバル変数](../../atl/reference/atl-global-variables.md)<br/>
[Typedefs](../../atl/reference/atl-typedefs.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
