---
title: CStrBufT クラス
ms.date: 10/18/2018
f1_keywords:
- CStrBufT
- ATLSIMPSTR/ATL::CStrBufT
- ATLSIMPSTR/ATL::CStrBufT::CStrBufT
- ATLSIMPSTR/ATL::CStrBufT::SetLength
- ATLSIMPSTR/ATL::CStrBufT::AUTO_LENGTH
- ATLSIMPSTR/ATL::CStrBufT::SET_LENGTH
helpviewer_keywords:
- strings [C++], custom memory management
- CStrBufT class
- shared classes, CStrBufT
ms.assetid: 6b50fa8f-87e8-4ed4-a229-157ce128710f
ms.openlocfilehash: 81c3b429089eab3ba95c178e3fc7cf2bf55783a2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62223494"
---
# <a name="cstrbuft-class"></a>CStrBufT クラス

このクラスは、リソースの自動クリーンアップの`GetBuffer`と`ReleaseBuffer`既存呼び出し`CStringT`オブジェクト。

## <a name="syntax"></a>構文

```
template<typename TCharType>
class CStrBufT
```

#### <a name="parameters"></a>パラメーター

*TCharType*<br/>
文字型、`CStrBufT`クラス。 次のいずれかの値を指定します。

- **char** (の ANSI 文字列)

- **wchar_t** (の Unicode 文字の文字列)

- TCHAR (の ANSI および Unicode 文字列)

## <a name="members"></a>メンバー

### <a name="public-typedefs"></a>パブリック typedef

|名前|説明|
|----------|-----------------|
|PCXSTR|定数文字列へのポインター。|
|PXSTR|文字列へのポインター。|
|`StringType`|バッファーがこのクラス テンプレートの特殊化によって操作される文字列型。|

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CStrBufT::CStrBufT](#cstrbuft)|文字列のバッファー オブジェクトのコンス トラクター。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CStrBufT::SetLength](#setlength)|関連付けられている文字列オブジェクトの文字バッファーの長さを設定します。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CStrBufT::operator PCXSTR](#operator_pcxstr)|取得、 **const**関連付けられている文字列オブジェクトの文字バッファーへのポインター。|
|[CStrBufT::operator PXSTR](#operator_pxstr)|関連付けられている文字列オブジェクトの文字バッファーへのポインターを取得します。|

### <a name="public-constants"></a>パブリック定数

|名前|説明|
|----------|-----------------|
|[CStrBufT::AUTO_LENGTH](#auto_length)|新しいリリースで、文字列の長さを自動的に決定します。|
|[CStrBufT::SET_LENGTH](#set_length)|GetBuffer 時に文字列オブジェクトの長さを設定します。|

## <a name="remarks"></a>Remarks

このクラスはへの呼び出しを置き換えるため、ラッパー クラスとして使用[GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer)と[ReleaseBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#releasebuffer)、または[GetBufferSetLength](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffersetlength)と`ReleaseBuffer`します。

ヘルパー クラスとして主に設計されています`CStrBufT`方法の詳細について心配することがなく、文字列オブジェクトの文字バッファーを使用する開発者にとって便利な方法を提供します。 またはを呼び出すタイミング`ReleaseBuffer`します。 これは、ラッパー オブジェクトが例外または終了する複数のコード パスの場合は当然のスコープ外になるため、可能文字列リソースを解放するには、そのデストラクターが原因で。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlsimpstr.h

##  <a name="auto_length"></a>  CStrBufT::AUTO_LENGTH

新しいリリースで、文字列の長さを自動的に決定します。

```
static const DWORD AUTO_LENGTH = 0x01;
```

### <a name="remarks"></a>Remarks

新しいリリースで、文字列の長さを自動的に決定します。 Null で終わる文字列がある必要があります。

##  <a name="cstrbuft"></a>  CStrBufT::CStrBufT

バッファー オブジェクトを構築します。

```
CStrBufT(StringType& str, int nMinLength, DWORD dwFlags = AUTO_LENGTH) throw(...);
explicit CStrBufT(StringType& str) throw(...);
```

### <a name="parameters"></a>パラメーター

*str*<br/>
バッファーに関連付けられている文字列オブジェクト。 通常、開発者がの定義済みの typedef を使用`CStrBuf`(TCHAR バリアント型)、 `CStrBufA` (**char**バリアント型) と`CStrBufW`(**wchar_t**バリアント型)。

*nMinLength*<br/>
文字バッファーの最小長。

*dwFlags*<br/>
文字列の長さが自動的に決定されているかどうかを決定します。 次のいずれかの値を指定します。

- AUTO_LENGTH 文字列の長さが自動的に決定するときに[CSimpleStringT::Release](../../atl-mfc-shared/reference/csimplestringt-class.md#releasebuffer)が呼び出されます。 Null で終わる文字列がある必要があります。 既定値です。

- 場合、SET_LENGTH 文字列の長さが設定[CSimpleStringT::GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer)が呼び出されます。

### <a name="remarks"></a>Remarks

関連付けられている文字列オブジェクトの文字列バッファーを作成します。 構築時に、 [CSimpleStringT::GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer)または[CSimpleStringT::GetBufferSetLength](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffersetlength)が呼び出されます。

コピー コンス トラクターは**プライベート**します。

##  <a name="operator_pcxstr"></a>  CStrBufT::operator PCXSTR

関連付けられている文字列オブジェクトを C スタイルの文字列として格納される文字が直接アクセスします。

```
operator PCXSTR() const throw();
```

### <a name="return-value"></a>戻り値

文字列のデータを指すポインター。

### <a name="remarks"></a>Remarks

この関数では、文字列オブジェクトの文字バッファーへのポインターを返します。 このポインターには、文字列オブジェクトの内容を変更できません。

##  <a name="operator_pxstr"></a>  CStrBufT::operator PXSTR

関連付けられている文字列オブジェクトを C スタイルの文字列として格納される文字が直接アクセスします。

```
operator PXSTR() throw();
```

### <a name="return-value"></a>戻り値

文字列のデータを指すポインター。

### <a name="remarks"></a>Remarks

この関数では、文字列オブジェクトの文字バッファーへのポインターを返します。 開発者は、このポインターを持つ文字列オブジェクトの内容を変更できます。

##  <a name="pcxstr"></a>  CStrBufT::PCXSTR

定数文字列へのポインター。

```
typedef CSimpleStringT<TCharType>::PCXSTR PCXSTR;
```

##  <a name="pxstr"></a>  CStrBufT::PXSTR

文字列へのポインター。

```
typedef CSimpleStringT<TCharType>::PXSTR PXSTR;
```

##  <a name="set_length"></a>  CStrBufT::SET_LENGTH

文字列オブジェクトの長さを設定`GetBuffer`時間。

```
static const DWORD SET_LENGTH = 0x02;
```

### <a name="remarks"></a>Remarks

GetBuffer 時に、文字列オブジェクトの長さを設定します。

かどうかを[CSimpleStringT::GetBuffer](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffer)と[CSimpleStringT::GetBufferSetLength](../../atl-mfc-shared/reference/csimplestringt-class.md#getbuffersetlength)文字列バッファー オブジェクトが構築された場合に呼び出されます。

##  <a name="setlength"></a>  CStrBufT::SetLength

文字バッファーの長さを設定します。

```
void SetLength(int nLength);
```

### <a name="parameters"></a>パラメーター

*nLength*<br/>
文字列オブジェクトの文字バッファーの新しい長さ。

> [!NOTE]
>  コンス トラクターで指定された最小バッファー長未満でなければなりません`CStrBufT`します。

### <a name="remarks"></a>Remarks

バッファー オブジェクトによって表される文字列の長さを設定するには、この関数を呼び出します。

##  <a name="stringtype"></a>  CStrBufT::StringType

バッファーがこのクラス テンプレートの特殊化によって操作される文字列型。

```
typedef CSimpleStringT<TCharType> StringType;
```

### <a name="remarks"></a>Remarks

`TCharType` 文字型は、クラス テンプレートの特殊化に使用されます。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[ATL/MFC 共有クラス](../../atl-mfc-shared/atl-mfc-shared-classes.md)
