---
title: CDynamicStringAccessor クラス
ms.date: 11/04/2016
f1_keywords:
- CDynamicStringAccessor
- CDynamicStringAccessor.GetString
- CDynamicStringAccessor::GetString
- CDynamicStringAccessor::SetString
- CDynamicStringAccessor.SetString
helpviewer_keywords:
- CDynamicStringAccessor class
- GetString method
- SetString method
ms.assetid: 138dc4de-c7c3-478c-863e-431e48249027
ms.openlocfilehash: 6ba56143beb3411734899839a46ab42992dfa4d8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62230996"
---
# <a name="cdynamicstringaccessor-class"></a>CDynamicStringAccessor クラス

データベース スキーマ (データベースの基になる構造) の知識があるない場合にデータ ソースにアクセスすることができます。

## <a name="syntax"></a>構文

```cpp
template< typename BaseType, DBTYPEENUM OleDbType >
class CDynamicStringAccessorT : public CDynamicAccessor
```

## <a name="requirements"></a>必要条件

**ヘッダー**: atldbcli.h

## <a name="members"></a>メンバー

### <a name="methods"></a>メソッド

|||
|-|-|
|[GetString](#getstring)|指定された列のデータを文字列として取得します。|
|[SetString](#setstring)|文字列として指定された列のデータを設定します。|

## <a name="remarks"></a>Remarks

中に[CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) 、プロバイダーによって報告されたネイティブ形式でデータを要求`CDynamicStringAccessor`要求プロバイダーが文字列データとしてデータ ストアからすべてのデータをフェッチします。 これは、表示またはデータ ストアの内容を印刷するなど、データ ストア内の値の計算を必要としない単純なタスクに特に便利です。

データ ストア内の列のデータのネイティブな型は問題になりません。プロバイダーがデータ変換をサポートできる限りの文字列形式のデータが供給されます。 プロバイダーが、ネイティブ データ型から (これは一般的ではない) 文字列への変換をサポートしていない場合、要求側の呼び出しは DB_S_ERRORSOCCURED、成功の値を返しに対応する列のステータスには、変換の問題によって示されますDBSTATUS_E_CANTCONVERTVALUE します。

使用`CDynamicStringAccessor`列情報を取得するメソッド。 実行時に動的にアクセサーを作成するのにには、この列の情報を使用します。

列の情報は、このクラスによって作成および管理のバッファーに格納されます。 使用してバッファーからデータを取得[GetString](../../data/oledb/cdynamicstringaccessor-getstring.md)を使用して、バッファーに格納または[SetString](../../data/oledb/cdynamicstringaccessor-setstring.md)します。

動的アクセサー クラスの使用例とについては、次を参照してください。[動的アクセサーの使用](../../data/oledb/using-dynamic-accessors.md)します。

## <a name="getstring"></a> CDynamicStringAccessor::GetString

指定された列のデータを文字列として取得します。

### <a name="syntax"></a>構文

```cpp
BaseType* GetString(DBORDINAL nColumn) const throw();

BaseType* GetString(const CHAR* pColumnName) const throw();

BaseType* GetString(const WCHAR* pColumnName) const throw();
```

#### <a name="parameters"></a>パラメーター

*nColumn*<br/>
[in]列の番号。 列番号 1 から始まります。 値 0 は、存在する場合、ブックマーク列を参照します。

*pColumnName*<br/>
[in]列名を含む文字列へのポインター。

### <a name="return-value"></a>戻り値

文字列値へのポインターは、指定された列から取得されます。 型の値は、`BaseType`は**CHAR**または**WCHAR** _UNICODE が定義されているかどうかどうかによって異なります。 指定された列が見つからない場合は、NULL を返します。

### <a name="remarks"></a>Remarks

2 番目のオーバーライド フォームは、ANSI 文字列として列名を取得します。 3 番目のオーバーライド フォームは、Unicode 文字列として列名を取得します。

## <a name="setstring"></a> CDynamicStringAccessor::SetString

文字列として指定された列のデータを設定します。

### <a name="syntax"></a>構文

```cpp
HRESULT SetString(DBORDINAL nColumn,
   BaseType* data) throw();

HRESULT SetString(const CHAR* pColumnName,
   BaseType* data) throw();

HRESULT SetString(const WCHAR* pColumnName,
   BaseType* data) throw();
```

#### <a name="parameters"></a>パラメーター

*nColumn*<br/>
[in]列の番号。 列番号 1 から始まります。 0 の特殊な値は、存在する場合、ブックマーク列を参照します。

*pColumnName*<br/>
[in]列名を含む文字列へのポインター。

*data*<br/>
[in]指定された列に書き込まれる文字列のデータへのポインター。

### <a name="return-value"></a>戻り値

指定された列を設定する文字列値へのポインター。 型の値は、`BaseType`は**CHAR**または**WCHAR** _UNICODE が定義されているかどうかどうかによって異なります。

### <a name="remarks"></a>Remarks

オーバーライド フォームは、ANSI 文字列として列名、2 番目と 3 番目のオーバーライド フォームは Unicode 文字列として列名。

場合、ランタイム アサーション エラーが生成されます _SECURE_ATL の 0 以外の値を持つが定義されている場合、入力*データ*文字列が参照されるデータ列の最大許容長を超えています。 それ以外の場合、許容される最大長よりも長い場合に、入力文字列が切り捨てられます。

## <a name="see-also"></a>関連項目

[OLE DB コンシューマー テンプレート](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB コンシューマー テンプレート リファレンス](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor クラス](../../data/oledb/caccessor-class.md)<br/>
[CDynamicParameterAccessor クラス](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
[CManualAccessor クラス](../../data/oledb/cmanualaccessor-class.md)<br/>
[CDynamicAccessor クラス](../../data/oledb/cdynamicaccessor-class.md)<br/>
[CDynamicStringAccessorA クラス](../../data/oledb/cdynamicstringaccessora-class.md)<br/>
[CDynamicStringAccessorW クラス](../../data/oledb/cdynamicstringaccessorw-class.md)<br/>
[CXMLAccessor クラス](../../data/oledb/cxmlaccessor-class.md)