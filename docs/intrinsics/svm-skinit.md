---
title: __svm_skinit
ms.date: 09/02/2019
f1_keywords:
- __svm_skinit
helpviewer_keywords:
- SKINIT instruction
- __svm_skinit intrinsic
ms.assetid: 787ec781-4cf2-40a2-aa20-5192334b131a
ms.openlocfilehash: 6657921d647a23bf027a5800702527951f7f6831
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219858"
---
# <a name="__svm_skinit"></a>__svm_skinit

**Microsoft 固有の仕様**

バーチャルマシンモニターなどの検証可能なセキュリティで保護されたソフトウェアの読み込みを開始します。

## <a name="syntax"></a>構文

```C
void __svm_skinit(
   int block_address
);
```

### <a name="parameters"></a>パラメーター

*block_address*\
64 k バイトセキュアローダーブロック (SLB) の32ビット物理アドレス。

## <a name="remarks"></a>Remarks

`__svm_skinit` 関数は `SKINIT` マシン語命令と同じです。 この機能は、プロセッサとトラステッドプラットフォームモジュール (TPM) を使用して、*セキュリティカーネル*(SK) と呼ばれる信頼されたソフトウェアの検証と読み込みを行うセキュリティシステムの一部です。 仮想マシンモニターは、セキュリティカーネルの一例です。 セキュリティシステムは、初期化プロセス中に読み込まれたプログラムコンポーネントを検証します。 割り込み、デバイスアクセス、またはコンピューターがマルチプロセッサの場合、別のプログラムによって、コンポーネントの改ざんを防ぐことができます。

*Block_address*パラメーターは、 *Secure Loader block* (SLB) と呼ばれる 64 k のメモリブロックの物理アドレスを指定します。 SLB には、*セキュアローダー*と呼ばれるプログラムが含まれています。 コンピューターの運用環境を確立し、セキュリティカーネルを読み込みます。

この関数は、ホストの仮想マシンのモニターと、ゲスト オペレーティング システムとそのアプリケーションとの対話をサポートします。 詳細については、「AMD64 アーキテクチャプログラマの手動ボリューム 2:システムプログラミングについては、「 [AMD corporation](https://developer.amd.com/resources/developer-guides-manuals/)サイト」をご覧ください。

## <a name="requirements"></a>必要条件

|組み込み|アーキテクチャ|
|---------------|------------------|
|`__svm_skinit`|x86、x64|

**ヘッダーファイル**\<>

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)
