---
title: volatile (C++)
ms.date: 05/07/2019
f1_keywords:
- volatile_cpp
helpviewer_keywords:
- interrupt handlers and volatile keyword [C++]
- volatile keyword [C++]
- volatile objects
- objects [C++], volatile
ms.assetid: 81db4a85-ed5a-4a2c-9a53-5d07a771d2de
ms.openlocfilehash: 572fe244a076492e3f3316dd6d00f6fe7d7c3c9c
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857204"
---
# <a name="volatile-c"></a>volatile (C++)

オブジェクトをハードウェアがプログラム内で変更できることを宣言するために使用できる型修飾子です。

## <a name="syntax"></a>構文

```
volatile declarator ;
```

## <a name="remarks"></a>Remarks

[/Volatile](../build/reference/volatile-volatile-keyword-interpretation.md)コンパイラスイッチを使用して、コンパイラがこのキーワードを解釈する方法を変更できます。

Visual Studio の解釈、**volatile**ターゲット アーキテクチャに応じて、異なるキーワード。 ARM では、 **/volatile**コンパイラオプションが指定されていない場合、コンパイラは **/volatile: iso**が指定されているかのように実行します。 ARM 以外のアーキテクチャでは、 **/volatile**コンパイラオプションが指定されていない場合、コンパイラは **/volatile: ms**が指定されているかのように実行します。そのため、ARM 以外のアーキテクチャの場合は、 **/volatile: iso**を指定することを強くお勧めします。また、スレッド間で共有されるメモリを扱う場合は、明示的な同期プリミティブとコンパイラ組み込みを使用することをお勧めします。

使用することができます、**volatile**割り込みハンドラーのような非同期プロセスによって使用されるメモリの場所へのアクセスを提供する修飾子。

ときに**volatile**も持っている変数の使用は、 [_ _restrict](../cpp/extension-restrict.md)キーワード、**volatile**が優先されます。

場合、**struct**メンバーをマーク**volatile**、し**volatile**構造全体に伝達されます。 構造体がコピーできる長さ、現在のアーキテクチャで 1 つの命令を使用して**volatile**その構造に完全に失われる可能性があります。

**volatile**キーワード効果を持ちませんフィールドで、次の条件のいずれかが true の場合。

- volatile フィールドの長さが、現在のアーキテクチャで 1 つの命令を使用してコピーできる最大サイズを超えている。

- 含んでいる最も外側の長さ**struct**: おそらく入れ子になったのメンバーである場合または**struct**— 1 つの命令を使用して、現在のアーキテクチャでコピーできる最大サイズを超えています。

キャッシュ不可能な変数としてマークする必要がありますが、プロセッサには、キャッシュ不可能なメモリ アクセス並べ替えされません、**volatile**コンパイラがメモリを並べ替えるしないことを保証するためにアクセスします。

として宣言されているオブジェクト**volatile**その値は、いつでもでも変更できるため、特定の最適化では使用されません。  システムは、以前の命令で同じオブジェクトの値が要求されていても、常に volatile オブジェクトの現在の値を、要求されたときに読み取ります。  また、オブジェクトの値は、代入時にすぐに書き込まれます。

## <a name="iso-compliant"></a>ISO 準拠 →

慣れている場合、 C# volatile キーワード、またはの動作に慣れて**volatile**以前のバージョンの MicrosoftC++コンパイラ (MSVC) がありますが、C++ 11 ISO 標準**volatile**キーワードは異なっており、MSVC のサポートは、ときに、 [/volatile:iso](../build/reference/volatile-volatile-keyword-interpretation.md)コンパイラ オプションを指定します。 ARM では、このオプションが既定で指定されています。 **volatile**; ハードウェアへのアクセスにのみ使用する C++11 ISO 標準コードのキーワードは、スレッド間通信に使用しないでください。 スレッド間通信には、 [ C++標準ライブラリ](../standard-library/cpp-standard-library-reference.md)の[std:: atomic\<t >](../standard-library/atomic.md)などの機構を使用します。

## <a name="end-of-iso-compliant"></a>END ISO 準拠

**Microsoft 固有の仕様**

**/Volatile: ms**コンパイラオプションが使用されている場合 (ARM 以外のアーキテクチャが対象となっている場合、既定では、コンパイラは、他のグローバルオブジェクトへの参照の順序を維持するだけでなく、揮発性オブジェクトへの参照の順序を維持するために追加のコードを生成します。 特に次の点に注意してください。

- volatile オブジェクトへの書き込み (volatile 書き込み) は、解放セマンティクスを持っています。つまり、命令シーケンスで volatile オブジェクトへの書き込み前に発生するグローバル オブジェクトまたは静的オブジェクトへの参照は、コンパイルされたバイナリでの volatile 書き込みの前に発生します。

- volatile オブジェクトの読み取り (volatile 読み取り) は、取得セマンティクスを持っています。つまり、命令シーケンスで volatile メモリの読み取り後に発生するグローバル オブジェクトまたは静的オブジェクトへの参照は、コンパイルされたバイナリでの volatile 読み取りの後に発生します。

これによって、マルチスレッド アプリケーションでのメモリのロックと解放に volatile オブジェクトを使用できるようになります。

> [!NOTE]
>  **/Volatile: ms**コンパイラオプションの使用時に提供される強化された保証に依存する場合、コードは移植できません。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>参照

[キーワード](../cpp/keywords-cpp.md)<br/>
[const](../cpp/const-cpp.md)<br/>
[const ポインターと volatile ポインター](../cpp/const-and-volatile-pointers.md)