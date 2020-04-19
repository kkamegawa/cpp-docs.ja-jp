---
title: CSecurityAttributes クラス
ms.date: 11/04/2016
f1_keywords:
- CSecurityAttributes
- ATLSECURITY/ATL::CSecurityAttributes
- ATLSECURITY/ATL::CSecurityAttributes::CSecurityAttributes
- ATLSECURITY/ATL::CSecurityAttributes::Set
helpviewer_keywords:
- CSecurityAttributes class
ms.assetid: a094880c-52e1-4a28-97ff-752d5869908e
ms.openlocfilehash: ebffbea120101a77450a5e8da3cdb6e34723e7be
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496502"
---
# <a name="csecurityattributes-class"></a>CSecurityAttributes クラス

このクラスは、security attributes 構造体のシンラッパーです。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行されるアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
class CSecurityAttributes : public SECURITY_ATTRIBUTES
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CSecurityAttributes:: CSecurityAttributes](#csecurityattributes)|コンストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CSecurityAttributes:: Set](#set)|`CSecurityAttributes`オブジェクトの属性を設定するには、このメソッドを呼び出します。|

## <a name="remarks"></a>Remarks

構造`SECURITY_ATTRIBUTES`体には、オブジェクトの作成に使用される[セキュリティ記述子](/windows/win32/api/winnt/ns-winnt-security_descriptor)が含まれ、この構造体を指定して取得されたハンドルが継承可能かどうかを指定します。

Windows のアクセス制御モデルの概要については、Windows SDK の「 [Access Control](/windows/win32/SecAuthZ/access-control) 」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

`SECURITY_ATTRIBUTES`

`CSecurityAttributes`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlsecurity .h

##  <a name="csecurityattributes"></a>CSecurityAttributes:: CSecurityAttributes

コンストラクターです。

```
CSecurityAttributes() throw();
explicit CSecurityAttributes(const CSecurityDesc& rSecurityDescriptor, bool bInheritsHandle = false) throw(...);
```

### <a name="parameters"></a>パラメーター

*rSecurityDescriptor*<br/>
セキュリティ記述子への参照。

*bInheritsHandle*<br/>
新しいプロセスの作成時に、返されたハンドルを継承するかどうかを指定します。 このメンバーが true の場合、新しいプロセスは、返されたハンドルを継承します。

##  <a name="set"></a>CSecurityAttributes:: Set

`CSecurityAttributes`オブジェクトの属性を設定するには、このメソッドを呼び出します。

```
void Set(const CSecurityDesc& rSecurityDescriptor, bool bInheritHandle = false) throw(...);
```

### <a name="parameters"></a>パラメーター

*rSecurityDescriptor*<br/>
セキュリティ記述子への参照。

*bInheritHandle*<br/>
新しいプロセスの作成時に、返されたハンドルを継承するかどうかを指定します。 このメンバーが true の場合、新しいプロセスは、返されたハンドルを継承します。

### <a name="remarks"></a>Remarks

このメソッドは、 `CSecurityAttributes`オブジェクトを初期化するためにコンストラクターによって使用されます。

## <a name="see-also"></a>関連項目

[セキュリティのサンプル](../../overview/visual-cpp-samples.md)<br/>
[SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\))<br/>
[セキュリティ記述子](/windows/win32/api/winnt/ns-winnt-security_descriptor)<br/>
[クラスの概要](../../atl/atl-class-overview.md)<br/>
[セキュリティに関するグローバル関数](../../atl/reference/security-global-functions.md)
