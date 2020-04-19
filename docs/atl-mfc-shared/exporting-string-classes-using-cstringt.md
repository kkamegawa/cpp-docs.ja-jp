---
title: CStringT による文字列クラスをエクスポートします。
ms.date: 11/04/2016
helpviewer_keywords:
- CStringT class, exporting strings
ms.assetid: bdfc441e-8d2a-461c-9885-46178066c09f
ms.openlocfilehash: a4ee73d2ae5cfb7bf9834fb23eed8470b7d29445
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62252741"
---
# <a name="exporting-string-classes-using-cstringt"></a>CStringT による文字列クラスをエクスポートします。

派生した MFC 開発者まで、`CString`独自の文字列クラスを専門とします。 Microsoft Visual C .net (MFC 8.0)、 [CString](../atl-mfc-shared/using-cstring.md)クラスは、という名前のテンプレート クラスによって置き換えられました[CStringT](../atl-mfc-shared/reference/cstringt-class.md)します。 これには、いくつかの利点が用意されています。

- MFC が許可されている`CString`ATL で使用されるクラスは、大規模な MFC のスタティック ライブラリまたは DLL にリンクせずプロジェクトします。

- 新しい`CStringT`カスタマイズするテンプレート クラスは、 `CString` C++ 標準ライブラリでテンプレートのような文字特性を指定するテンプレート パラメーターを使用して動作します。

- DLL を使用してから、独自の文字列クラスをエクスポートする`CStringT`、コンパイラが自動的にエクスポート、`CString`基本クラス。 `CString`テンプレート クラス自体は、コンパイラが認識しない限りには、使用すると、コンパイラでインスタンス化を`CString`DLL からインポートされます。 リンカーは乗算定義のエラーのシンボルが発生したことがあります Visual C 6.0 から Visual C .NET にプロジェクトを移行した場合`CString`の競合により、 `CString` DLL と、ローカルでインスタンス化されたバージョンからインポートします。 これを行う適切な方法を以下に示します。

次のシナリオには、重複して定義されたクラスのシンボル エラーを生成するために、リンカーが発生します。 エクスポートすることを前提としています、 `CString`-派生クラス (`CMyString`) MFC 拡張 DLL から。

[!code-cpp[NVC_MFC_DLL#6](../atl-mfc-shared/codesnippet/cpp/exporting-string-classes-using-cstringt_1.cpp)]

コンシューマー コードの組み合わせを使用して`CString`と`CMyString`します。 プリコンパイル済みヘッダー、およびいくつかの使用状況の"MyString.h"が含まれていない`CString`が`CMyString`表示します。

使用することを前提としています、`CString`と`CMyString`Source1.cpp および Source2.cpp、別のソース ファイル内のクラス。 Source1.cpp でを使用して`CMyString`と #include MyString.h します。 Source2.cpp でを使用して`CString`、そうでない #include MyString.h します。 この場合、リンカーは不満の`CStringT`複数回定義されています。 これが原因で`CString`をエクスポートする DLL からインポートした両方のされる`CMyString`、を通じてコンパイラによってローカルでインスタンス化し、`CStringT`テンプレート。

この問題を解決するには、次の操作を行います。

エクスポート`CStringA`と`CStringW`(および必要な基本クラス) MFC90 から。DLL です。 MFC を含むプロジェクトが MFC DLL エクスポートを使用して常に`CStringA`と`CStringW`以前の MFC 実装のようにします。

使用して、エクスポート可能な派生クラスを作成し、`CStringT`テンプレートとして`CStringT_Exported`たとえば以下に示します。

[!code-cpp[NVC_MFC_DLL#7](../atl-mfc-shared/codesnippet/cpp/exporting-string-classes-using-cstringt_2.cpp)]

AfxStr.h で置き換える前`CString`、 `CStringA`、および`CStringW`typedef として次のとおりです。

[!code-cpp[NVC_MFC_DLL#8](../atl-mfc-shared/codesnippet/cpp/exporting-string-classes-using-cstringt_3.cpp)]

これにはいくつかの注意事項があります。

- エクスポートする必要がありますいない`CStringT`自体をエクスポートする特殊な ATL 専用のプロジェクトが生じるため`CStringT`クラス。

- クラスから派生した、エクスポートを使用して`CStringT`再実装することを最小限に抑えます`CStringT`機能します。 追加のコードをコンス トラクターの転送に限定されます、`CStringT`基本クラス。

- `CString`、 `CStringA`、および`CStringW`のみマークされている必要があります`__declspec(dllexport/dllimport)`DLL を共有するときに、MFC で構築しています。 エクスポートこれらのクラスをマークする場合は、MFC のスタティック ライブラリとリンク、いない必要があります。それ以外の場合、内部使用`CString`、`CStringA`と`CStringW`ユーザー Dll をマークする内部`CString`もエクスポートします。

## <a name="related-topics"></a>関連トピック

[CStringT クラス](../atl-mfc-shared/reference/cstringt-class.md)

## <a name="see-also"></a>関連項目

[CStringT の使用](../atl-mfc-shared/using-cstringt.md)<br/>
[CString の使用](../atl-mfc-shared/using-cstring.md)
