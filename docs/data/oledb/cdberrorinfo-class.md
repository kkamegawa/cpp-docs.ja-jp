---
title: CDBErrorInfo クラス
ms.date: 11/04/2016
f1_keywords:
- CDBErrorInfo
- ATL::CDBErrorInfo
- ATL.CDBErrorInfo
- ATL.CDBErrorInfo.GetAllErrorInfo
- CDBErrorInfo::GetAllErrorInfo
- ATL::CDBErrorInfo::GetAllErrorInfo
- GetAllErrorInfo
- CDBErrorInfo.GetAllErrorInfo
- CDBErrorInfo::GetBasicErrorInfo
- ATL.CDBErrorInfo.GetBasicErrorInfo
- CDBErrorInfo.GetBasicErrorInfo
- ATL::CDBErrorInfo::GetBasicErrorInfo
- GetBasicErrorInfo
- CDBErrorInfo::GetCustomErrorObject
- ATL.CDBErrorInfo.GetCustomErrorObject
- CDBErrorInfo.GetCustomErrorObject
- ATL::CDBErrorInfo::GetCustomErrorObject
- GetCustomErrorObject
- GetErrorInfo
- ATL.CDBErrorInfo.GetErrorInfo
- CDBErrorInfo.GetErrorInfo
- ATL::CDBErrorInfo::GetErrorInfo
- CDBErrorInfo::GetErrorInfo
- ATL.CDBErrorInfo.GetErrorParameters
- CDBErrorInfo::GetErrorParameters
- ATL::CDBErrorInfo::GetErrorParameters
- CDBErrorInfo.GetErrorParameters
- GetErrorParameters
- CDBErrorInfo.GetErrorRecords
- ATL.CDBErrorInfo.GetErrorRecords
- ATL::CDBErrorInfo::GetErrorRecords
- GetErrorRecords
- CDBErrorInfo::GetErrorRecords
helpviewer_keywords:
- CDBErrorInfo class
- GetAllErrorInfo method
- GetBasicErrorInfo method
- GetCustomErrorObject method
- GetErrorInfo method
- GetErrorParameters method
- GetErrorRecords method
ms.assetid: 9a5c18a2-ee3e-40f5-ab4c-581288d7f737
ms.openlocfilehash: bc13137a4222ba51cf3745f9706353d48068a072
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62209335"
---
# <a name="cdberrorinfo-class"></a>CDBErrorInfo クラス

OLE DB を使用して OLE DB エラー処理のサポートを提供します。 [IErrorRecords](/previous-versions/windows/desktop/ms718112(v=vs.85))インターフェイス。

## <a name="syntax"></a>構文

```cpp
class CDBErrorInfo
```

## <a name="requirements"></a>必要条件

**ヘッダー:** atldbcli.h

## <a name="members"></a>メンバー

### <a name="methods"></a>メソッド

|||
|-|-|
|[GetAllErrorInfo](#getallerrorinfo)|エラー レコードに含まれるすべてのエラー情報を返します。|
|[GetBasicErrorInfo](#getbasicerrorinfo)|呼び出し[IErrorRecords::GetBasicErrorInfo](/previous-versions/windows/desktop/ms723907(v=vs.85))指定したエラーに関する基本的な情報を返します。|
|[GetCustomErrorObject](#getcustomerrorobject)|呼び出し[IErrorRecords::GetCustomErrorObject](/previous-versions/windows/desktop/ms725417(v=vs.85))カスタム エラー オブジェクトのインターフェイス ポインターを返します。|
|[GetErrorInfo](#geterrorinfo)|呼び出し[IErrorRecords::GetErrorInfo](/previous-versions/windows/desktop/ms711230(v=vs.85))を返す、`IErrorInfo`指定されたレコードへのインターフェイス ポインター。|
|[GetErrorParameters](#geterrorparameters)|呼び出し[IErrorRecords::GetErrorParameters](/previous-versions/windows/desktop/ms715793(v=vs.85))エラー パラメーターを取得します。|
|[GetErrorRecords](#geterrorrecords)|指定したオブジェクトのエラー レコードを取得します。|

## <a name="remarks"></a>Remarks

このインターフェイスは、ユーザーに 1 つまたは複数のエラー レコードを返します。 呼び出す[cdberrorinfo::geterrorrecords](../../data/oledb/cdberrorinfo-geterrorrecords.md)最初は、エラー レコードの数を取得します。 などのアクセスのいずれかの関数を呼び出します[cdberrorinfo::getallerrorinfo](../../data/oledb/cdberrorinfo-getallerrorinfo.md)、各レコードのエラー情報を取得します。

## <a name="getallerrorinfo"></a> CDBErrorInfo::GetAllErrorInfo

すべての種類のエラー レコードに含まれるエラー情報を返します。

### <a name="syntax"></a>構文

```cpp
HRESULT GetAllErrorInfo(ULONG ulRecordNum,
   LCID lcid,  BSTR* pbstrDescription,
   BSTR* pbstrSource = NULL,
   GUID* pguid = NULL,
   DWORD* pdwHelpContext = NULL,
   BSTR* pbstrHelpFile = NULL) const throw();
```

#### <a name="parameters"></a>パラメーター

*ulRecordNum*<br/>
[in]エラー情報を返す対象のレコードの 0 から始まる番号。

*lcid*<br/>
[in]返されるエラーについては、ロケール ID。

*pbstrDescription*<br/>
[out]ロケールがサポートされていない場合、エラーの説明のテキストへのポインター。 「解説」を参照してください。

*pbstrSource*<br/>
[out]エラーを生成したコンポーネントの名前を含む文字列へのポインター。

*pguid*<br/>
[out]エラーを定義するインターフェイスの GUID へのポインター。

*pdwHelpContext*<br/>
[out]エラーのヘルプ コンテキスト ID へのポインター。

*pbstrHelpFile*<br/>
[out]エラーを説明するヘルプ ファイルへのパスを含む文字列へのポインター。

### <a name="return-value"></a>戻り値

成功した場合は s_ok を返します。 参照してください[IErrorRecords::GetErrorInfo](/previous-versions/windows/desktop/ms711230(v=vs.85))で、 *OLE DB プログラマーズ リファレンス*の他の戻り値。

### <a name="remarks"></a>Remarks

出力値*pbstrDescription*が内部的に呼び出すことによって取得`IErrorInfo::GetDescription`ロケールがサポートされていない場合、または、次の条件の両方に該当する場合、NULL に値を設定します。

1. 値*lcid*米国ではありません英語と

1. 値*lcid*は GetUserDefaultLCID によって返される値と等しくありません。

## <a name="getbasicerrorinfo"></a> CDBErrorInfo::GetBasicErrorInfo

呼び出し[IErrorRecords::GetBasicErrorInfo](/previous-versions/windows/desktop/ms723907(v=vs.85))リターン コードとプロバイダー固有のエラー数など、エラーに関する基本的な情報を返します。

### <a name="syntax"></a>構文

```cpp
HRESULT GetBasicErrorInfo(ULONG ulRecordNum,
   ERRORINFO* pErrorInfo) const throw();
```

#### <a name="parameters"></a>パラメーター

参照してください[IErrorRecords::GetBasicErrorInfo](/previous-versions/windows/desktop/ms723907(v=vs.85))で、 *OLE DB プログラマーズ リファレンス*します。

### <a name="return-value"></a>戻り値

標準の HRESULT です。

## <a name="getcustomerrorobject"></a> CDBErrorInfo::GetCustomErrorObject

呼び出し[IErrorRecords::GetCustomErrorObject](/previous-versions/windows/desktop/ms725417(v=vs.85))カスタム エラー オブジェクトのインターフェイス ポインターを返します。

### <a name="syntax"></a>構文

```cpp
HRESULT GetCustomErrorObject(ULONG ulRecordNum,
   REFIID riid,IUnknown** ppObject) const throw();
```

#### <a name="parameters"></a>パラメーター

参照してください[IErrorRecords::GetCustomErrorObject](/previous-versions/windows/desktop/ms725417(v=vs.85))で、 *OLE DB プログラマーズ リファレンス*します。

### <a name="return-value"></a>戻り値

標準の HRESULT です。

## <a name="geterrorinfo"></a> CDBErrorInfo::GetErrorInfo

呼び出し[IErrorRecords::GetErrorInfo](/previous-versions/windows/desktop/ms711230(v=vs.85))を返す、 [IErrorInfo](/previous-versions/windows/desktop/ms718112(v=vs.85))指定されたレコードへのインターフェイス ポインター。

### <a name="syntax"></a>構文

```cpp
HRESULT GetErrorInfo(ULONG ulRecordNum,
   LCID lcid,IErrorInfo** ppErrorInfo) const throw();
```

#### <a name="parameters"></a>パラメーター

参照してください[IErrorRecords::GetErrorInfo](/previous-versions/windows/desktop/ms711230(v=vs.85))で、 *OLE DB プログラマーズ リファレンス*します。

### <a name="return-value"></a>戻り値

標準の HRESULT です。

## <a name="geterrorparameters"></a> CDBErrorInfo::GetErrorParameters

呼び出し[IErrorRecords::GetErrorParameters](/previous-versions/windows/desktop/ms715793(v=vs.85))エラー パラメーターを取得します。

### <a name="syntax"></a>構文

```cpp
HRESULT GetErrorParameters(ULONG ulRecordNum,
   DISPPARAMS* pdispparams) const throw();
```

#### <a name="parameters"></a>パラメーター

参照してください[IErrorRecords::GetErrorParameters](/previous-versions/windows/desktop/ms715793(v=vs.85))で、 *OLE DB プログラマーズ リファレンス*します。

### <a name="return-value"></a>戻り値

標準の HRESULT です。

## <a name="geterrorrecords"></a> CDBErrorInfo::GetErrorRecords

指定したオブジェクトのエラー レコードを取得します。

### <a name="syntax"></a>構文

```cpp
HRESULT GetErrorRecords(IUnknown* pUnk,
   const IID& iid,
   ULONG* pcRecords) throw();

HRESULT GetErrorRecords(ULONG* pcRecords) throw();
```

#### <a name="parameters"></a>パラメーター

*pUnk*<br/>
[in]エラー レコードを取得する対象のオブジェクトへのインターフェイスします。

*iid*<br/>
[in]エラーに関連付けられているインターフェイスの IID。

*pcRecords*<br/>
[out]エラー レコードの (1 から始まる) の数へのポインター。

### <a name="return-value"></a>戻り値

標準の HRESULT です。

### <a name="remarks"></a>Remarks

エラー情報を取得するには、どのインターフェイスを確認したい場合は、関数の最初のフォームを使用します。 それ以外の場合、2 番目の形式を使用します。

## <a name="see-also"></a>関連項目

[DBViewer](../../overview/visual-cpp-samples.md)<br/>
[OLE DB コンシューマー テンプレート](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB コンシューマー テンプレート リファレンス](../../data/oledb/ole-db-consumer-templates-reference.md)