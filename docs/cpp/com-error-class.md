---
title: _com_error クラス
ms.date: 11/04/2016
f1_keywords:
- _com_error
helpviewer_keywords:
- _com_error class
ms.assetid: 70dafa69-b1fb-4a5c-9249-e857e0793d42
ms.openlocfilehash: 828a1ec68fef631700d5b64e6aeeec6660acf9a8
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498746"
---
# <a name="_com_error-class"></a>_com_error クラス

**Microsoft 固有の仕様**

エラーオブジェクトは、タイプライブラリから生成されたヘッダーファイル内のエラー処理ラッパー関数、またはいずれかの com サポートクラスによって検出された例外条件を表します。 **エラー**クラスは、HRESULT エラーコードおよび関連付けられている`IErrorInfo Interface`オブジェクトをカプセル化します。

### <a name="construction"></a>構築

|||
|-|-|
|[_com_error](../cpp/com-error-com-error.md)|エラーオブジェクトを構築します ( **_t** )。|

### <a name="operators"></a>演算子

|||
|-|-|
|[operator=](../cpp/com-error-operator-equal.md)|既存の**エラー**オブジェクトを別のオブジェクトに割り当てます。|

### <a name="extractor-functions"></a>抽出関数

|||
|-|-|
|[エラー](../cpp/com-error-error.md)|コンストラクターに渡された HRESULT を取得します。|
|[ErrorInfo](../cpp/com-error-errorinfo.md)|コンストラクターに渡された `IErrorInfo` オブジェクトを取得します。|
|[WCode](../cpp/com-error-wcode.md)|カプセル化された HRESULT にマップされた16ビットエラーコードを取得します。|

### <a name="ierrorinfo-functions"></a>IErrorInfo の関数

|||
|-|-|
|[説明](../cpp/com-error-description.md)|`IErrorInfo::GetDescription` 関数を呼び出します。|
|[HelpContext](../cpp/com-error-helpcontext.md)|`IErrorInfo::GetHelpContext` 関数を呼び出します。|
|[HelpFile](../cpp/com-error-helpfile.md)|`IErrorInfo::GetHelpFile` 関数を呼び出します。|
|[ソース](../cpp/com-error-source.md)|`IErrorInfo::GetSource` 関数を呼び出します。|
|[GUID](../cpp/com-error-guid.md)|`IErrorInfo::GetGUID` 関数を呼び出します。|

### <a name="format-message-extractor"></a>書式メッセージの抽出

|||
|-|-|
|[ErrorMessage](../cpp/com-error-errormessage.md)|HRESULT の文字列メッセージを取得します。**エラー**オブジェクトに格納されます。|

### <a name="exepinfowcode-to-hresult-mappers"></a>ExepInfo.wCode と HRESULT のマッパー

|||
|-|-|
|[HRESULTToWCode](../cpp/com-error-hresulttowcode.md)|32ビットの HRESULT を16ビット`wCode`にマップします。|
|[WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)|16ビット`wCode`を32ビット HRESULT にマップします。|

**Microsoft 固有の仕様はここまで**

## <a name="requirements"></a>必要条件

**ヘッダー:** \<comdef. h >

`Lib:`(詳細については、「 [/zc: wchar_t (Wchar_t はネイティブ型)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) 」を参照してください)

## <a name="see-also"></a>関連項目

[コンパイラ COM サポート クラス](../cpp/compiler-com-support-classes.md)<br/>
[IErrorInfo インターフェイス](/windows/win32/api/oaidl/nn-oaidl-ierrorinfo)