---
title: ARM64 組み込み
description: Microsoft C++コンパイラでサポートされている ARM64 組み込みの一覧。
f1_keywords:
- __break
- __addx18byte
- __addx18word
- __addx18dword
- __addx18qword
- __cas8
- __cas16
- __cas32
- __cas64
- __casa8
- __casa16
- __casa32
- __casa64
- __casl8
- __casl16
- __casl32
- __casl64
- __casal8
- __casal16
- __casal32
- __casal64
- __crc32b
- __crc32h
- __crc32w
- __crc32d
- __crc32cb
- __crc32ch
- __crc32cw
- __crc32cd
- __getReg
- __getRegFp
- __getCallerReg
- __getCallerRegFp
- __hlt
- __incx18byte
- __incx18word
- __incx18dword
- __incx18qword
- __ldar8
- __ldar16
- __ldar32
- __ldar64
- __ldapr8
- __ldapr16
- __ldapr32
- __ldapr64
- __prefetch2
- __readx18byte
- __readx18word
- __readx18dword
- __readx18qword
- __setReg
- __setRegFp
- __setCallerReg
- __setCallerRegFp
- __stlr8
- __stlr16
- __stlr32
- __stlr64
- __swp8
- __swp16
- __swp32
- __swp64
- __swpa8
- __swpa16
- __swpa32
- __swpa64
- __swpl8
- __swpl16
- __swpl32
- __swpl64
- __swpal8
- __swpal16
- __swpal32
- __swpal64
- __sys
- __svc
- __writex18byte
- __writex18word
- __writex18dword
- __writex18qword
author: sigatrev
ms.author: magardn
ms.date: 11/14/2019
ms.openlocfilehash: 30881c2b45714f91bf9035819b11ae41322b7086
ms.sourcegitcommit: e805200eaef4fe7a65a00051bbd305273af94fe7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2019
ms.locfileid: "74163683"
---
# <a name="arm64-intrinsics"></a>ARM64 組み込み

Microsoft C++コンパイラ (MSVC) を使用すると、次の組み込みが ARM64 アーキテクチャで利用できるようになります。 ARM の詳細については、 [Arm 開発者ドキュメント](https://developer.arm.com/docs)web サイトのアーキテクチャとソフトウェア開発ツールに関するセクションを参照してください。

## <a name="top"></a>NEON

ARM64 のネオンベクター命令セット拡張は、Single Instruction Multiple Data (SIMD) 機能を提供します。 これらは、x86 および x64 アーキテクチャのプロセッサに共通する MMX および SSE ベクター命令セットのものに似ています。

ヘッダーファイル*arm64_neon .h*に指定されているように、ネオン組み込みがサポートされています。 MSVC のネオン組み込みのサポートは、ARM64 コンパイラのものに似ています。これは、arm のインフォ web サイトの[ARM ネオン組み込みリファレンス](https://static.docs.arm.com/ihi0073/c/IHI0073C_arm_neon_intrinsics_ref.pdf)に記載されています。

##  <a name="A"></a>ARM64 固有の組み込みリスト

|[関数名]|命令|関数プロトタイプ|
|-------------------|-----------------|------------------------|
|__break|BRK|void __break (int)|
|__addx18byte||void __addx18byte (unsigned long、unsigned char)|
|__addx18word||void __addx18word (unsigned long、unsigned short)|
|__addx18dword||void __addx18dword (unsigned long、unsigned long)|
|__addx18qword||void __addx18qword (unsigned long、unsigned __int64)|
|__cas8|CASB|署名されていない __int8 __cas8 (符号なし __int8 volatile * _Target、署名されていない __int8 _Comp、署名されていない __int8 _Value)|
|__cas16|代金|署名されていない __int16 __cas16 (符号なし __int16 volatile * _Target、署名されていない __int16 _Comp、署名されていない __int16 _Value)|
|__cas32|CAS|署名されていない __int32 __cas32 (符号なし __int32 volatile * _Target、署名されていない __int32 _Comp、署名されていない __int32 _Value)|
|__cas64|CAS|署名されていない __int64 __cas64 (符号なし __int64 volatile * _Target、署名されていない __int64 _Comp、署名されていない __int64 _Value)|
|__casa8|CASAB|署名されていない __int8 __casa8 (符号なし __int8 volatile * _Target、署名されていない __int8 _Comp、署名されていない __int8 _Value)|
|__casa16|CASAH|署名されていない __int16 __casa16 (符号なし __int16 volatile * _Target、署名されていない __int16 _Comp、署名されていない __int16 _Value)|
|__casa32|CASA|署名されていない __int32 __casa32 (符号なし __int32 volatile * _Target、署名されていない __int32 _Comp、署名されていない __int32 _Value)|
|__casa64|CASA|署名されていない __int64 __casa64 (符号なし __int64 volatile * _Target、署名されていない __int64 _Comp、署名されていない __int64 _Value)|
|__casl8|CASLB|署名されていない __int8 __casl8 (符号なし __int8 volatile * _Target、署名されていない __int8 _Comp、署名されていない __int8 _Value)|
|__casl16|CASLH|署名されていない __int16 __casl16 (符号なし __int16 volatile * _Target、署名されていない __int16 _Comp、署名されていない __int16 _Value)|
|__casl32|CASL|署名されていない __int32 __casl32 (符号なし __int32 volatile * _Target、署名されていない __int32 _Comp、署名されていない __int32 _Value)|
|__casl64|CASL|署名されていない __int64 __casl64 (符号なし __int64 volatile * _Target、署名されていない __int64 _Comp、署名されていない __int64 _Value)|
|__casal8|CASALB|署名されていない __int8 __casal8 (符号なし __int8 volatile * _Target、署名されていない __int8 _Comp、署名されていない __int8 _Value)|
|__casal16|CASALH|署名されていない __int16 __casal16 (符号なし __int16 volatile * _Target、署名されていない __int16 _Comp、署名されていない __int16 _Value)|
|__casal32|CASAL|署名されていない __int32 __casal32 (符号なし __int32 volatile * _Target、署名されていない __int32 _Comp、署名されていない __int32 _Value)|
|__casal64|CASAL|署名されていない __int64 __casal64 (符号なし __int64 volatile * _Target、署名されていない __int64 _Comp、署名されていない __int64 _Value)|
|__crc32b|CRC32B|署名されていない __int32 __crc32b (unsigned __int32、署名されていない __int32)|
|__crc32h|CRC32H|署名されていない __int32 __crc32h (unsigned __int32、署名されていない __int32)|
|__crc32w|CRC32W|署名されていない __int32 __crc32w (unsigned __int32、署名されていない __int32)|
|__crc32d|CRC32X|署名されていない __int32 __crc32d (unsigned __int32、署名されていない __int64)|
|__crc32cb|CRC32CB|署名されていない __int32 __crc32cb (unsigned __int32、署名されていない __int32)|
|__crc32ch|CRC32CH|署名されていない __int32 __crc32ch (unsigned __int32、署名されていない __int32)|
|__crc32cw|CRC32CW|署名されていない __int32 __crc32cw (unsigned __int32、署名されていない __int32)|
|__crc32cd|CRC32CX|署名されていない __int32 __crc32cd (unsigned __int32、署名されていない __int64)|
|__dmb|DMB|void __dmb(unsigned int `_Type`)<br /><br /> 命令ストリームにメモリ バリア操作を挿入します。 パラメーター `_Type` で、バリアによって適用される制限の種類を指定します。<br /><br /> 適用できる制限の種類の詳細については、「[メモリバリアの制限](#BarrierRestrictions)」を参照してください。|
|__dsb|DSB|void __dsb(unsigned int _Type)<br /><br /> 命令ストリームにメモリ バリア操作を挿入します。 パラメーター `_Type` で、バリアによって適用される制限の種類を指定します。<br /><br /> 適用できる制限の種類の詳細については、「[メモリバリアの制限](#BarrierRestrictions)」を参照してください。|
|__isb|ISB|void __isb(unsigned int _Type)<br /><br /> 命令ストリームにメモリ バリア操作を挿入します。 パラメーター `_Type` で、バリアによって適用される制限の種類を指定します。<br /><br /> 適用できる制限の種類の詳細については、「[メモリバリアの制限](#BarrierRestrictions)」を参照してください。|
|__getReg||unsigned __int64 __getReg (int)|
|__getRegFp||double __getRegFp (int)|
|__getCallerReg||unsigned __int64 __getCallerReg (int)|
|__getCallerRegFp||double __getCallerRegFp (int)|
|__hvc|HVC|unsigned int __hvc(unsigned int, ...)|
|__hlt|HLT|int __hlt (符号なし int,...)|
|__incx18byte||void __incx18byte (unsigned long)|
|__incx18word||void __incx18word (unsigned long)|
|__incx18dword||void __incx18dword (unsigned long)|
|__incx18qword||void __incx18qword (unsigned long)|
|__iso_volatile_load16||__int16 \__iso_volatile_load16 (const volatile \__int16 \*)<br /><br /> 詳細については、「 [__iso_volatile_load/ストアの組み込み](#IsoVolatileLoadStore)」を参照してください。|
|__iso_volatile_load32||__int32 \__iso_volatile_load32 (const volatile \__int32 \*)<br /><br /> 詳細については、「 [__iso_volatile_load/ストアの組み込み](#IsoVolatileLoadStore)」を参照してください。|
|__iso_volatile_load64||__int64 \__iso_volatile_load64 (const volatile \__int64 \*)<br /><br /> 詳細については、「 [__iso_volatile_load/ストアの組み込み](#IsoVolatileLoadStore)」を参照してください。|
|__iso_volatile_load8||__int8 \__iso_volatile_load8 (const volatile \__int8 \*)<br /><br /> 詳細については、「 [__iso_volatile_load/ストアの組み込み](#IsoVolatileLoadStore)」を参照してください。|
|__iso_volatile_store16||void __iso_volatile_store16 (volatile \__int16 \*、\__int16)<br /><br /> 詳細については、「 [__iso_volatile_load/ストアの組み込み](#IsoVolatileLoadStore)」を参照してください。|
|__iso_volatile_store32||void __iso_volatile_store32 (volatile \__int32 \*、\__int32)<br /><br /> 詳細については、「 [__iso_volatile_load/ストアの組み込み](#IsoVolatileLoadStore)」を参照してください。|
|__iso_volatile_store64||void __iso_volatile_store64 (volatile \__int64 \*、\__int64)<br /><br /> 詳細については、「 [__iso_volatile_load/ストアの組み込み](#IsoVolatileLoadStore)」を参照してください。|
|__iso_volatile_store8||void __iso_volatile_store8 (volatile \__int8 \*、\__int8)<br /><br /> 詳細については、「 [__iso_volatile_load/ストアの組み込み](#IsoVolatileLoadStore)」を参照してください。|
|__ldar8|LDARB|署名されていない __int8 __ldar8 (unsigned __int8 volatile * _Target)|
|__ldar16|LDARH|署名されていない __int16 __ldar16 (unsigned __int16 volatile * _Target)|
|__ldar32|LDAR|署名されていない __int32 __ldar32 (unsigned __int32 volatile * _Target)|
|__ldar64|LDAR|署名されていない __int64 __ldar64 (unsigned __int64 volatile * _Target)|
|__ldapr8|LDAPRB|署名されていない __int8 __ldapr8 (unsigned __int8 volatile * _Target)|
|__ldapr16|LDAPRH|署名されていない __int16 __ldapr16 (unsigned __int16 volatile * _Target)|
|__ldapr32|LDAPR|署名されていない __int32 __ldapr32 (unsigned __int32 volatile * _Target)|
|__ldapr64|LDAPR|署名されていない __int64 __ldapr64 (unsigned __int64 volatile * _Target)|
|__mulh||\__int64 __mulh (\__int64、\__int64)|
|__prefetch|PRFM|void __cdecl \__prefetch (const void \*)<br /><br /> プリフェッチ操作に `PRFM` メモリヒントを提供します。この操作は、指定されたアドレスに近いか、指定したアドレス付近にあるメモリが間もなくアクセスされる可能性があることをシステムに `PLDL1KEEP` します。 システムによっては、実行時のパフォーマンスを向上させるために、そのメモリへのアクセス パターンを最適化する場合があります。 ただし、C++ 言語側からすると、この関数には目に見える効果がなく、何も実行しないことがあります。|
|__prefetch2|PRFM|void __cdecl \__prefetch (const void \*、uint8_t prfop)<br /><br /> 指定されたプリフェッチ操作を使用した `PRFM` メモリヒントをシステムに提供します。この操作は、指定したアドレスの前後のメモリが間もなくアクセスされる可能性があります。 システムによっては、実行時のパフォーマンスを向上させるために、そのメモリへのアクセス パターンを最適化する場合があります。 ただし、C++ 言語側からすると、この関数には目に見える効果がなく、何も実行しないことがあります。|
|__readx18byte||unsigned char __readx18byte (unsigned long)|
|__readx18word||unsigned short __readx18word (unsigned long)|
|__readx18dword||unsigned long __readx18dword (unsigned long)|
|__readx18qword||符号なし __int64 __readx18qword (unsigned long)|
|__setReg||void __setReg (int、unsigned __int64)|
|__setRegFp||void __setRegFp (int, double)|
|__setCallerReg||void __setCallerReg (int、unsigned __int64)|
|__setCallerRegFp||void __setCallerRegFp (int, double)|
|__sev|SEV|void __sev(void)|
|__static_assert||void __static_assert (int, const char \*)|
|__stlr8|STLRB|void __stlr8 (符号なし __int8 volatile * _Target、署名されていない __int8 _Value)|
|__stlr16|STLRH|void __stlr16 (符号なし __int16 volatile * _Target、署名されていない __int16 _Value)|
|__stlr32|STLR|void __stlr32 (符号なし __int32 volatile * _Target、署名されていない __int32 _Value)|
|__stlr64|STLR|void __stlr64 (符号なし __int64 volatile * _Target、署名されていない __int64 _Value)|
|__swp8|SWPB|署名されていない __int8 __swp8 (符号なし __int8 volatile * _Target、署名されていない __int8 _Value)|
|__swp16|SWPH|署名されていない __int16 __swp16 (符号なし __int16 volatile * _Target、署名されていない __int16 _Value)|
|__swp32|SWP|署名されていない __int32 __swp32 (符号なし __int32 volatile * _Target、署名されていない __int32 _Value)|
|__swp64|SWP|署名されていない __int64 __swp64 (符号なし __int64 volatile * _Target、署名されていない __int64 _Value)|
|__swpa8|SWPAB|署名されていない __int8 __swpa8 (符号なし __int8 volatile * _Target、署名されていない __int8 _Value)|
|__swpa16|SWPAH|署名されていない __int16 __swpa16 (符号なし __int16 volatile * _Target、署名されていない __int16 _Value)|
|__swpa32|SWPA|署名されていない __int32 __swpa32 (符号なし __int32 volatile * _Target、署名されていない __int32 _Value)|
|__swpa64|SWPA|署名されていない __int64 __swpa64 (符号なし __int64 volatile * _Target、署名されていない __int64 _Value)|
|__swpl8|SWPLB|署名されていない __int8 __swpl8 (符号なし __int8 volatile * _Target、署名されていない __int8 _Value)|
|__swpl16|SWPLH|署名されていない __int16 __swpl16 (符号なし __int16 volatile * _Target、署名されていない __int16 _Value)|
|__swpl32|SWPL|署名されていない __int32 __swpl32 (符号なし __int32 volatile * _Target、署名されていない __int32 _Value)|
|__swpl64|SWPL|署名されていない __int64 __swpl64 (符号なし __int64 volatile * _Target、署名されていない __int64 _Value)|
|__swpal8|SWPALB|署名されていない __int8 __swpal8 (符号なし __int8 volatile * _Target、署名されていない __int8 _Value)|
|__swpal16|SWPALH|署名されていない __int16 __swpal16 (符号なし __int16 volatile * _Target、署名されていない __int16 _Value)|
|__swpal32|SWPAL|署名されていない __int32 __swpal32 (符号なし __int32 volatile * _Target、署名されていない __int32 _Value)|
|__swpal64|SWPAL|署名されていない __int64 __swpal64 (符号なし __int64 volatile * _Target、署名されていない __int64 _Value)|
|__sys|SYS.DATABASES|unsigned int __sys (int, __int64)|
|__svc|SVC|unsigned int __svc (符号なし int,...)|
|__wfe|WFE|void __wfe(void)|
|__wfi|WFI|void __wfi(void)|
|__writex18byte||void __writex18byte (unsigned long、unsigned char)|
|__writex18word||void __writex18word (unsigned long、unsigned short)|
|__writex18dword||void __writex18dword (unsigned long、unsigned long)|
|__writex18qword||void __writex18qword (unsigned long、unsigned __int64)|
|__umulh||署名されていない \__int64 __umulh (署名されていない \__int64、署名されていない \__int64)|
|_CopyDoubleFromInt64||double _CopyDoubleFromInt64 (\__int64)|
|_CopyFloatFromInt32||float _CopyFloatFromInt32 (\__int32)|
|_CopyInt32FromFloat||__int32 _CopyInt32FromFloat(float)|
|_CopyInt64FromDouble||__int64 _CopyInt64FromDouble(double)|
|_CountLeadingOnes||unsigned int _CountLeadingOnes(unsigned long)|
|_CountLeadingOnes64||unsigned int _CountLeadingOnes64 (unsigned \__int64)|
|_CountLeadingSigns||unsigned int _CountLeadingSigns(long)|
|_CountLeadingSigns64||unsigned int _CountLeadingSigns64 (\__int64)|
|_CountLeadingZeros||unsigned int _CountLeadingZeros(unsigned long)|
|_CountLeadingZeros64||unsigned int _CountLeadingZeros64 (unsigned \__int64)|
|_ReadStatusReg|MRS|\__int64 _ReadStatusReg (int)|
|_WriteStatusReg|MSR|void _WriteStatusReg (int, \__int64)|

[[トップに戻る](#top)]

###  <a name="BarrierRestrictions"></a>メモリバリアの制限

組み込み関数 `__dmb` (データメモリバリア)、`__dsb` (データ同期バリア)、および `__isb` (命令同期バリア) では、次の定義済みの値を使用して、共有ドメインおよび操作の影響を受けるアクセスの種類に関するメモリバリア制限を指定します。

|制限値|説明|
|-----------------------|-----------------|
|_ARM64_BARRIER_SY|システム全体、読み取りと書き込み。|
|_ARM64_BARRIER_ST|システム全体、書き込みのみ。|
|_ARM64_BARRIER_LD|フルシステム、読み取り専用。|
|_ARM64_BARRIER_ISH|内部共有可能、読み取りと書き込み。|
|_ARM64_BARRIER_ISHST|内部共有可能、書き込みのみ。|
|_ARM64_BARRIER_ISHLD|内部共有可能、読み取り専用。|
|_ARM64_BARRIER_NSH|共有不可、読み取りと書き込み。|
|_ARM64_BARRIER_NSHST|共有不可、書き込みのみ。|
|_ARM64_BARRIER_NSHLD|共有不可、読み取り専用。|
|_ARM64_BARRIER_OSH|外部共有可能、読み取りと書き込み。|
|_ARM64_BARRIER_OSHST|外部共有可能、書き込みのみ。|
|_ARM64_BARRIER_OSHLD|外部共有可能、読み取り専用。|

組み込み `__isb` の場合、現在有効な制限は _ARM64_BARRIER_SY のみです。その他の値はすべて、アーキテクチャによって予約されています。

###  <a name="IsoVolatileLoadStore"></a>__iso_volatile_load/ストア組み込み

これらの組み込み関数は、コンパイラの最適化の対象にならない読み込みと格納を明示的に実行します。

```C
__int16 __iso_volatile_load16(const volatile __int16 * Location);
__int32 __iso_volatile_load32(const volatile __int32 * Location);
__int64 __iso_volatile_load64(const volatile __int64 * Location);
__int8 __iso_volatile_load8(const volatile __int8 * Location);

void __iso_volatile_store16(volatile __int16 * Location, __int16 Value);
void __iso_volatile_store32(volatile __int32 * Location, __int32 Value);
void __iso_volatile_store64(volatile __int64 * Location, __int64 Value);
void __iso_volatile_store8(volatile __int8 * Location, __int8 Value);
```

#### <a name="parameters"></a>パラメーター

*場所*の\
読み取る、または書き込むメモリ位置のアドレスです。

*値*の\
指定したメモリ位置に書き込む値 (ストア組み込みのみ)。

#### <a name="return-value-load-intrinsics-only"></a>戻り値 (組み込みの読み込みのみ)

*Location*によって指定されたメモリ位置の値。

#### <a name="remarks"></a>Remarks

`__iso_volatile_load8/16/32/64` と `__iso_volatile_store8/16/32/64` 組み込みを使用して、コンパイラの最適化の対象になっていないメモリアクセスを明示的に実行できます。 コンパイラは、これらの操作の相対順序を削除、同期、または変更することはできません。 ただし、暗黙的なハードウェアメモリバリアは生成されません。 したがって、ハードウェアでも複数のスレッド間で観察可能なメモリ アクセスの順序が変更される場合があります。 より正確に言うと、これらの組み込みは、 **/volatile: iso**でコンパイルされる次の式と同じです。

```cpp
int a = __iso_volatile_load32(p);    // equivalent to: int a = *(const volatile __int32*)p;
__iso_volatile_store32(p, a);        // equivalent to: *(volatile __int32*)p = a;
```

組み込みは、volatile 変数を格納する volatile ポインターを受け取ることに注意してください。 ただし、volatile ポインターを引数として使用するための要件や推奨事項はありません。 これらの操作のセマンティクスは、通常の非 volatile 型が使用される場合とまったく同じです。

**/Volatile: iso**コマンドライン引数の詳細については、「 [/volatile (volatile キーワードの解釈)](../build/reference/volatile-volatile-keyword-interpretation.md)」を参照してください。

##  <a name="I"></a>ARM64 その他のアーキテクチャからの組み込みのサポート

次の表に、ARM64 プラットフォームでサポートされている他のアーキテクチャの組み込みの一覧を示します。 ARM64 に組み込まれているの動作が他のハードウェアアーキテクチャでの動作と異なる場合は、さらに詳細な情報が記載されています。

|[関数名]|関数プロトタイプ|
|-------------------|------------------------|
|__assume|void __assume(int)|
|__code_seg|void __code_seg (const char \*)|
|__debugbreak|void __cdecl \__debugbreak (void)|
|__fastfail|__declspec (noreturn) void \__fastfail (unsigned int)|
|__nop|void __nop(void)|
|__yield|void __yield (void)**注:** ARM64 プラットフォームでは、この関数は yield 命令を生成します。 この命令は、スレッドが、プログラムに悪影響を及ぼすことなく、(スピンロックなどの) 実行から一時的に中断される可能性があるタスクを実行していることを示します。 これにより、CPU は実行サイクル中に他のタスクを実行し、無駄になる可能性があります。|
|_AddressOfReturnAddress|void \* _AddressOfReturnAddress (void)|
|_BitScanForward|unsigned char _BitScanForward (unsigned long \* _Index、unsigned long _Mask)|
|_BitScanForward64|unsigned char _BitScanForward64 (unsigned long \* _Index、署名されていない __int64 _Mask)|
|_BitScanReverse|unsigned char _BitScanReverse (unsigned long \* _Index、unsigned long _Mask)|
|_BitScanReverse64|unsigned char _BitScanReverse64 (unsigned long \* _Index、署名されていない __int64 _Mask)|
|_bittest|unsigned char _bittest (long const \*、long)|
|_bittest64|unsigned char _bittest64 (__int64 const \*、__int64)|
|_bittestandcomplement|unsigned char _bittestandcomplement (long \*、long)|
|_bittestandcomplement64|unsigned char _bittestandcomplement64 (__int64 \*、__int64)|
|_bittestandreset|unsigned char _bittestandreset (long \*、long)|
|_bittestandreset64|unsigned char _bittestandreset64 (__int64 \*、__int64)|
|_bittestandset|unsigned char _bittestandset (long \*、long)|
|_bittestandset64|unsigned char _bittestandset64 (__int64 \*、__int64)|
|_byteswap_uint64|署名されていない __int64 \__cdecl _byteswap_uint64 (署名されていない \__int64)|
|_byteswap_ulong|unsigned long __cdecl _byteswap_ulong(unsigned long)|
|_byteswap_ushort|unsigned short __cdecl _byteswap_ushort(unsigned short)|
|_disable|void __cdecl _disable (void)**メモ:** ARM64 プラットフォームでは、この関数は命令 `MSR DAIFCLR,#2`を生成します。これは組み込みとしてのみ使用できます。|
|_enable|void __cdecl _enable (void)**メモ:** ARM64 プラットフォームでは、この関数は命令 `MSR DAIFSET,#2`を生成します。これは組み込みとしてのみ使用できます。|
|_lrotl|unsigned long __cdecl _lrotl(unsigned long, int)|
|_lrotr|unsigned long __cdecl _lrotr(unsigned long, int)|
|_ReadBarrier|void _ReadBarrier(void)|
|_ReadWriteBarrier|void _ReadWriteBarrier(void)|
|_ReturnAddress|void \* _ReturnAddress (void)|
|_rotl|unsigned int __cdecl _rotl(unsigned int _Value, int _Shift)|
|_rotl16|unsigned short _rotl16(unsigned short _Value, unsigned char _Shift)|
|_rotl64|署名されていない __int64 \__cdecl _rotl64 (符号なし \__int64 _Value、int _Shift)|
|_rotl8|unsigned char _rotl8(unsigned char _Value, unsigned char _Shift)|
|_rotr|unsigned int __cdecl _rotr(unsigned int _Value, int _Shift)|
|_rotr16|unsigned short _rotr16(unsigned short _Value, unsigned char _Shift)|
|_rotr64|署名されていない __int64 \__cdecl _rotr64 (符号なし \__int64 _Value、int _Shift)|
|_rotr8|unsigned char _rotr8(unsigned char _Value, unsigned char _Shift)|
|_setjmpex|int __cdecl _setjmpex(jmp_buf)|
|_WriteBarrier|void _WriteBarrier(void)|

[[トップに戻る](#top)]

## <a name="interlocked-intrinsics"></a>インタロック組み込み

インタロックされた組み込みは、アトミックな読み取り/変更/書き込み操作を実行するときに使用する一連の組み込みです。 一部の組み込みは、すべてのプラットフォームに共通です。 これらは、多数存在するため、ここでは個別に一覧表示されています。 これらの定義はほとんど冗長であるため、一般的な用語について考える方が簡単です。 組み込みの名前から、その具体的な動作を推測できます。

次の表は、非ビットテストのインタロックされた組み込みの ARM64 サポートをまとめたものです。 テーブル内の各セルで、行の一番左のセルにある操作名と、列の一番上にある型名を `_Interlocked` の最後に付け加えると、組み込みの名前になります。 たとえば、`Xor` 行と `8` 列の交差部分にあるセルは `_InterlockedXor8` に対応し、完全にサポートされています。 サポートされているほとんどの関数には、オプションのサフィックス `_acq`、`_rel`、および `_nf` が用意されています。 `_acq` サフィックスは "取得" のセマンティクスを示し、`_rel` サフィックスは "解放" のセマンティクスを示します。 `_nf` または "フェンスなし" サフィックスは ARM と ARM64 に固有であり、次のセクションで説明します。

||8|16|32|64|128|P|
|-|-------|--------|--------|--------|-------|-------|
|追加|None|None|完全|完全|None|None|
|および|完全|完全|完全|完全|None|None|
|CompareExchange|完全|完全|完全|完全|完全|完全|
|Decrement|None|完全|完全|完全|None|None|
|Exchange|完全|完全|完全|完全|None|完全|
|ExchangeAdd|完全|完全|完全|完全|None|None|
|インクリメント|None|完全|完全|完全|None|None|
|or|完全|完全|完全|完全|None|None|
|Xor|完全|完全|完全|完全|None|None|

重要:

- **Full**: プレーン、`_acq`、`_rel`、および `_nf` のフォームをサポートします。

- **なし**: サポートされていません

###  <a name="nf_suffix"></a>_nf (フェンスなし) サフィックス

`_nf` または "フェンスなし" サフィックスは、他の3つの形式 (plain、`_acq`、および `_rel`) とは対照的に、操作がどのような種類のメモリバリアとしても動作しないことを示します。これは、すべての種類のバリアとして動作します。 `_nf` フォームの使用方法の1つとして、複数のスレッドによって同時に更新される統計カウンターを保持することがありますが、複数のスレッドを実行している間は値が使用されません。

### <a name="list-of-interlocked-intrinsics"></a>インタロック組み込みのリスト

|[関数名]|関数プロトタイプ|
|-------------------|------------------------|
|_InterlockedAdd|長い _InterlockedAdd (long _volatile \*、long)|
|_InterlockedAdd64|__int64 _InterlockedAdd64 (\__int64 volatile \*、\__int64)|
|_InterlockedAdd64_acq|__int64 _InterlockedAdd64_acq (\__int64 volatile \*、\__int64)|
|_InterlockedAdd64_nf|__int64 _InterlockedAdd64_nf (\__int64 volatile \*、\__int64)|
|_InterlockedAdd64_rel|__int64 _InterlockedAdd64_rel (\__int64 volatile \*、\__int64)|
|_InterlockedAdd_acq|長い _InterlockedAdd_acq (long volatile \*、long)|
|_InterlockedAdd_nf|長い _InterlockedAdd_nf (long volatile \*、long)|
|_InterlockedAdd_rel|長い _InterlockedAdd_rel (long volatile \*、long)|
|_InterlockedAnd|長い _InterlockedAnd (long volatile \*、long)|
|_InterlockedAnd16|短い _InterlockedAnd16 (短い揮発性 \*、短い)|
|_InterlockedAnd16_acq|短い _InterlockedAnd16_acq (短い揮発性 \*、短い)|
|_InterlockedAnd16_nf|短い _InterlockedAnd16_nf (短い揮発性 \*、短い)|
|_InterlockedAnd16_rel|短い _InterlockedAnd16_rel (短い揮発性 \*、短い)|
|_InterlockedAnd64|__int64 _InterlockedAnd64 (\__int64 volatile \*、\__int64)|
|_InterlockedAnd64_acq|__int64 _InterlockedAnd64_acq (\__int64 volatile \*、\__int64)|
|_InterlockedAnd64_nf|__int64 _InterlockedAnd64_nf (\__int64 volatile \*、\__int64)|
|_InterlockedAnd64_rel|__int64 _InterlockedAnd64_rel (\__int64 volatile \*、\__int64)|
|_InterlockedAnd8|char _InterlockedAnd8 (char volatile \*, char)|
|_InterlockedAnd8_acq|char _InterlockedAnd8_acq (char volatile \*, char)|
|_InterlockedAnd8_nf|char _InterlockedAnd8_nf (char volatile \*, char)|
|_InterlockedAnd8_rel|char _InterlockedAnd8_rel (char volatile \*, char)|
|_InterlockedAnd_acq|長い _InterlockedAnd_acq (long volatile \*、long)|
|_InterlockedAnd_nf|長い _InterlockedAnd_nf (long volatile \*、long)|
|_InterlockedAnd_rel|長い _InterlockedAnd_rel (long volatile \*、long)|
|_InterlockedCompareExchange|長い __cdecl _InterlockedCompareExchange (long volatile \*、long、long)|
|_InterlockedCompareExchange_acq|長い _InterlockedCompareExchange_acq (long volatile \*、long、long)|
|_InterlockedCompareExchange_nf|長い _InterlockedCompareExchange_nf (long volatile \*、long、long)|
|_InterlockedCompareExchange_rel|長い _InterlockedCompareExchange_rel (long volatile \*、long、long)|
|_InterlockedCompareExchange16|短い _InterlockedCompareExchange16 (短い volatile \*、short、short)|
|_InterlockedCompareExchange16_acq|短い _InterlockedCompareExchange16_acq (短い volatile \*、short、short)|
|_InterlockedCompareExchange16_nf|短い _InterlockedCompareExchange16_nf (短い volatile \*、short、short)|
|_InterlockedCompareExchange16_rel|短い _InterlockedCompareExchange16_rel (短い volatile \*、short、short)|
|_InterlockedCompareExchange64|__int64 _InterlockedCompareExchange64 (\__int64 volatile \*、\__int64、\__int64)|
|_InterlockedCompareExchange64_acq|__int64 _InterlockedCompareExchange64_acq (\__int64 volatile \*、\__int64、\__int64)|
|_InterlockedCompareExchange64_nf|__int64 _InterlockedCompareExchange64_nf (\__int64 volatile \*、\__int64、\__int64)|
|_InterlockedCompareExchange64_rel|__int64 _InterlockedCompareExchange64_rel (\__int64 volatile \*、\__int64、\__int64)|
|_InterlockedCompareExchange8|char _InterlockedCompareExchange8 (char volatile \*、char、char)|
|_InterlockedCompareExchange8_acq|char _InterlockedCompareExchange8_acq (char volatile \*、char、char)|
|_InterlockedCompareExchange8_nf|char _InterlockedCompareExchange8_nf (char volatile \*、char、char)|
|_InterlockedCompareExchange8_rel|char _InterlockedCompareExchange8_rel (char volatile \*、char、char)|
|_InterlockedCompareExchangePointer|void \* _InterlockedCompareExchangePointer (void \* volatile \*、void \*、void \*)|
|_InterlockedCompareExchangePointer_acq|void \* _InterlockedCompareExchangePointer_acq (void \* volatile \*、void \*、void \*)|
|_InterlockedCompareExchangePointer_nf|void \* _InterlockedCompareExchangePointer_nf (void \* volatile \*、void \*、void \*)|
|_InterlockedCompareExchangePointer_rel|void \* _InterlockedCompareExchangePointer_rel (void \* volatile \*、void \*、void \*)|
|_InterlockedCompareExchange128|unsigned char _InterlockedCompareExchange128 (\__int64 volatile \* _Destination、\__int64 _ExchangeHigh、\__int64 _ExchangeLow、\__int64 \* _ComparandResult)|
|_InterlockedCompareExchange128_acq|unsigned char _InterlockedCompareExchange128_acq (\__int64 volatile \* _Destination、\__int64 _ExchangeHigh、\__int64 _ExchangeLow、\__int64 \* _ComparandResult)|
|_InterlockedCompareExchange128_nf|unsigned char _InterlockedCompareExchange128_nf (\__int64 volatile \* _Destination、\__int64 _ExchangeHigh、\__int64 _ExchangeLow、\__int64 \* _ComparandResult)|
|_InterlockedCompareExchange128_rel|unsigned char _InterlockedCompareExchange128_rel (\__int64 volatile \* _Destination、\__int64 _ExchangeHigh、\__int64 _ExchangeLow、\__int64 \* _ComparandResult)|
|_InterlockedDecrement|長い __cdecl _InterlockedDecrement (長い揮発性 \*)|
|_InterlockedDecrement16|短い _InterlockedDecrement16 (短い揮発性 \*)|
|_InterlockedDecrement16_acq|短い _InterlockedDecrement16_acq (短い揮発性 \*)|
|_InterlockedDecrement16_nf|短い _InterlockedDecrement16_nf (短い揮発性 \*)|
|_InterlockedDecrement16_rel|短い _InterlockedDecrement16_rel (短い揮発性 \*)|
|_InterlockedDecrement64|__int64 _InterlockedDecrement64 (\__int64 volatile \*)|
|_InterlockedDecrement64_acq|__int64 _InterlockedDecrement64_acq (\__int64 volatile \*)|
|_InterlockedDecrement64_nf|__int64 _InterlockedDecrement64_nf (\__int64 volatile \*)|
|_InterlockedDecrement64_rel|__int64 _InterlockedDecrement64_rel (\__int64 volatile \*)|
|_InterlockedDecrement_acq|長い _InterlockedDecrement_acq (長 volatile \*)|
|_InterlockedDecrement_nf|長い _InterlockedDecrement_nf (長 volatile \*)|
|_InterlockedDecrement_rel|長い _InterlockedDecrement_rel (長 volatile \*)|
|_InterlockedExchange|長い __cdecl _InterlockedExchange (long volatile \* _Target、long)|
|_InterlockedExchange_acq|長い _InterlockedExchange_acq (long volatile \* _Target、long)|
|_InterlockedExchange_nf|長い _InterlockedExchange_nf (long volatile \* _Target、long)|
|_InterlockedExchange_rel|長い _InterlockedExchange_rel (long volatile \* _Target、long)|
|_InterlockedExchange16|短い _InterlockedExchange16 (短い揮発性 \* _Target、短い)|
|_InterlockedExchange16_acq|短い _InterlockedExchange16_acq (短い揮発性 \* _Target、短い)|
|_InterlockedExchange16_nf|短い _InterlockedExchange16_nf (短い揮発性 \* _Target、短い)|
|_InterlockedExchange16_rel|短い _InterlockedExchange16_rel (短い揮発性 \* _Target、短い)|
|_InterlockedExchange64|__int64 _InterlockedExchange64 (\__int64 volatile \* _Target、\__int64)|
|_InterlockedExchange64_acq|__int64 _InterlockedExchange64_acq (\__int64 volatile \* _Target、\__int64)|
|_InterlockedExchange64_nf|__int64 _InterlockedExchange64_nf (\__int64 volatile \* _Target、\__int64)|
|_InterlockedExchange64_rel|__int64 _InterlockedExchange64_rel (\__int64 volatile \* _Target、\__int64)|
|_InterlockedExchange8|char _InterlockedExchange8 (char volatile \* _Target、char)|
|_InterlockedExchange8_acq|char _InterlockedExchange8_acq (char volatile \* _Target、char)|
|_InterlockedExchange8_nf|char _InterlockedExchange8_nf (char volatile \* _Target、char)|
|_InterlockedExchange8_rel|char _InterlockedExchange8_rel (char volatile \* _Target、char)|
|_InterlockedExchangeAdd|長い __cdecl _InterlockedExchangeAdd (long volatile \*、long)|
|_InterlockedExchangeAdd16|短い _InterlockedExchangeAdd16 (短い揮発性 \*、短い)|
|_InterlockedExchangeAdd16_acq|短い _InterlockedExchangeAdd16_acq (短い揮発性 \*、短い)|
|_InterlockedExchangeAdd16_nf|短い _InterlockedExchangeAdd16_nf (短い揮発性 \*、短い)|
|_InterlockedExchangeAdd16_rel|短い _InterlockedExchangeAdd16_rel (短い揮発性 \*、短い)|
|_InterlockedExchangeAdd64|__int64 _InterlockedExchangeAdd64 (\__int64 volatile \*、\__int64)|
|_InterlockedExchangeAdd64_acq|__int64 _InterlockedExchangeAdd64_acq (\__int64 volatile \*、\__int64)|
|_InterlockedExchangeAdd64_nf|__int64 _InterlockedExchangeAdd64_nf (\__int64 volatile \*、\__int64)|
|_InterlockedExchangeAdd64_rel|__int64 _InterlockedExchangeAdd64_rel (\__int64 volatile \*、\__int64)|
|_InterlockedExchangeAdd8|char _InterlockedExchangeAdd8 (char volatile \*, char)|
|_InterlockedExchangeAdd8_acq|char _InterlockedExchangeAdd8_acq (char volatile \*, char)|
|_InterlockedExchangeAdd8_nf|char _InterlockedExchangeAdd8_nf (char volatile \*, char)|
|_InterlockedExchangeAdd8_rel|char _InterlockedExchangeAdd8_rel (char volatile \*, char)|
|_InterlockedExchangeAdd_acq|長い _InterlockedExchangeAdd_acq (long volatile \*、long)|
|_InterlockedExchangeAdd_nf|長い _InterlockedExchangeAdd_nf (long volatile \*、long)|
|_InterlockedExchangeAdd_rel|長い _InterlockedExchangeAdd_rel (long volatile \*、long)|
|_InterlockedExchangePointer|void \* _InterlockedExchangePointer (void \* volatile \* _Target、void \*)|
|_InterlockedExchangePointer_acq|void \* _InterlockedExchangePointer_acq (void \* volatile \* _Target、void \*)|
|_InterlockedExchangePointer_nf|void \* _InterlockedExchangePointer_nf (void \* volatile \* _Target、void \*)|
|_InterlockedExchangePointer_rel|void \* _InterlockedExchangePointer_rel (void \* volatile \* _Target、void \*)|
|_InterlockedIncrement|長い __cdecl _InterlockedIncrement (長い揮発性 \*)|
|_InterlockedIncrement16|短い _InterlockedIncrement16 (短い揮発性 \*)|
|_InterlockedIncrement16_acq|短い _InterlockedIncrement16_acq (短い揮発性 \*)|
|_InterlockedIncrement16_nf|短い _InterlockedIncrement16_nf (短い揮発性 \*)|
|_InterlockedIncrement16_rel|短い _InterlockedIncrement16_rel (短い揮発性 \*)|
|_InterlockedIncrement64|__int64 _InterlockedIncrement64 (\__int64 volatile \*)|
|_InterlockedIncrement64_acq|__int64 _InterlockedIncrement64_acq (\__int64 volatile \*)|
|_InterlockedIncrement64_nf|__int64 _InterlockedIncrement64_nf (\__int64 volatile \*)|
|_InterlockedIncrement64_rel|__int64 _InterlockedIncrement64_rel (\__int64 volatile \*)|
|_InterlockedIncrement_acq|長い _InterlockedIncrement_acq (長 volatile \*)|
|_InterlockedIncrement_nf|長い _InterlockedIncrement_nf (長 volatile \*)|
|_InterlockedIncrement_rel|長い _InterlockedIncrement_rel (長 volatile \*)|
|_InterlockedOr|長い _InterlockedOr (long volatile \*、long)|
|_InterlockedOr16|短い _InterlockedOr16 (短い揮発性 \*、短い)|
|_InterlockedOr16_acq|短い _InterlockedOr16_acq (短い揮発性 \*、短い)|
|_InterlockedOr16_nf|短い _InterlockedOr16_nf (短い揮発性 \*、短い)|
|_InterlockedOr16_rel|短い _InterlockedOr16_rel (短い揮発性 \*、短い)|
|_InterlockedOr64|__int64 _InterlockedOr64 (\__int64 volatile \*、\__int64)|
|_InterlockedOr64_acq|__int64 _InterlockedOr64_acq (\__int64 volatile \*、\__int64)|
|_InterlockedOr64_nf|__int64 _InterlockedOr64_nf (\__int64 volatile \*、\__int64)|
|_InterlockedOr64_rel|__int64 _InterlockedOr64_rel (\__int64 volatile \*、\__int64)|
|_InterlockedOr8|char _InterlockedOr8 (char volatile \*, char)|
|_InterlockedOr8_acq|char _InterlockedOr8_acq (char volatile \*, char)|
|_InterlockedOr8_nf|char _InterlockedOr8_nf (char volatile \*, char)|
|_InterlockedOr8_rel|char _InterlockedOr8_rel (char volatile \*, char)|
|_InterlockedOr_acq|長い _InterlockedOr_acq (long volatile \*、long)|
|_InterlockedOr_nf|長い _InterlockedOr_nf (long volatile \*、long)|
|_InterlockedOr_rel|長い _InterlockedOr_rel (long volatile \*、long)|
|_InterlockedXor|長い _InterlockedXor (long volatile \*、long)|
|_InterlockedXor16|短い _InterlockedXor16 (短い揮発性 \*、短い)|
|_InterlockedXor16_acq|短い _InterlockedXor16_acq (短い揮発性 \*、短い)|
|_InterlockedXor16_nf|短い _InterlockedXor16_nf (短い揮発性 \*、短い)|
|_InterlockedXor16_rel|短い _InterlockedXor16_rel (短い揮発性 \*、短い)|
|_InterlockedXor64|__int64 _InterlockedXor64 (\__int64 volatile \*、\__int64)|
|_InterlockedXor64_acq|__int64 _InterlockedXor64_acq (\__int64 volatile \*、\__int64)|
|_InterlockedXor64_nf|__int64 _InterlockedXor64_nf (\__int64 volatile \*、\__int64)|
|_InterlockedXor64_rel|__int64 _InterlockedXor64_rel (\__int64 volatile \*、\__int64)|
|_InterlockedXor8|char _InterlockedXor8 (char volatile \*, char)|
|_InterlockedXor8_acq|char _InterlockedXor8_acq (char volatile \*, char)|
|_InterlockedXor8_nf|char _InterlockedXor8_nf (char volatile \*, char)|
|_InterlockedXor8_rel|char _InterlockedXor8_rel (char volatile \*, char)|
|_InterlockedXor_acq|長い _InterlockedXor_acq (long volatile \*、long)|
|_InterlockedXor_nf|長い _InterlockedXor_nf (long volatile \*、long)|
|_InterlockedXor_rel|長い _InterlockedXor_rel (long volatile \*、long)|

[[トップに戻る](#top)]

### <a name="_interlockedbittest-intrinsics"></a>組み込みの _interlockedbittest

プレーンインタロックされたビットテストの組み込みは、すべてのプラットフォームに共通です。 ARM64、`_rel`、および `_nf` のバリアントを `_acq`追加します。これにより、この記事の「 [_nf (フェンスなし) サフィックス](#nf_suffix)」で説明されているように、操作のバリアセマンティクスを変更するだけです。

|[関数名]|関数プロトタイプ|
|-------------------|------------------------|
|_interlockedbittestandreset|unsigned char _interlockedbittestandreset (long volatile \*、long)|
|_interlockedbittestandreset_acq|unsigned char _interlockedbittestandreset_acq (long volatile \*、long)|
|_interlockedbittestandreset_nf|unsigned char _interlockedbittestandreset_nf (long volatile \*、long)|
|_interlockedbittestandreset_rel|unsigned char _interlockedbittestandreset_rel (long volatile \*、long)|
|_interlockedbittestandreset64|unsigned char _interlockedbittestandreset64 (__int64 volatile \*、__int64)|
|_interlockedbittestandreset64_acq|unsigned char _interlockedbittestandreset64_acq (__int64 volatile \*、__int64)|
|_interlockedbittestandreset64_nf|unsigned char _interlockedbittestandreset64_nf (__int64 volatile \*、__int64)|
|_interlockedbittestandreset64_rel|unsigned char _interlockedbittestandreset64_rel (__int64 volatile \*、__int64)|
|_interlockedbittestandset|unsigned char _interlockedbittestandset (long volatile \*、long)|
|_interlockedbittestandset_acq|unsigned char _interlockedbittestandset_acq (long volatile \*、long)|
|_interlockedbittestandset_nf|unsigned char _interlockedbittestandset_nf (long volatile \*、long)|
|_interlockedbittestandset_rel|unsigned char _interlockedbittestandset_rel (long volatile \*、long)|
|_interlockedbittestandset64|unsigned char _interlockedbittestandset64 (__int64 volatile \*、__int64)|
|_interlockedbittestandset64_acq|unsigned char _interlockedbittestandset64_acq (__int64 volatile \*、__int64)|
|_interlockedbittestandset64_nf|unsigned char _interlockedbittestandset64_nf (__int64 volatile \*、__int64)|
|_interlockedbittestandset64_rel|unsigned char _interlockedbittestandset64_rel (__int64 volatile \*、__int64)|

[[トップに戻る](#top)]

## <a name="see-also"></a>関連項目

[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)\
[ARM 組み込み](arm-intrinsics.md)\
[ARM アセンブラーリファレンス](../assembler/arm/arm-assembler-reference.md)\
[C++言語リファレンス](../cpp/cpp-language-reference.md)
