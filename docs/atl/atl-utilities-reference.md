---
title: ATL ユーティリティのリファレンス
ms.date: 11/04/2016
ms.assetid: dd8a2888-34f4-461e-9bf4-834218f9b95b
ms.openlocfilehash: 6c1481929f832e6f810ce46773f328f278b503fa
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491703"
---
# <a name="atl-utilities-reference"></a>ATL ユーティリティのリファレンス

ATL には、 [Cpatht](../atl/reference/cpatht-class.md)および[CUrl](../atl/reference/curl-class.md)の形式でパスと url を操作するためのコードが用意されています。 スレッドプール[CThreadPool](../atl/reference/cthreadpool-class.md)は、アプリケーションで使用できます。 このコードは、atlpath.h および atlutil.h に含まれます。

### <a name="classes"></a>クラス

|||
|-|-|
|[CPathT クラス](../atl/reference/cpatht-class.md)|このクラスは、パスを表します。|
|[CDebugReportHook クラス](../atl/reference/cdebugreporthook-class.md)|このクラスを使用して、デバッグレポートを名前付きパイプに送信します。|
|[CNonStatelessWorker クラス](../atl/reference/cnonstatelessworker-class.md)|は、スレッドプールから要求を受信し、各要求で作成および破棄されたワーカーオブジェクトにそれらを渡します。|
|[CNoWorkerThread クラス](../atl/reference/cnoworkerthread-class.md)|動的キャッシュのメンテナンスを無効にする`MonitorClass`場合は、このクラスをテンプレートパラメーターの引数としてキャッシュクラスに使用します。|
|[CThreadPool クラス](../atl/reference/cthreadpool-class.md)|このクラスは、作業項目のキューを処理するワーカースレッドのプールを提供します。|
|[CUrl クラス](../atl/reference/curl-class.md)|このクラスは、URL を表します。 これにより、既存の URL 文字列を解析するか、文字列をゼロから構築するかどうかに関係なく、URL の各要素を他のユーザーとは独立して操作できます。|
|[CWorkerThread クラス](../atl/reference/cworkerthread-class.md)|このクラスは、ワーカースレッドを作成するか、既存のスレッドを使用して1つ以上のカーネルオブジェクトハンドルで待機し、いずれかのハンドルがシグナル状態になったときに、指定されたクライアント関数を実行します。|

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[CPath](../atl/reference/atl-typedefs.md#cpath)|を使用`CString`した[cpatht](../atl/reference/cpatht-class.md)の特殊化。|
|[CPathA](../atl/reference/atl-typedefs.md#cpatha)|を使用`CStringA`した[cpatht](../atl/reference/cpatht-class.md)の特殊化。|
|[CPathW](../atl/reference/atl-typedefs.md#cpathw)|を使用`CStringW`した[cpatht](../atl/reference/cpatht-class.md)の特殊化。|
|[ATL_URL_PORT](../atl/reference/atl-typedefs.md#atl_url_port)|ポート番号を指定するために[CUrl](../atl/reference/curl-class.md)によって使用される型。|

### <a name="enums"></a>列挙体

|||
|-|-|
|[ATL_URL_SCHEME](../atl/reference/atl-url-scheme-enum.md)|この列挙体のメンバーは、 [CUrl](../atl/reference/curl-class.md)によって認識されるスキームの定数を提供します。|

### <a name="functions"></a>関数

|||
|-|-|
|[AtlCanonicalizeUrl](../atl/reference/atl-http-utility-functions.md#atlcanonicalizeurl)|URL を標準形式に変換します。安全でない文字や空白をエスケープ シーケンスに変換する処理などが含まれます。|
|[AtlCombineUrl](../atl/reference/atl-http-utility-functions.md#atlcombineurl)|ベース URL と相対 URL を結合して、1 つの標準形式の URL にします。|
|[AtlEscapeUrl](../atl/reference/atl-http-utility-functions.md#atlescapeurl)|すべての安全でない文字をエスケープ シーケンスに変換します。|
|[AtlGetDefaultUrlPort](../atl/reference/atl-http-utility-functions.md#atlgetdefaulturlport)|この関数を呼び出して、特定のインターネットプロトコルまたはスキームに関連付けられている既定のポート番号を取得します。|
|[AtlHexValue](../atl/reference/atl-text-encoding-functions.md#atlhexvalue)|16 進数の数値を取得します。|
|[AtlIsUnsafeUrlChar](../atl/reference/atl-http-utility-functions.md#atlisunsafeurlchar)|URL で使用しても安全な文字かどうかを判断します。|
|[AtlUnescapeUrl](../atl/reference/atl-http-utility-functions.md#atlunescapeurl)|エスケープされた文字を元の値に変換します。|
|[SystemTimeToHttpDate](../atl/reference/atl-http-utility-functions.md#systemtimetohttpdate)|システム時刻を HTTP ヘッダーで使用できる形式の文字列に変換します。|

|[ATLPath::AddBackslash](../atl/reference/atl-path-functions.md#addbackslash)|この関数はオーバー ロードされたラッパー [PathAddBackslash](/windows/desktop/api/shlwapi/nf-shlwapi-pathaddbackslasha
). | |[ATLPath::AddExtension](../atl/reference/atl-path-functions.md#addextension)|この関数はオーバー ロードされたラッパー [PathAddExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathaddextensionw). | |[ATLPath::Append](../atl/reference/atl-path-functions.md#append)|この関数はオーバー ロードされたラッパー [PathAppend](/windows/win32/api/shlwapi/nf-shlwapi-pathappendw). | |[ATLPath::BuildRoot](../atl/reference/atl-path-functions.md#buildroot)|この関数はオーバー ロードされたラッパー [PathBuildRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathbuildrootw). | |[ATLPath::Canonicalize](../atl/reference/atl-path-functions.md#canonicalize)|この関数はオーバー ロードされたラッパー [PathCanonicalize](/windows/win32/api/shlwapi/nf-shlwapi-pathcanonicalizew). | |[ATLPath::Combine](../atl/reference/atl-path-functions.md#combine)|この関数はオーバー ロードされたラッパー [PathCombine](/windows/win32/api/shlwapi/nf-shlwapi-pathcombinew). | |[ATLPath::CommonPrefix](../atl/reference/atl-path-functions.md#commonprefix)|この関数はオーバー ロードされたラッパー [PathCommonPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathcommonprefixw). | |[ATLPath::CompactPath](../atl/reference/atl-path-functions.md#compactpath)|この関数はオーバー ロードされたラッパー [PathCompactPath](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathw). | |[ATLPath::CompactPathEx](../atl/reference/atl-path-functions.md#compactpathex)|この関数はオーバー ロードされたラッパー [PathCompactPathEx](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathexw). | |[ATLPath::FileExists](../atl/reference/atl-path-functions.md#fileexists)|この関数はオーバー ロードされたラッパー [PathFileExists](/windows/win32/api/shlwapi/nf-shlwapi-pathfileexistsw). | |[ATLPath::FindExtension](../atl/reference/atl-path-functions.md#findextension)|この関数はオーバー ロードされたラッパー [PathFindExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathfindextensionw). | |[ATLPath::FindFileName](../atl/reference/atl-path-functions.md#findfilename)|この関数はオーバー ロードされたラッパー [PathFindFileName](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew). | |[ATLPath::GetDriveNumber](../atl/reference/atl-path-functions.md#getdrivenumber)|この関数はオーバー ロードされたラッパー [PathGetDriveNumber](/windows/win32/api/shlwapi/nf-shlwapi-pathgetdrivenumberw). | |[ATLPath::IsDirectory](../atl/reference/atl-path-functions.md#isdirectory)|この関数はオーバー ロードされたラッパー [PathIsDirectory](/windows/win32/api/shlwapi/nf-shlwapi-pathisdirectoryw). | |[ATLPath::IsFileSpec](../atl/reference/atl-path-functions.md#isfilespec)|この関数はオーバー ロードされたラッパー [PathIsFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathisfilespecw). | |[ATLPath::IsPrefix](../atl/reference/atl-path-functions.md#isprefix)|この関数はオーバー ロードされたラッパー [PathIsPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathisprefixw). | |[ATLPath::IsRelative](../atl/reference/atl-path-functions.md#isrelative)|この関数はオーバー ロードされたラッパー [PathIsRelative](/windows/win32/api/shlwapi/nf-shlwapi-pathisrelativew). | |[ATLPath::IsRoot](../atl/reference/atl-path-functions.md#isroot)|この関数はオーバー ロードされたラッパー [PathIsRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathisrootw). | |[ATLPath::IsSameRoot](../atl/reference/atl-path-functions.md#issameroot)|この関数はオーバー ロードされたラッパー [PathIsSameRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathissamerootw). | |[ATLPath::IsUNC](../atl/reference/atl-path-functions.md#isunc)|この関数はオーバー ロードされたラッパー [PathIsUNC](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncw). | |[ATLPath::IsUNCServer](../atl/reference/atl-path-functions.md#isuncserver)|この関数はオーバー ロードされたラッパー [PathIsUNCServer](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserverw). | |[ATLPath::IsUNCServerShare](../atl/reference/atl-path-functions.md#isuncservershare)|この関数はオーバー ロードされたラッパー [PathIsUNCServerShare](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserversharew).| |[ATLPath::MakePretty](../atl/reference/atl-path-functions.md#makepretty)|This function is an overloaded wrapper for [PathMakePretty](/windows/win32/api/shlwapi/nf-shlwapi-pathmakeprettyw).| |[ATLPath::MatchSpec](../atl/reference/atl-path-functions.md#matchspec)|This function is an overloaded wrapper for [PathMatchSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathmatchspecw).| |[ATLPath::QuoteSpaces](../atl/reference/atl-path-functions.md#quotespaces)|This function is an overloaded wrapper for [PathQuoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathquotespacesw).| |[ATLPath::RelativePathTo](../atl/reference/atl-path-functions.md#relativepathto)|This function is an overloaded wrapper for [PathRelativePathTo](/windows/win32/api/shlwapi/nf-shlwapi-pathrelativepathtow).| |[ATLPath::RemoveArgs](../atl/reference/atl-path-functions.md#removeargs)|This function is an overloaded wrapper for [PathRemoveArgs](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveargsw).| |[ATLPath::RemoveBackslash](../atl/reference/atl-path-functions.md#removebackslash)|This function is an overloaded wrapper for [PathRemoveBackslash](/windows/win32/api/shlwapi/nf-shlwapi-pathremovebackslashw).| |[ATLPath::RemoveBlanks](../atl/reference/atl-path-functions.md#removeblanks)|This function is an overloaded wrapper for [PathRemoveBlanks](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveblanksw).| |[ATLPath::RemoveExtension](../atl/reference/atl-path-functions.md#removeextension)|This function is an overloaded wrapper for [PathRemoveExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveextensionw).| |[ATLPath::RemoveFileSpec](../atl/reference/atl-path-functions.md#removefilespec)|This function is an overloaded wrapper for [PathRemoveFileSpec](/windows/win32/api/shlwapi/nf-shlwapi-pathremovefilespecw).| |[ATLPath::RenameExtension](../atl/reference/atl-path-functions.md#renameextension)|This function is an overloaded wrapper for [PathRenameExtension](/windows/win32/api/shlwapi/nf-shlwapi-pathrenameextensionw).| |[ATLPath::SkipRoot](../atl/reference/atl-path-functions.md#skiproot)|This function is an overloaded wrapper for [PathSkipRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathskiprootw).| |[ATLPath::StripPath](../atl/reference/atl-path-functions.md#strippath)|This function is an overloaded wrapper for [PathStripPath](/windows/win32/api/shlwapi/nf-shlwapi-pathstrippathw).| |[ATLPath::StripToRoot](../atl/reference/atl-path-functions.md#striptoroot)|This function is an overloaded wrapper for [PathStripToRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathstriptorootw).| |[ATLPath::UnquoteSpaces](../atl/reference/atl-path-functions.md#unquotespaces)|This function is an overloaded wrapper for [PathUnquoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathunquotespacesw).|

## <a name="see-also"></a>関連項目

[概念](../atl/active-template-library-atl-concepts.md)<br/>
[ATL COM デスクトップ コンポーネント](../atl/atl-com-desktop-components.md)
