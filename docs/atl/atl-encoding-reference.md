---
title: ATL のエンコーディングのリファレンス
ms.date: 11/04/2016
helpviewer_keywords:
- encoding
- encoding, functions
ms.assetid: 82d4fdf3-3c4a-4fe2-b297-8ffb4714406f
ms.openlocfilehash: a9c7689e49efce0d65e945f1a032a680e2277594
ms.sourcegitcommit: 878a164fe6d550ca81ab87d8425c8d3cd52fe384
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/22/2019
ms.locfileid: "68375868"
---
# <a name="atl-encoding-reference"></a>ATL のエンコーディングのリファレンス

Uuencode、16進数、UTF8 などの一般的なインターネット標準の範囲内でのエンコードは、atlenc で見つかったコードによってサポートされています。

### <a name="functions"></a>関数

|||
|-|-|
|[AtlGetHexValue](reference/atl-text-encoding-functions.md#atlgethexvalue)|16 進数の数値を取得します。|
|[AtlHexDecode](reference/atl-text-encoding-functions.md#atlhexdecode)|[AtlHexEncode](reference/atl-text-encoding-functions.md#atlhexencode)の以前の呼び出しによって、16進数のテキストとしてエンコードされたデータの文字列をデコードします。|
|[AtlHexDecodeGetRequiredLength](reference/atl-text-encoding-functions.md#atlhexdecodegetrequiredlength)|指定した長さの 16 進エンコードされた文字列からデコードされたデータを格納できるバッファーのサイズを、バイト単位で取得します。|
|[AtlHexEncode](reference/atl-text-encoding-functions.md#atlhexencode)|一部のデータを 16 進テキストの文字列としてエンコードします。|
|[AtlHexEncodeGetRequiredLength](reference/atl-text-encoding-functions.md#atlhexencodegetrequiredlength)|指定したサイズのデータからエンコードされた文字列を格納できるバッファーのサイズを、文字数で取得します。|
|[AtlUnicodeToUTF8](reference/atl-text-encoding-functions.md#atlunicodetoutf8)|Unicode 文字列を UTF-8 に変換します。|
|[BEncode](reference/atl-text-encoding-functions.md#bencode)|"B" エンコーディングを使用して一部のデータを変換します。|
|[BEncodeGetRequiredLength](reference/atl-text-encoding-functions.md#bencodegetrequiredlength)|指定したサイズのデータからエンコードされた文字列を格納できるバッファーのサイズを、文字数で取得します。|
|[EscapeXML](reference/atl-text-encoding-functions.md#escapexml)|XML での使用には安全でない文字を安全な文字に変換します。|
|[GetExtendedChars](reference/atl-text-encoding-functions.md#getextendedchars)|文字列に含まれる拡張文字の数を取得します。|
|[IsExtendedChar](reference/atl-text-encoding-functions.md#isextendedchar)|この関数を呼び出して、特定の文字が拡張文字 (32 未満、126より大きい、タブ、ラインフィード、またはキャリッジリターンではない) であるかどうかを確認します。|
|[QEncode](reference/atl-text-encoding-functions.md#qencode)|"Q" エンコーディングを使用して一部のデータを変換します。|
|[QEncodeGetRequiredLength](reference/atl-text-encoding-functions.md#qencodegetrequiredlength)|指定したサイズのデータからエンコードされた文字列を格納できるバッファーのサイズを、文字数で取得します。|
|[QPDecode](reference/atl-text-encoding-functions.md#qpdecode)|前回の[qの](reference/atl-text-encoding-functions.md#qpencode)呼び出しによってなど、引用符で囲まれた印刷可能な形式でエンコードされたデータの文字列をデコードします。|
|[QPDecodeGetRequiredLength](reference/atl-text-encoding-functions.md#qpdecodegetrequiredlength)|quoted-printable にエンコードされた指定長の文字列からデコードされたデータを格納できるバッファーのサイズを、バイト単位で取得します。|
|[Qのコード](reference/atl-text-encoding-functions.md#qpencode)|一部のデータを quoted-printable 形式にエンコードします。|
|[QPEncodeGetRequiredLength](reference/atl-text-encoding-functions.md#qpencodegetrequiredlength)|指定したサイズのデータからエンコードされた文字列を格納できるバッファーのサイズを、文字数で取得します。|
|[UUDecode](reference/atl-text-encoding-functions.md#uudecode)|[Uuencode](reference/atl-text-encoding-functions.md#uuencode)の前回の呼び出しによって、uuencode されたデータの文字列をデコードします。|
|[UUDecodeGetRequiredLength](reference/atl-text-encoding-functions.md#uudecodegetrequiredlength)|指定した長さの uuencode された文字列からデコードされたデータを格納できるバッファーのサイズを、バイト単位で取得します。|
|[UUEncode](reference/atl-text-encoding-functions.md#uuencode)|データを uuencode します。|
|[UUEncodeGetRequiredLength](reference/atl-text-encoding-functions.md#uuencodegetrequiredlength)|指定したサイズのデータからエンコードされた文字列を格納できるバッファーのサイズを、文字数で取得します。|

## <a name="see-also"></a>関連項目

[概念](../atl/active-template-library-atl-concepts.md)<br/>
[ATL COM デスクトップ コンポーネント](../atl/atl-com-desktop-components.md)
