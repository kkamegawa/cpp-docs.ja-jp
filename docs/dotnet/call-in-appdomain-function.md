---
title: call_in_appdomain 関数
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- call_in_appdomain
helpviewer_keywords:
- call_in_appdomain function
ms.assetid: 9a1a5026-b76b-4cae-a3d4-29badeb9db9c
ms.openlocfilehash: a7ee0ef9c98ee940ab810abd82f6220da95d7346
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62351496"
---
# <a name="callinappdomain-function"></a>call_in_appdomain 関数

指定したアプリケーション ドメインでは、関数を実行します。

## <a name="syntax"></a>構文

```
template <typename ArgType1, ...typename ArgTypeN>
void call_in_appdomain(
   DWORD appdomainId,
   void (*voidFunc)(ArgType1, ...ArgTypeN) [ ,
   ArgType1 arg1,
   ...
   ArgTypeN argN ]
);
template <typename RetType, typename ArgType1, ...typename ArgTypeN>
RetType call_in_appdomain(
   DWORD appdomainId,
   RetType (*nonvoidFunc)(ArgType1, ...ArgTypeN) [ ,
   ArgType1 arg1,
   ...
   ArgTypeN argN ]
);
```

#### <a name="parameters"></a>パラメーター

*appdomainId*<br/>
関数を呼び出すアプリケーション ドメイン。

*voidFunc*<br/>
ポインターを`void`N パラメーターを受け取る関数 (0 < = N < = 15)。

*nonvoidFunc*<br/>
以外へのポインター`void` N パラメーターを受け取る関数 (0 < = N < = 15)。

*arg1...argN*<br/>
0 ~ 15 個のパラメーターに渡される`voidFunc`または`nonvoidFunc`他の appdomain にします。

## <a name="return-value"></a>戻り値

実行結果`voidFunc`または`nonvoidFunc`で指定されたアプリケーション ドメイン。

## <a name="remarks"></a>Remarks

関数の引数に渡されます`call_in_appdomain`CLR 型をすることはできません。

## <a name="example"></a>例

```
// msl_call_in_appdomain.cpp
// compile with: /clr

// Defines two functions: one takes a parameter and returns nothing,
// the other takes no parameters and returns an int.  Calls both
// functions in the default appdomain and in a newly-created
// application domain using call_in_appdomain.

#include <msclr\appdomain.h>

using namespace System;
using namespace msclr;

void PrintCurrentDomainName( char* format )
{
   String^ s = gcnew String(format);
   Console::WriteLine( s, AppDomain::CurrentDomain->FriendlyName );
}

int GetDomainId()
{
   return AppDomain::CurrentDomain->Id;
}

int main()
{
   AppDomain^ appDomain1 = AppDomain::CreateDomain( "First Domain" );

   call_in_appdomain( AppDomain::CurrentDomain->Id,
                   &PrintCurrentDomainName,
                   (char*)"default appdomain: {0}" );
   call_in_appdomain( appDomain1->Id,
                   &PrintCurrentDomainName,
                   (char*)"in appDomain1: {0}" );

   int id;
   id = call_in_appdomain( AppDomain::CurrentDomain->Id, &GetDomainId );
   Console::WriteLine( "default appdomain id = {0}", id );
   id = call_in_appdomain( appDomain1->Id, &GetDomainId );
   Console::WriteLine( "appDomain1 id = {0}", id );
}
```

## <a name="output"></a>出力

```
default appdomain: msl_call_in_appdomain.exe
in appDomain1: First Domain
default appdomain id = 1
appDomain1 id = 2
```

## <a name="requirements"></a>必要条件

**ヘッダー ファイル** \<msclr\appdomain.h >

**Namespace** msclr