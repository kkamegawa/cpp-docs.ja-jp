---
title: 文字列データ管理
ms.date: 11/04/2016
helpviewer_keywords:
- Unicode, string objects
ms.assetid: 0b53a542-eeb1-4108-9ada-6700645b6f8f
ms.openlocfilehash: b247e97f5aa6b5e85a6a6b6f57a64224a9e0f435
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62252663"
---
# <a name="string-data-management"></a>文字列データ管理

Visual C には、文字列データを管理するためにいくつかの方法が用意されています。

- [文字列操作](../c-runtime-library/string-manipulation-crt.md)C スタイルの null で終わる文字列を操作するため

- 文字列を管理するための Win32 API 関数

- Mfc の[CStringT クラス](../atl-mfc-shared/reference/cstringt-class.md)、柔軟でサイズ変更可能な文字列オブジェクトを提供します。

- クラス[CStringT クラス](../atl-mfc-shared/reference/cstringt-class.md)MFC に依存しない文字列オブジェクトと同じ機能を提供 `CString`

ほぼすべてのプログラムは、文字列データを操作します。 MFC の`CString`クラスは、柔軟な文字列処理の最適なソリューションでは多くの場合。 バージョン 7.0 以降`CString`MFC または MFC に依存しないプログラムで使用できます。 ランタイム ライブラリと`CString`Unicode や MBCS のプログラミングのように、マルチバイト (ワイド) 文字を含む文字列をサポートします。

この記事では、クラス ライブラリでは、文字列の操作に関連するが提供する汎用的なサービスについて説明します。 この記事で説明したトピックは次のとおりです。

- [Unicode と MBCS 提供の移植性](#_core_unicode_and_mbcs_provide_portability)

- [Cstring、const char ポインター](#_core_cstrings_and_const_char_pointers)

- [CString の参照カウント](#_core_cstring_reference_counting)

[CStringT クラス](../atl-mfc-shared/reference/cstringt-class.md)クラスは、文字列の操作のサポートを提供します。 置き換えるし、通常、C ランタイム ライブラリ文字列パッケージによって提供される機能を拡張するものです。 `CString`クラスは、メンバー関数と演算子では、Basic と同様、簡略化された文字列処理を提供します。 クラスはコンス トラクターと演算子も提供すると作成、割り当て、および比較の`CString`s と標準 C++ 文字列データ型。 `CString`から派生していない`CObject`、使用することができます`CString`ほとんどの Microsoft Foundation Class ライブラリ (MFC) とは無関係にオブジェクト。

`CString` オブジェクトは、「セマンティクス値です」に従う A`CString`オブジェクトは、一意の値を表します。 考える、`CString`文字列へのポインターとしてではなく、実際の文字列として。

A`CString`オブジェクトは、変数の数の文字のシーケンスを表します。 `CString` オブジェクトは、文字の配列として考えることができます。

##  <a name="_core_unicode_and_mbcs_provide_portability"></a> Unicode と MBCS の移植性を提供します。

MFC バージョン 3.0 以降、MFC などで`CString`Unicode とマルチバイト文字セット (MBCS) の両方に対して有効にします。 このサポートでは、Unicode または ANSI のいずれかの文字をビルドできるポータブル アプリケーションを記述するためのやすくなります。 この移植性を内の各文字を有効にする、`CString`オブジェクトが型として定義されている、TCHAR `wchar_t` 、アプリケーションをビルドするときに、シンボル _UNICODE を定義する場合、またはとして`char`かどうか。 A`wchar_t`文字が 16 ビット幅。 MBCS は、シンボル _MBCS が未定義でビルドする場合に有効です。 MFC 自体が (NAFX ライブラリ) の _MBCS シンボルを使って構築または _UNICODE のシンボル (UAFX ライブラリ) を定義します。

> [!NOTE]
>  `CString`これと文字列に付随する記事の例は、_T マクロが、これをフォームにリテラル文字列の変換を使用して、Unicode の移植性に対する適切な形式のリテラル文字列を示します。

`L"literal string"`

> [!NOTE]
>  コンパイラは、Unicode 文字列として扱います。 コード例を次に示します。

[!code-cpp[NVC_ATLMFC_Utilities#187](../atl-mfc-shared/codesnippet/cpp/string-data-management_1.cpp)]

> [!NOTE]
>  _UNICODE が定義されている場合は、Unicode 文字列とない場合は、ANSI 文字列に変換されます。 詳細については、この記事を参照してください。 [Unicode およびマルチバイト文字セット (MBCS) のサポート](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)します。

A `CString` INT_MAX (2,147, 483,647) 文字にオブジェクトを格納できます。 取得または設定内の個々 の文字、TCHAR データ型が使用される、`CString`オブジェクト。 文字の配列とは異なり、`CString`クラスには、組み込みのメモリ割り当てが可能です。 これにより、`CString`必要に応じて自動的に拡張するオブジェクト (は、増加について心配する必要する必要はありません、`CString`長い文字列に合わせてオブジェクト)。

##  <a name="_core_cstrings_and_const_char_pointers"></a> Cstring、const char ポインター

A`CString`オブジェクトは、リテラルの C スタイル文字列のように動作できますも (、`PCXSTR`と同じ**const char** <strong>\*</strong> Unicode 下ではない場合)。 [CSimpleStringT::operator PCXSTR](../atl-mfc-shared/reference/csimplestringt-class.md#operator_pcxstr)変換演算子を使うと`CString`自由に関数呼び出しで文字ポインターの代わりに使用するオブジェクト。 **CString (LPCWSTR** `pszSrc` **)** コンス トラクターの代わりに使用する文字のポインターを使用する`CString`オブジェクト。

折りたたむ場合に試行は行われません`CString`オブジェクト。 2 つの操作を行った場合`CString`オブジェクトを含む`Chicago`、たとえば、内の文字`Chicago`2 つの場所に格納されます。 (この可能性がありますできません MFC では、将来のバージョンの場合は true。 それに依存する必要がありますしないようにします。)

> [!NOTE]
>  使用して、 [CSimpleStringT::GetBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer)と[CSimpleStringT::ReleaseBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#releasebuffer)メンバー関数に直接アクセスする必要がある場合、`CString`文字への非定数ポインターとして。

> [!NOTE]
>  使用して、 [CStringT::AllocSysString](../atl-mfc-shared/reference/cstringt-class.md#allocsysstring)と[名称](../atl-mfc-shared/reference/cstringt-class.md#setsysstring)の割り当てし、オートメーション (以前の OLE オートメーション) で使用される BSTR オブジェクトを設定するメンバー関数。

> [!NOTE]
>  可能であれば、割り当てる`CString`ヒープではなく、フレーム オブジェクト。 これにより、メモリを節約し、パラメーターの引き渡しを簡略化します。

`CString`クラスとして実装されていない Microsoft Foundation Class ライブラリのコレクション クラスでは、ただし`CString`オブジェクトは、コレクション内の要素として確実に保存できます。

##  <a name="_core_cstring_reference_counting"></a> CString の参照カウント

MFC バージョン 4.0 の時点でとき[CStringT クラス](../atl-mfc-shared/reference/cstringt-class.md)オブジェクトがコピーされ、MFC は、データをコピーするのではなく、参照カウントをインクリメントします。 これは、ため、値を返す、パラメーターの引き渡し`CString`より効率的な値でオブジェクト。 これらの操作は、コピー コンス トラクターが呼び出されると、場合によっては複数回に発生します。 これらの一般的な操作のオーバーヘッドを削減しを使用して、参照カウントをインクリメント`CString`もより魅力的なオプションです。

各コピーが破棄されると、元のオブジェクト内の参照カウントは減少します。 元の`CString`オブジェクトは、参照カウントが 0 に減少するまで破棄されません。

使用することができます、`CString`メンバー関数[CSimpleStringT::LockBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#lockbuffer)と[CSimpleStringT::UnlockBuffer](../atl-mfc-shared/reference/csimplestringt-class.md#unlockbuffer)参照カウントを有効または無効にします。

## <a name="see-also"></a>関連項目

[MFC の一般的なトピック](../mfc/general-mfc-topics.md)
