﻿---
title: x86 組み込み一覧
ms.date: 02/28/2020
helpviewer_keywords:
- cl.exe compiler, intrinsics
- intrinsics, x86
ms.openlocfilehash: 00d10668b791303d7f5f27cacdb1ab8021470ae3
ms.sourcegitcommit: ab8d7b47b63b62892a1256a09b1324a9a136eccf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/02/2020
ms.locfileid: "78215486"
---
# <a name="x86-intrinsics-list"></a>x86 組み込み一覧

このドキュメントでは、x86 が対象にC++なっている場合に Microsoft C/C コンパイラがサポートする組み込みの一覧を示します。

各組み込みの詳細については、対象とするプロセッサに応じて、次の技術情報も参照してください。

- ヘッダー ファイル。 多数の組み込みが、ヘッダー ファイル内のコメント内に文書化されています。

- [Intel Intrinsics Guide](https://software.intel.com/sites/landingpage/IntrinsicsGuide/)。 検索ボックスを使って特定の組み込みを見つけてください。

- [Intel 64 and IA-32 Architectures Software Developer Manuals (インテル 64 および IA-32 アーキテクチャ ソフトウェア デベロッパーズ マニュアル)](https://software.intel.com/articles/intel-sdm)

- [Intel アーキテクチャ命令セット拡張機能プログラミング リファレンス](https://software.intel.com/isa-extensions)

- [Intel Advanced Vector Extensions の概要](https://software.intel.com/articles/introduction-to-intel-advanced-vector-extensions)

- [AMD 開発者ガイド、マニュアル & ISA ドキュメント](https://developer.amd.com/resources/developer-guides-manuals/)

## <a name="x86-intrinsics"></a>x86 組み込み

次の表は、x86 プロセッサで利用可能な組み込みの一覧です。 [テクノロジ] 列に、必要な命令セットのサポートを示します。 [__cpuid](cpuid-cpuidex.md) 組み込みを使用して、実行時に命令セットのサポートを確認します。 1 つの行に 2 つのエントリがある場合は、同じ組み込みに対する異なるエントリ ポイントを表しています。 [1] は、組み込みが AMD プロセッサでのみ利用可能であることを示します。 [2] は、組み込みが Intel プロセッサでのみ利用可能であることを示します。 [3] は、プロトタイプがマクロであることを示します。 関数プロトタイプに必要なヘッダーが "ヘッダー" 列に示されています。 分かりやすくするために、Intrin.h ヘッダーには immintrin.h と ammintrin.h の両方を含めています。

|組み込みの名前|テクノロジ|ヘッダー|関数プロトタイプ|
|--------------------|----------------|------------|------------------------|
|_addcarry_u16||intrin.h|unsigned char _addcarry_u16 (unsigned char、unsigned short、unsigned short、unsigned short \*)|
|[_addcarry_u32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_addcarry_u32)||intrin.h|unsigned char _addcarry_u32 (unsigned char、unsigned int、unsigned int、unsigned int \*)|
|_addcarry_u8||intrin.h|unsigned char _addcarry_u8 (unsigned char、unsigned char、unsigned char、unsigned char \*)|
|[_addcarryx_u32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_addcarryx_u32)|ADX [2]|immintrin.h|unsigned char _addcarryx_u32 (unsigned char、unsigned int、unsigned int、unsigned int \*)|
|[__addfsbyte](addfsbyte-addfsword-addfsdword.md)||intrin.h|void __addfsbyte (unsigned long、unsigned char)|
|[__addfsdword](addfsbyte-addfsword-addfsdword.md)||intrin.h|void __addfsdword (unsigned long、unsigned long)|
|[__addfsword](addfsbyte-addfsword-addfsdword.md)||intrin.h|void __addfsword (unsigned long、unsigned short)|
|[_AddressOfReturnAddress](addressofreturnaddress.md)||intrin.h|void \* _AddressOfReturnAddress (void)|
|[_andn_u32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_andn_u32)|BMI [1]|ammintrin.h|unsigned int _andn_u32(unsigned int, unsigned int)|
|[_bextr_u32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_bextr_u32)|BMI|ammintrin.h, immintrin.h|unsigned int _bextr_u32(unsigned int, unsigned int, unsigned int)|
|_bextri_u32|ABM [1]|ammintrin.h|unsigned int _bextri_u32(unsigned int, unsigned int)|
|[_BitScanForward](bitscanforward-bitscanforward64.md)||intrin.h|unsigned char _BitScanForward (unsigned long\*、unsigned long)|
|[_BitScanReverse](bitscanreverse-bitscanreverse64.md)||intrin.h|unsigned char _BitScanReverse (unsigned long\*、unsigned long)|
|[_bittest](bittest-bittest64.md)||intrin.h|unsigned char _bittest (long const \*、long)|
|[_bittestandcomplement](bittestandcomplement-bittestandcomplement64.md)||intrin.h|unsigned char _bittestandcomplement (long \*、long)|
|[_bittestandreset](bittestandreset-bittestandreset64.md)||intrin.h|unsigned char _bittestandreset (long \*、long)|
|[_bittestandset](bittestandset-bittestandset64.md)||intrin.h|unsigned char _bittestandset (long \*、long)|
|_blcfill_u32|ABM [1]|ammintrin.h|unsigned int _blcfill_u32(unsigned int)|
|_blci_u32|ABM [1]|ammintrin.h|unsigned int _blci_u32(unsigned int)|
|_blcic_u32|ABM [1]|ammintrin.h|unsigned int _blcic_u32(unsigned int)|
|_blcmsk_u32|ABM [1]|ammintrin.h|unsigned int _blcmsk_u32(unsigned int)|
|_blcs_u32|ABM [1]|ammintrin.h|unsigned int _blcs_u32(unsigned int)|
|_blsfill_u32|ABM [1]|ammintrin.h|unsigned int _blsfill_u32(unsigned int)|
|[_blsi_u32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_blsi_u32)|BMI|ammintrin.h, immintrin.h|unsigned int _blsi_u32(unsigned int)|
|_blsic_u32|ABM [1]|ammintrin.h|unsigned int _blsic_u32(unsigned int)|
|[_blsmsk_u32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_blsmsk_u32)|BMI|ammintrin.h, immintrin.h|unsigned int _blsmsk_u32(unsigned int)|
|[_blsr_u32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_blsr_u32)|BMI|ammintrin.h, immintrin.h|unsigned int _blsr_u32(unsigned int)|
|[_bzhi_u32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_bzhi_u32)|BMI [2]|immintrin.h|unsigned int _bzhi_u32(unsigned int, unsigned int)|
|_clac|SMAP|intrin.h|void _clac(void)|
|[__cpuid](cpuid-cpuidex.md)||intrin.h|void __cpuid (int \*, int)|
|[__cpuidex](cpuid-cpuidex.md)||intrin.h|void __cpuidex (int \*, int, int)|
|[__debugbreak](debugbreak.md)||intrin.h|void __debugbreak(void)|
|[_disable](disable.md)||intrin.h|void _disable(void)|
|[_div64](div64.md)||intrin.h| int \_div64 (\__int64、int、int \*)|
|[__emul](emul-emulu.md)||intrin.h|__int64 [pascal/cdecl] \__emul (int, int)|
|[__emulu](emul-emulu.md)||intrin.h|署名されていない __int64 [pascal/cdecl]\__emulu (unsigned int, unsigned int)|
|[_enable](enable.md)||intrin.h|void _enable(void)|
|[__fastfail](fastfail.md)||intrin.h|void __fastfail(unsigned int)|
|[_fxrstor](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_fxrstor)|FXSR [2]|immintrin.h|void _fxrstor (void const\*)|
|[_fxsave](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_fxsave)|FXSR [2]|immintrin.h|void _fxsave (void\*)|
|[__getcallerseflags](getcallerseflags.md)||intrin.h|(unsigned int __getcallerseflags())|
|[__halt](halt.md)||intrin.h|void __halt(void)|
|[__inbyte](inbyte.md)||intrin.h|unsigned char __inbyte(unsigned short)|
|[__inbytestring](inbytestring.md)||intrin.h|void __inbytestring (unsigned short、unsigned char \*、unsigned long)|
|[__incfsbyte](incfsbyte-incfsword-incfsdword.md)||intrin.h|void __incfsbyte(unsigned long)|
|[__incfsdword](incfsbyte-incfsword-incfsdword.md)||intrin.h|void __incfsdword(unsigned long)|
|[__incfsword](incfsbyte-incfsword-incfsdword.md)||intrin.h|void __incfsword(unsigned long)|
|[__indword](indword.md)||intrin.h|unsigned long __indword (unsigned short)|
|[__indwordstring](indwordstring.md)||intrin.h|void __indwordstring (unsigned short、unsigned long \*、unsigned long)|
|[__int2c](int2c.md)||intrin.h|void __int2c(void)|
|[_InterlockedAddLargeStatistic](interlockedaddlargestatistic.md)||intrin.h|長い _InterlockedAddLargeStatistic (\__int64 揮発性 \*、長い)|
|[_InterlockedAnd](interlockedand-intrinsic-functions.md)||intrin.h|長い _InterlockedAnd (long volatile \*、long)|
|[_InterlockedAnd_HLEAcquire](interlockedand-intrinsic-functions.md)|HLE [2]|immintrin.h|長い _InterlockedAnd_HLEAcquire (long volatile \*、long)|
|[_InterlockedAnd_HLERelease](interlockedand-intrinsic-functions.md)|HLE [2]|immintrin.h|長い _InterlockedAnd_HLERelease (long volatile \*、long)|
|[_InterlockedAnd16](interlockedand-intrinsic-functions.md)||intrin.h|短い _InterlockedAnd16 (短い揮発性 \*、短い)|
|[_InterlockedAnd8](interlockedand-intrinsic-functions.md)||intrin.h|char _InterlockedAnd8 (char volatile \*, char)|
|[_interlockedbittestandreset](interlockedbittestandreset-intrinsic-functions.md)||intrin.h|unsigned char _interlockedbittestandreset (long \*、long)|
|[_interlockedbittestandreset_HLEAcquire](interlockedbittestandreset-intrinsic-functions.md)|HLE [2]|immintrin.h|unsigned char _interlockedbittestandreset_HLEAcquire (long \*、long)|
|[_interlockedbittestandreset_HLERelease](interlockedbittestandreset-intrinsic-functions.md)|HLE [2]|immintrin.h|unsigned char _interlockedbittestandreset_HLERelease (long \*、long)|
|[_interlockedbittestandset](interlockedbittestandset-intrinsic-functions.md)||intrin.h|unsigned char _interlockedbittestandset (long \*、long)|
|[_interlockedbittestandset_HLEAcquire](interlockedbittestandset-intrinsic-functions.md)|HLE [2]|immintrin.h|unsigned char _interlockedbittestandset_HLEAcquire (long \*、long)|
|[_interlockedbittestandset_HLERelease](interlockedbittestandset-intrinsic-functions.md)|HLE [2]|immintrin.h|unsigned char _interlockedbittestandset_HLERelease (long \*、long)|
|[_InterlockedCompareExchange](interlockedcompareexchange-intrinsic-functions.md)||intrin.h|長い _InterlockedCompareExchange (long volatile \*、long、long)|
|[_InterlockedCompareExchange_HLEAcquire](interlockedcompareexchange-intrinsic-functions.md)|HLE [2]|immintrin.h|長い _InterlockedCompareExchange_HLEAcquire (long volatile \*、long、long)|
|[_InterlockedCompareExchange_HLERelease](interlockedcompareexchange-intrinsic-functions.md)|HLE [2]|immintrin.h|長い _InterlockedCompareExchange_HLERelease (long volatile \*、long、long)|
|[_InterlockedCompareExchange16](interlockedcompareexchange-intrinsic-functions.md)||intrin.h|短い _InterlockedCompareExchange16 (短い volatile \*、short、short)|
|[_InterlockedCompareExchange64](interlockedcompareexchange-intrinsic-functions.md)||intrin.h|__int64 _InterlockedCompareExchange64 (\__int64 volatile \*、\__int64、\__int64)|
|[_InterlockedCompareExchange64_HLEAcquire](interlockedcompareexchange-intrinsic-functions.md)|HLE [2]|immintrin.h|__int64 _InterlockedCompareExchange64_HLEAcquire (\__int64 volatile \*、\__int64、\__int64)|
|[_InterlockedCompareExchange64_HLERelease](interlockedcompareexchange-intrinsic-functions.md)|HLE [2]|immintrin.h|__int64 _InterlockedCompareExchange64_HLERelease (\__int64 volatile \*、\__int64、\__int64)|
|[_InterlockedCompareExchange8](interlockedcompareexchange-intrinsic-functions.md)||intrin.h|char _InterlockedCompareExchange8 (char volatile \*、char、char)|
|[_InterlockedCompareExchangePointer](interlockedcompareexchangepointer-intrinsic-functions.md)||intrin.h|void \*_InterlockedCompareExchangePointer (void \*volatile \*、void \*、void \*)|
|[_InterlockedCompareExchangePointer_HLEAcquire](interlockedcompareexchangepointer-intrinsic-functions.md)|HLE [2]|immintrin.h|void \*_InterlockedCompareExchangePointer_HLEAcquire (void \*volatile \*、void \*、void \*)|
|[_InterlockedCompareExchangePointer_HLERelease](interlockedcompareexchangepointer-intrinsic-functions.md)|HLE [2]|immintrin.h|void \*_InterlockedCompareExchangePointer_HLERelease (void \*volatile \*、void \*、void \*)|
|[_InterlockedDecrement](interlockeddecrement-intrinsic-functions.md)||intrin.h|長い _InterlockedDecrement (長 volatile \*)|
|[_InterlockedDecrement16](interlockeddecrement-intrinsic-functions.md)||intrin.h|短い _InterlockedDecrement16 (短い揮発性 \*)|
|[_InterlockedExchange](interlockedexchange-intrinsic-functions.md)||intrin.h|長い _InterlockedExchange (long volatile \*、long)|
|[_InterlockedExchange_HLEAcquire](interlockedexchange-intrinsic-functions.md)|HLE [2]|immintrin.h|長い _InterlockedExchange_HLEAcquire (long volatile \*、long)|
|[_InterlockedExchange_HLERelease](interlockedexchange-intrinsic-functions.md)|HLE [2]|immintrin.h|長い _InterlockedExchange_HLERelease (long volatile \*、long)|
|[_InterlockedExchange16](interlockedexchange-intrinsic-functions.md)||intrin.h|短い _InterlockedExchange16 (短い揮発性 \*、短い)|
|[_InterlockedExchange8](interlockedexchange-intrinsic-functions.md)||intrin.h|char _InterlockedExchange8 (char volatile \*, char)|
|[_InterlockedExchangeAdd](interlockedexchangeadd-intrinsic-functions.md)||intrin.h|長い _InterlockedExchangeAdd (long volatile \*、long)|
|[_InterlockedExchangeAdd_HLEAcquire](interlockedexchangeadd-intrinsic-functions.md)|HLE [2]|immintrin.h|長い _InterlockedExchangeAdd_HLEAcquire (long volatile \*、long)|
|[_InterlockedExchangeAdd_HLERelease](interlockedexchangeadd-intrinsic-functions.md)|HLE [2]|immintrin.h|長い _InterlockedExchangeAdd_HLERelease (long volatile \*、long)|
|[_InterlockedExchangeAdd16](interlockedexchangeadd-intrinsic-functions.md)||intrin.h|short _InterlockedExchangeAdd16(short volatile *, short)|
|[_InterlockedExchangeAdd8](interlockedexchangeadd-intrinsic-functions.md)||intrin.h|char _InterlockedExchangeAdd8 (char volatile \*, char)|
|[_InterlockedExchangePointer](interlockedexchangepointer-intrinsic-functions.md)||intrin.h|void \* _InterlockedExchangePointer (void \*volatile \*、void \*)|
|[_InterlockedExchangePointer_HLEAcquire](interlockedexchangepointer-intrinsic-functions.md)|HLE [2]|immintrin.h|void \* _InterlockedExchangePointer_HLEAcquire (void \*volatile \*、void \*)|
|[_InterlockedExchangePointer_HLERelease](interlockedexchangepointer-intrinsic-functions.md)|HLE [2]|immintrin.h|void \* _InterlockedExchangePointer_HLERelease (void \*volatile \*、void \*)|
|[_InterlockedIncrement](interlockedincrement-intrinsic-functions.md)||intrin.h|長い _InterlockedIncrement (長 volatile \*)|
|[_InterlockedIncrement16](interlockedincrement-intrinsic-functions.md)||intrin.h|短い _InterlockedIncrement16 (短い揮発性 \*)|
|[_InterlockedOr](interlockedor-intrinsic-functions.md)||intrin.h|長い _InterlockedOr (long volatile \*、long)|
|[_InterlockedOr_HLEAcquire](interlockedor-intrinsic-functions.md)|HLE [2]|immintrin.h|長い _InterlockedOr_HLEAcquire (long volatile \*、long)|
|[_InterlockedOr_HLERelease](interlockedor-intrinsic-functions.md)|HLE [2]|immintrin.h|長い _InterlockedOr_HLERelease (long volatile \*、long)|
|[_InterlockedOr16](interlockedor-intrinsic-functions.md)||intrin.h|短い _InterlockedOr16 (短い揮発性 \*、短い)|
|[_InterlockedOr8](interlockedor-intrinsic-functions.md)||intrin.h|char _InterlockedOr8 (char volatile \*, char)|
|[_InterlockedXor](interlockedxor-intrinsic-functions.md)||intrin.h|長い _InterlockedXor (long volatile \*、long)|
|[_InterlockedXor_HLEAcquire](interlockedxor-intrinsic-functions.md)|HLE [2]|immintrin.h|長い _InterlockedXor_HLEAcquire (long volatile \*、long)|
|[_InterlockedXor_HLERelease](interlockedxor-intrinsic-functions.md)|HLE [2]|immintrin.h|長い _InterlockedXor_HLERelease (long volatile \*、long)|
|[_InterlockedXor16](interlockedxor-intrinsic-functions.md)||intrin.h|短い _InterlockedXor16 (短い揮発性 \*、短い)|
|[_InterlockedXor8](interlockedxor-intrinsic-functions.md)||intrin.h|char _InterlockedXor8 (char volatile \*, char)|
|[__invlpg](invlpg.md)||intrin.h|void __invlpg (void\*)|
|[_invpcid](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_invpcid)|INVPCID [2]|immintrin.h|void _invpcid (unsigned int, void \*)|
|[__inword](inword.md)||intrin.h|unsigned short __inword (unsigned short)|
|[__inwordstring](inwordstring.md)||intrin.h|void __inwordstring (unsigned short、unsigned short \*、unsigned long)|
|_lgdt||intrin.h|void _lgdt (void\*)|
|[__lidt](lidt.md)||intrin.h|void __lidt (void\*)|
|[__ll_lshift](ll-lshift.md)||intrin.h|署名されていない __int64 [pascal/cdecl] \__ll_lshift (符号なし \__int64, int)|
|[__ll_rshift](ll-rshift.md)||intrin.h|__int64 [pascal/cdecl] \__ll_rshift (\__int64, int)|
|_load_be_u16<br /><br /> [_loadbe_i16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_loadbe_i16&expand=3071)|MOVBE|immintrin.h|unsigned short _load_be_u16 (void const\*);<br /><br /> short _loadbe_i16 (void const\*);番|
|_load_be_u32<br /><br /> [_loadbe_i32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_loadbe_i32&expand=3072)|MOVBE|immintrin.h|unsigned int _load_be_u32 (void const\*);<br /><br /> int _loadbe_i32 (void const\*);番|
|__llwpcb|LWP [1]|ammintrin.h|void __llwpcb (void \*)|
|__lwpins32|LWP [1]|ammintrin.h|unsigned char __lwpins32 (符号なし整数、符号なし整数、符号なし int)|
|__lwpval32|LWP [1]|ammintrin.h|void __lwpval32 (符号なし整数、符号なし整数、符号なし int)|
|[__lzcnt](lzcnt16-lzcnt-lzcnt64.md)|LZCNT|intrin.h|unsigned int __lzcnt(unsigned int)|
|[_lzcnt_u32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_lzcnt_u32)|BMI|ammintrin.h, immintrin.h|unsigned int _lzcnt_u32(unsigned int)|
|[__lzcnt16](lzcnt16-lzcnt-lzcnt64.md)|LZCNT|intrin.h|unsigned short __lzcnt16(unsigned short)|
|[_m_empty](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_empty)|MMX|intrin.h|void _m_empty(void)|
|_m_femms|3DNOW|intrin.h|void _m_femms(void)|
|_m_from_float|3DNOW|intrin.h|__m64 _m_from_float(float)|
|[_m_from_int](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_from_int)|MMX|intrin.h|__m64 _m_from_int(int)|
|[_m_maskmovq](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_maskmovq)|SSE|intrin.h|void _m_maskmovq (\__m64、\__m64、char\*)|
|[_m_packssdw](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_packssdw)|MMX|intrin.h|__m64 _m_packssdw (\__m64、\__m64)|
|[_m_packsswb](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_packsswb)|MMX|intrin.h|__m64 _m_packsswb (\__m64、\__m64)|
|[_m_packuswb](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_packuswb)|MMX|intrin.h|__m64 _m_packuswb (\__m64、\__m64)|
|[_m_paddb](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_paddb)|MMX|intrin.h|__m64 _m_paddb (\__m64、\__m64)|
|[_m_paddd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_paddd)|MMX|intrin.h|__m64 _m_paddd (\__m64、\__m64)|
|[_m_paddsb](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_paddsb)|MMX|intrin.h|__m64 _m_paddsb (\__m64、\__m64)|
|[_m_paddsw](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_paddsw)|MMX|intrin.h|__m64 _m_paddsw (\__m64、\__m64)|
|[_m_paddusb](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_paddusb)|MMX|intrin.h|__m64 _m_paddusb (\__m64、\__m64)|
|[_m_paddusw](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_paddusw)|MMX|intrin.h|__m64 _m_paddusw (\__m64、\__m64)|
|[_m_paddw](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_paddw)|MMX|intrin.h|__m64 _m_paddw (\__m64、\__m64)|
|[_m_pand](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_pand)|MMX|intrin.h|__m64 _m_pand (\__m64、\__m64)|
|[_m_pandn](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_pandn)|MMX|intrin.h|__m64 _m_pandn (\__m64、\__m64)|
|[_m_pavgb](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_pavgb)|SSE|intrin.h|__m64 _m_pavgb (\__m64、\__m64)|
|_m_pavgusb|3DNOW|intrin.h|__m64 _m_pavgusb (\__m64、\__m64)|
|[_m_pavgw](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_pavgw)|SSE|intrin.h|__m64 _m_pavgw (\__m64、\__m64)|
|[_m_pcmpeqb](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_pcmpeqb)|MMX|intrin.h|__m64 _m_pcmpeqb (\__m64、\__m64)|
|[_m_pcmpeqd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_pcmpeqd)|MMX|intrin.h|__m64 _m_pcmpeqd (\__m64、\__m64)|
|[_m_pcmpeqw](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_pcmpeqw)|MMX|intrin.h|__m64 _m_pcmpeqw (\__m64、\__m64)|
|[_m_pcmpgtb](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_pcmpgtb)|MMX|intrin.h|__m64 _m_pcmpgtb (\__m64、\__m64)|
|[_m_pcmpgtd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_pcmpgtd)|MMX|intrin.h|__m64 _m_pcmpgtd (\__m64、\__m64)|
|[_m_pcmpgtw](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_pcmpgtw)|MMX|intrin.h|__m64 _m_pcmpgtw (\__m64、\__m64)|
|[_m_pextrw](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_pextrw)|SSE|intrin.h|int _m_pextrw (\__m64、int)|
|_m_pf2id|3DNOW|intrin.h|__m64 _m_pf2id (\__m64)|
|_m_pf2iw|3DNOWEXT|intrin.h|__m64 _m_pf2iw (\__m64)|
|_m_pfacc|3DNOW|intrin.h|__m64 _m_pfacc (\__m64、\__m64)|
|_m_pfadd|3DNOW|intrin.h|__m64 _m_pfadd (\__m64、\__m64)|
|_m_pfcmpeq|3DNOW|intrin.h|__m64 _m_pfcmpeq (\__m64、\__m64)|
|_m_pfcmpge|3DNOW|intrin.h|__m64 _m_pfcmpge (\__m64、\__m64)|
|_m_pfcmpgt|3DNOW|intrin.h|__m64 _m_pfcmpgt (\__m64、\__m64)|
|_m_pfmax|3DNOW|intrin.h|__m64 _m_pfmax (\__m64、\__m64)|
|_m_pfmin|3DNOW|intrin.h|__m64 _m_pfmin (\__m64、\__m64)|
|_m_pfmul|3DNOW|intrin.h|__m64 _m_pfmul (\__m64、\__m64)|
|_m_pfnacc|3DNOWEXT|intrin.h|__m64 _m_pfnacc (\__m64、\__m64)|
|_m_pfpnacc|3DNOWEXT|intrin.h|__m64 _m_pfpnacc (\__m64、\__m64)|
|_m_pfrcp|3DNOW|intrin.h|__m64 _m_pfrcp (\__m64)|
|_m_pfrcpit1|3DNOW|intrin.h|__m64 _m_pfrcpit1 (\__m64、\__m64)|
|_m_pfrcpit2|3DNOW|intrin.h|__m64 _m_pfrcpit2 (\__m64、\__m64)|
|_m_pfrsqit1|3DNOW|intrin.h|__m64 _m_pfrsqit1 (\__m64、\__m64)|
|_m_pfrsqrt|3DNOW|intrin.h|__m64 _m_pfrsqrt (\__m64)|
|_m_pfsub|3DNOW|intrin.h|__m64 _m_pfsub (\__m64、\__m64)|
|_m_pfsubr|3DNOW|intrin.h|__m64 _m_pfsubr (\__m64、\__m64)|
|_m_pi2fd|3DNOW|intrin.h|__m64 _m_pi2fd (\__m64)|
|_m_pi2fw|3DNOWEXT|intrin.h|__m64 _m_pi2fw (\__m64)|
|[_m_pinsrw](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_pinsrw)|SSE|intrin.h|__m64 _m_pinsrw (\__m64、int、int)|
|[_m_pmaddwd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_pmaddwd)|MMX|intrin.h|__m64 _m_pmaddwd (\__m64、\__m64)|
|[_m_pmaxsw](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_pmaxsw)|SSE|intrin.h|__m64 _m_pmaxsw (\__m64、\__m64)|
|[_m_pmaxub](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_pmaxub)|SSE|intrin.h|__m64 _m_pmaxub (\__m64、\__m64)|
|[_m_pminsw](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_pminsw)|SSE|intrin.h|__m64 _m_pminsw (\__m64、\__m64)|
|[_m_pminub](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_pminub)|SSE|intrin.h|__m64 _m_pminub (\__m64、\__m64)|
|[_m_pmovmskb](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_pmovmskb)|SSE|intrin.h|int _m_pmovmskb (\__m64)|
|_m_pmulhrw|3DNOW|intrin.h|__m64 _m_pmulhrw (\__m64、\__m64)|
|[_m_pmulhuw](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_pmulhuw)|SSE|intrin.h|__m64 _m_pmulhuw (\__m64、\__m64)|
|[_m_pmulhw](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_pmulhw)|MMX|intrin.h|__m64 _m_pmulhw (\__m64、\__m64)|
|[_m_pmullw](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_pmullw)|MMX|intrin.h|__m64 _m_pmullw (\__m64、\__m64)|
|[_m_por](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_por)|MMX|intrin.h|__m64 _m_por (\__m64、\__m64)|
|_m_prefetch|3DNOW|intrin.h|void _m_prefetch (void\*)|
|_m_prefetchw|3DNOW|intrin.h|void _m_prefetchw (void\*)|
|[_m_psadbw](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_psadbw)|SSE|intrin.h|__m64 _m_psadbw (\__m64、\__m64)|
|[_m_pshufw](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_pshufw)|SSE|intrin.h|__m64 _m_pshufw (\__m64、int)|
|[_m_pslld](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_pslld)|MMX|intrin.h|__m64 _m_pslld (\__m64、\__m64)|
|[_m_pslldi](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_pslldi)|MMX|intrin.h|__m64 _m_pslldi (\__m64、int)|
|[_m_psllq](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_psllq)|MMX|intrin.h|__m64 _m_psllq (\__m64、\__m64)|
|[_m_psllqi](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_psllqi)|MMX|intrin.h|__m64 _m_psllqi (\__m64、int)|
|[_m_psllw](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_psllw)|MMX|intrin.h|__m64 _m_psllw (\__m64、\__m64)|
|[_m_psllwi](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_psllwi)|MMX|intrin.h|__m64 _m_psllwi (\__m64、int)|
|[_m_psrad](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_psrad)|MMX|intrin.h|__m64 _m_psrad (\__m64、\__m64)|
|[_m_psradi](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_psradi)|MMX|intrin.h|__m64 _m_psradi (\__m64、int)|
|[_m_psraw](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_psraw)|MMX|intrin.h|__m64 _m_psraw (\__m64、\__m64)|
|[_m_psrawi](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_psrawi)|MMX|intrin.h|__m64 _m_psrawi (\__m64、int)|
|[_m_psrld](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_psrld)|MMX|intrin.h|__m64 _m_psrld (\__m64、\__m64)|
|[_m_psrldi](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_psrldi)|MMX|intrin.h|__m64 _m_psrldi (\__m64、int)|
|[_m_psrlq](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_psrlq)|MMX|intrin.h|__m64 _m_psrlq (\__m64、\__m64)|
|[_m_psrlqi](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_psrlqi)|MMX|intrin.h|__m64 _m_psrlqi (\__m64、int)|
|[_m_psrlw](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_psrlw)|MMX|intrin.h|__m64 _m_psrlw (\__m64、\__m64)|
|[_m_psrlwi](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_psrlwi)|MMX|intrin.h|__m64 _m_psrlwi (\__m64、int)|
|[_m_psubb](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_psubb)|MMX|intrin.h|__m64 _m_psubb (\__m64、\__m64)|
|[_m_psubd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_psubd)|MMX|intrin.h|__m64 _m_psubd (\__m64、\__m64)|
|[_m_psubsb](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_psubsb)|MMX|intrin.h|__m64 _m_psubsb (\__m64、\__m64)|
|[_m_psubsw](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_psubsw)|MMX|intrin.h|__m64 _m_psubsw (\__m64、\__m64)|
|[_m_psubusb](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_psubusb)|MMX|intrin.h|__m64 _m_psubusb (\__m64、\__m64)|
|[_m_psubusw](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_psubusw)|MMX|intrin.h|__m64 _m_psubusw (\__m64、\__m64)|
|[_m_psubw](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_psubw)|MMX|intrin.h|__m64 _m_psubw (\__m64、\__m64)|
|_m_pswapd|3DNOWEXT|intrin.h|__m64 _m_pswapd (\__m64)|
|[_m_punpckhbw](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_punpckhbw)|MMX|intrin.h|__m64 _m_punpckhbw (\__m64、\__m64)|
|[_m_punpckhdq](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_punpckhdq)|MMX|intrin.h|__m64 _m_punpckhdq (\__m64、\__m64)|
|[_m_punpckhwd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_punpckhwd)|MMX|intrin.h|__m64 _m_punpckhwd (\__m64、\__m64)|
|[_m_punpcklbw](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_punpcklbw)|MMX|intrin.h|__m64 _m_punpcklbw (\__m64、\__m64)|
|[_m_punpckldq](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_punpckldq)|MMX|intrin.h|__m64 _m_punpckldq (\__m64、\__m64)|
|[_m_punpcklwd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_punpcklwd)|MMX|intrin.h|__m64 _m_punpcklwd (\__m64、\__m64)|
|[_m_pxor](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_pxor)|MMX|intrin.h|__m64 _m_pxor (\__m64、\__m64)|
|_m_to_float|3DNOW|intrin.h|float _m_to_float (\__m64)|
|[_m_to_int](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_m_to_int)|MMX|intrin.h|int _m_to_int (\__m64)|
|[_mm_abs_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_abs_epi16)|SSSE3|intrin.h|__m128i _mm_abs_epi16 (\__m128i)|
|[_mm_abs_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_abs_epi32)|SSSE3|intrin.h|__m128i _mm_abs_epi32 (\__m128i)|
|[_mm_abs_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_abs_epi8)|SSSE3|intrin.h|__m128i _mm_abs_epi8 (\__m128i)|
|[_mm_abs_pi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_abs_pi16)|SSSE3|intrin.h|__m64 _mm_abs_pi16 (\__m64)|
|[_mm_abs_pi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_abs_pi32)|SSSE3|intrin.h|__m64 _mm_abs_pi32 (\__m64)|
|[_mm_abs_pi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_abs_pi8)|SSSE3|intrin.h|__m64 _mm_abs_pi8 (\__m64)|
|[_mm_add_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_add_epi16)|SSE2|intrin.h|__m128i _mm_add_epi16 (\__m128i、\__m128i)|
|[_mm_add_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_add_epi32)|SSE2|intrin.h|__m128i _mm_add_epi32 (\__m128i、\__m128i)|
|[_mm_add_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_add_epi64)|SSE2|intrin.h|__m128i _mm_add_epi64 (\__m128i、\__m128i)|
|[_mm_add_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_add_epi8)|SSE2|intrin.h|__m128i _mm_add_epi8 (\__m128i、\__m128i)|
|[_mm_add_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_add_pd)|SSE2|intrin.h|__m128d _mm_add_pd (\__m128d、\__m128d)|
|[_mm_add_pi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_add_pi8)|MMX|mmintrin .h|__m64 _mm_add_pi8 (\__m64、\__m64) [3]|
|[_mm_add_pi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_add_pi16)|MMX|mmintrin .h|__m64 _mm_add_pi16 (\__m64、\__m64) [3]|
|[_mm_add_pi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_add_pi32)|MMX|mmintrin .h|__m64 _mm_add_pi32 (\__m64、\__m64) [3]|
|[_mm_add_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_add_ps)|SSE|intrin.h|__m128 _mm_add_ps (\__m128、\__m128)|
|[_mm_add_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_add_sd)|SSE2|intrin.h|__m128d _mm_add_sd (\__m128d、\__m128d)|
|[_mm_add_si64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_add_si64)|SSE2|intrin.h|__m64 _mm_add_si64 (\__m64、\__m64)|
|[_mm_add_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_add_ss)|SSE|intrin.h|__m128 _mm_add_ss (\__m128、\__m128)|
|[_mm_adds_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_adds_epi16)|SSE2|intrin.h|__m128i _mm_adds_epi16 (\__m128i、\__m128i)|
|[_mm_adds_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_adds_epi8)|SSE2|intrin.h|__m128i _mm_adds_epi8 (\__m128i、\__m128i)|
|[_mm_adds_epu16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_adds_epu16)|SSE2|intrin.h|__m128i _mm_adds_epu16 (\__m128i、\__m128i)|
|[_mm_adds_epu8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_adds_epu8)|SSE2|intrin.h|__m128i _mm_adds_epu8 (\__m128i、\__m128i)|
|[_mm_adds_pi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_adds_pi8)|MMX|mmintrin .h|__m64 _mm_adds_pi8 (\__m64、\__m64) [3]|
|[_mm_adds_pi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_adds_pi16)|MMX|mmintrin .h|__m64 _mm_adds_pi16 (\__m64、\__m64) [3]|
|[_mm_adds_pu8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_adds_pu8)|MMX|mmintrin .h|__m64 _mm_adds_pu8 (\__m64、\__m64) [3]|
|[_mm_adds_pu16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_adds_pu16)|MMX|mmintrin .h|__m64 _mm_adds_pu16 (\__m64、\__m64) [3]|
|[_mm_addsub_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_addsub_pd)|SSE3|intrin.h|__m128d _mm_addsub_pd (\__m128d、\__m128d)|
|[_mm_addsub_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_addsub_ps)|SSE3|intrin.h|__m128 _mm_addsub_ps (\__m128、\__m128)|
|[_mm_aesdec_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_aesdec_si128)|AESNI [2]|immintrin.h|__m128i _mm_aesdec_si128 (\__m128i、\__m128i)|
|[_mm_aesdeclast_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_aesdeclast_si128)|AESNI [2]|immintrin.h|__m128i _mm_aesdeclast_si128 (\__m128i、\__m128i)|
|[_mm_aesenc_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_aesenc_si128)|AESNI [2]|immintrin.h|__m128i _mm_aesenc_si128 (\__m128i、\__m128i)|
|[_mm_aesenclast_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_aesenclast_si128)|AESNI [2]|immintrin.h|__m128i _mm_aesenclast_si128 (\__m128i、\__m128i)|
|[_mm_aesimc_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_aesimc_si128)|AESNI [2]|immintrin.h|__m128i _mm_aesimc_si128 (\__m128i)|
|[_mm_aeskeygenassist_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_aeskeygenassist_si128)|AESNI [2]|immintrin.h|__m128i _mm_aeskeygenassist_si128 (\__m128i、const int)|
|[_mm_alignr_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_alignr_epi8)|SSSE3|intrin.h|__m128i _mm_alignr_epi8 (\__m128i、\__m128i、int)|
|[_mm_alignr_pi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_alignr_pi8)|SSSE3|intrin.h|__m64 _mm_alignr_pi8 (\__m64、\__m64、int)|
|[_mm_and_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_and_pd)|SSE2|intrin.h|__m128d _mm_and_pd (\__m128d、\__m128d)|
|[_mm_and_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_and_ps)|SSE|intrin.h|__m128 _mm_and_ps (\__m128、\__m128)|
|[_mm_and_si64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_and_si64)|MMX|mmintrin .h|__m64 _mm_and_si64 (\__m64、\__m64) [3]|
|[_mm_and_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_and_si128)|SSE2|intrin.h|__m128i _mm_and_si128 (\__m128i、\__m128i)|
|[_mm_andnot_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_andnot_pd)|SSE2|intrin.h|__m128d _mm_andnot_pd (\__m128d、\__m128d)|
|[_mm_andnot_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_andnot_ps)|SSE|intrin.h|__m128 _mm_andnot_ps (\__m128、\__m128)|
|[_mm_andnot_si64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_andnot_si64)|MMX|mmintrin .h|__m64 _mm_andnot_si64 (\__m64、\__m64) [3]|
|[_mm_andnot_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_andnot_si128)|SSE2|intrin.h|__m128i _mm_andnot_si128 (\__m128i、\__m128i)|
|[_mm_avg_epu16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_avg_epu16)|SSE2|intrin.h|__m128i _mm_avg_epu16 (\__m128i、\__m128i)|
|[_mm_avg_epu8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_avg_epu8)|SSE2|intrin.h|__m128i _mm_avg_epu8 (\__m128i、\__m128i)|
|[_mm_blend_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_blend_epi16)|SSE41|intrin.h|__m128i _mm_blend_epi16 (\__m128i、\__m128i、const int)|
|[_mm_blend_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_blend_epi32)|AVX2 [2]|immintrin.h|__m128i _mm_blend_epi32 (\__m128i、\__m128i、const int)|
|[_mm_blend_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_blend_pd)|SSE41|intrin.h|__m128d _mm_blend_pd (\__m128d、\__m128d、const int)|
|[_mm_blend_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_blend_ps)|SSE41|intrin.h|__m128 _mm_blend_ps (\__m128、\__m128、const int)|
|[_mm_blendv_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_blendv_epi8)|SSE41|intrin.h|__m128i _mm_blendv_epi8 (\__m128i、\__m128i、\__m128i)|
|[_mm_blendv_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_blendv_pd)|SSE41|intrin.h|__m128d _mm_blendv_pd (\__m128d、\__m128d、\__m128d)|
|[_mm_blendv_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_blendv_ps)|SSE41|intrin.h|__m128 _mm_blendv_ps (\__m128、\__m128、\__m128)|
|[_mm_broadcast_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_broadcast_ss)|AVX [2]|immintrin.h|__m128 _mm_broadcast_ss(float const *)|
|[_mm_broadcastb_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_broadcastb_epi8)|AVX2 [2]|immintrin.h|__m128i _mm_broadcastb_epi8 (\__m128i)|
|[_mm_broadcastd_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_broadcastd_epi32)|AVX2 [2]|immintrin.h|__m128i _mm_broadcastd_epi32 (\__m128i)|
|[_mm_broadcastq_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_broadcastq_epi64)|AVX2 [2]|immintrin.h|__m128i _mm_broadcastq_epi64 (\__m128i)|
|[_mm_broadcastsd_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_broadcastsd_pd)|AVX2 [2]|immintrin.h|__m128d _mm_broadcastsd_pd (\__m128d)|
|[_mm_broadcastss_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_broadcastss_ps)|AVX2 [2]|immintrin.h|__m128 _mm_broadcastss_ps (\__m128)|
|[_mm_broadcastw_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_broadcastw_epi16)|AVX2 [2]|immintrin.h|__m128i _mm_broadcastw_epi16 (\__m128i)|
|[_mm_castpd_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_castpd_ps)|SSSE3|intrin.h|__m128 _mm_castpd_ps (\__m128d)|
|[_mm_castpd_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_castpd_si128)|SSSE3|intrin.h|__m128i _mm_castpd_si128 (\__m128d)|
|[_mm_castps_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_castps_pd)|SSSE3|intrin.h|__m128d _mm_castps_pd (\__m128)|
|[_mm_castps_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_castps_si128)|SSSE3|intrin.h|__m128i _mm_castps_si128 (\__m128)|
|[_mm_castsi128_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_castsi128_pd)|SSSE3|intrin.h|__m128d _mm_castsi128_pd (\__m128i)|
|[_mm_castsi128_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_castsi128_ps)|SSSE3|intrin.h|__m128 _mm_castsi128_ps (\__m128i)|
|[_mm_clflush](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_clflush)|SSE2|intrin.h|void _mm_clflush (void const \*)|
|[_mm_clmulepi64_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_clmulepi64_si128)|PCLMULQDQ [2]|immintrin.h|__m128i _mm_clmulepi64_si128 (\__m128i、\__m128i、const int)|
|_mm_cmov_si128|XOP [1]|ammintrin.h|__m128i _mm_cmov_si128 (\__m128i、\__m128i、\__m128i)|
|[_mm_cmp_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmp_pd)|AVX [2]|immintrin.h|__m128d _mm_cmp_pd (\__m128d、\__m128d、const int)|
|[_mm_cmp_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmp_ps)|AVX [2]|immintrin.h|__m128 _mm_cmp_ps (\__m128、\__m128、const int)|
|[_mm_cmp_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmp_sd)|AVX [2]|immintrin.h|__m128d _mm_cmp_sd (\__m128d、\__m128d、const int)|
|[_mm_cmp_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmp_ss)|AVX [2]|immintrin.h|__m128 _mm_cmp_ss (\__m128、\__m128、const int)|
|[_mm_cmpeq_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpeq_epi16)|SSE2|intrin.h|__m128i _mm_cmpeq_epi16 (\__m128i、\__m128i)|
|[_mm_cmpeq_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpeq_epi32)|SSE2|intrin.h|__m128i _mm_cmpeq_epi32 (\__m128i、\__m128i)|
|[_mm_cmpeq_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpeq_epi64)|SSE41|intrin.h|__m128i _mm_cmpeq_epi64 (\__m128i、\__m128i)|
|[_mm_cmpeq_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpeq_epi8)|SSE2|intrin.h|__m128i _mm_cmpeq_epi8 (\__m128i、\__m128i)|
|[_mm_cmpeq_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpeq_pd)|SSE2|intrin.h|__m128d _mm_cmpeq_pd (\__m128d、\__m128d)|
|[_mm_cmpeq_pi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpeq_pi8)|MMX|mmintrin .h|__m64 _mm_cmpeq_pi8 (\__m64、\__m64) [3]|
|[_mm_cmpeq_pi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpeq_pi16)|MMX|mmintrin .h|__m64 _mm_cmpeq_pi16 (\__m64、\__m64) [3]|
|[_mm_cmpeq_pi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpeq_pi32)|MMX|mmintrin .h|__m64 _mm_cmpeq_pi32 (\__m64、\__m64) [3]|
|[_mm_cmpeq_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpeq_ps)|SSE|intrin.h|__m128 _mm_cmpeq_ps (\__m128、\__m128)|
|[_mm_cmpeq_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpeq_sd)|SSE2|intrin.h|__m128d _mm_cmpeq_sd (\__m128d、\__m128d)|
|[_mm_cmpeq_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpeq_ss)|SSE|intrin.h|__m128 _mm_cmpeq_ss (\__m128、\__m128)|
|[_mm_cmpestra](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpestra)|SSE42|intrin.h|int _mm_cmpestra (\__m128i、int、\__m128i、int、const int)|
|[_mm_cmpestrc](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpestrc)|SSE42|intrin.h|int _mm_cmpestrc (\__m128i、int、\__m128i、int、const int)|
|[_mm_cmpestri](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpestri)|SSE42|intrin.h|int _mm_cmpestri (\__m128i、int、\__m128i、int、const int)|
|[_mm_cmpestrm](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpestrm)|SSE42|intrin.h|__m128i _mm_cmpestrm (\__m128i、int、\__m128i、int、const int)|
|[_mm_cmpestro](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpestro)|SSE42|intrin.h|int _mm_cmpestro (\__m128i、int、\__m128i、int、const int)|
|[_mm_cmpestrs](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpestrs)|SSE42|intrin.h|int _mm_cmpestrs (\__m128i、int、\__m128i、int、const int)|
|[_mm_cmpestrz](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpestrz)|SSE42|intrin.h|int _mm_cmpestrz (\__m128i、int、\__m128i、int、const int)|
|[_mm_cmpge_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpge_pd)|SSE2|intrin.h|__m128d _mm_cmpge_pd (\__m128d、\__m128d)|
|[_mm_cmpge_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpge_ps)|SSE|intrin.h|__m128 _mm_cmpge_ps (\__m128、\__m128)|
|[_mm_cmpge_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpge_sd)|SSE2|intrin.h|__m128d _mm_cmpge_sd (\__m128d、\__m128d)|
|[_mm_cmpge_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpge_ss)|SSE|intrin.h|__m128 _mm_cmpge_ss (\__m128、\__m128)|
|[_mm_cmpgt_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpgt_epi16)|SSE2|intrin.h|__m128i _mm_cmpgt_epi16 (\__m128i、\__m128i)|
|[_mm_cmpgt_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpgt_epi32)|SSE2|intrin.h|__m128i _mm_cmpgt_epi32 (\__m128i、\__m128i)|
|[_mm_cmpgt_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpgt_epi64)|SSE42|intrin.h|__m128i _mm_cmpgt_epi64 (\__m128i、\__m128i)|
|[_mm_cmpgt_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpgt_epi8)|SSE2|intrin.h|__m128i _mm_cmpgt_epi8 (\__m128i、\__m128i)|
|[_mm_cmpgt_pi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpgt_pi8)|MMX|mmintrin .h|__m64 _mm_cmpgt_pi8 (\__m64、\__m64) [3]|
|[_mm_cmpgt_pi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpgt_pi16)|MMX|mmintrin .h|__m64 _mm_cmpgt_pi16 (\__m64、\__m64) [3]|
|[_mm_cmpgt_pi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpgt_pi32)|MMX|mmintrin .h|__m64 _mm_cmpgt_pi32 (\__m64、\__m64) [3]|
|[_mm_cmpgt_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpgt_pd)|SSE2|intrin.h|__m128d _mm_cmpgt_pd (\__m128d、\__m128d)|
|[_mm_cmpgt_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpgt_ps)|SSE|intrin.h|__m128 _mm_cmpgt_ps (\__m128、\__m128)|
|[_mm_cmpgt_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpgt_sd)|SSE2|intrin.h|__m128d _mm_cmpgt_sd (\__m128d、\__m128d)|
|[_mm_cmpgt_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpgt_ss)|SSE|intrin.h|__m128 _mm_cmpgt_ss (\__m128、\__m128)|
|[_mm_cmpistra](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpistra)|SSE42|intrin.h|int _mm_cmpistra (\__m128i、\__m128i、const int)|
|[_mm_cmpistrc](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpistrc)|SSE42|intrin.h|int _mm_cmpistrc (\__m128i、\__m128i、const int)|
|[_mm_cmpistri](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpistri)|SSE42|intrin.h|int _mm_cmpistri (\__m128i、\__m128i、const int)|
|[_mm_cmpistrm](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpistrm)|SSE42|intrin.h|__m128i _mm_cmpistrm (\__m128i、\__m128i、const int)|
|[_mm_cmpistro](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpistro)|SSE42|intrin.h|int _mm_cmpistro (\__m128i、\__m128i、const int)|
|[_mm_cmpistrs](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpistrs)|SSE42|intrin.h|int _mm_cmpistrs (\__m128i、\__m128i、const int)|
|[_mm_cmpistrz](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpistrz)|SSE42|intrin.h|int _mm_cmpistrz (\__m128i、\__m128i、const int)|
|[_mm_cmple_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmple_pd)|SSE2|intrin.h|__m128d _mm_cmple_pd (\__m128d、\__m128d)|
|[_mm_cmple_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmple_ps)|SSE|intrin.h|__m128 _mm_cmple_ps (\__m128、\__m128)|
|[_mm_cmple_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmple_sd)|SSE2|intrin.h|__m128d _mm_cmple_sd (\__m128d、\__m128d)|
|[_mm_cmple_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmple_ss)|SSE|intrin.h|__m128 _mm_cmple_ss (\__m128、\__m128)|
|[_mm_cmplt_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmplt_epi16)|SSE2|intrin.h|__m128i _mm_cmplt_epi16 (\__m128i、\__m128i)|
|[_mm_cmplt_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmplt_epi32)|SSE2|intrin.h|__m128i _mm_cmplt_epi32 (\__m128i、\__m128i)|
|[_mm_cmplt_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmplt_epi8)|SSE2|intrin.h|__m128i _mm_cmplt_epi8 (\__m128i、\__m128i)|
|[_mm_cmplt_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmplt_pd)|SSE2|intrin.h|__m128d _mm_cmplt_pd (\__m128d、\__m128d)|
|[_mm_cmplt_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmplt_ps)|SSE|intrin.h|__m128 _mm_cmplt_ps (\__m128、\__m128)|
|[_mm_cmplt_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmplt_sd)|SSE2|intrin.h|__m128d _mm_cmplt_sd (\__m128d、\__m128d)|
|[_mm_cmplt_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmplt_ss)|SSE|intrin.h|__m128 _mm_cmplt_ss (\__m128、\__m128)|
|[_mm_cmpneq_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpneq_pd)|SSE2|intrin.h|__m128d _mm_cmpneq_pd (\__m128d、\__m128d)|
|[_mm_cmpneq_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpneq_ps)|SSE|intrin.h|__m128 _mm_cmpneq_ps (\__m128、\__m128)|
|[_mm_cmpneq_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpneq_sd)|SSE2|intrin.h|__m128d _mm_cmpneq_sd (\__m128d、\__m128d)|
|[_mm_cmpneq_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpneq_ss)|SSE|intrin.h|__m128 _mm_cmpneq_ss (\__m128、\__m128)|
|[_mm_cmpnge_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpnge_pd)|SSE2|intrin.h|__m128d _mm_cmpnge_pd (\__m128d、\__m128d)|
|[_mm_cmpnge_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpnge_ps)|SSE|intrin.h|__m128 _mm_cmpnge_ps (\__m128、\__m128)|
|[_mm_cmpnge_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpnge_sd)|SSE2|intrin.h|__m128d _mm_cmpnge_sd (\__m128d、\__m128d)|
|[_mm_cmpnge_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpnge_ss)|SSE|intrin.h|__m128 _mm_cmpnge_ss (\__m128、\__m128)|
|[_mm_cmpngt_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpngt_pd)|SSE2|intrin.h|__m128d _mm_cmpngt_pd (\__m128d、\__m128d)|
|[_mm_cmpngt_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpngt_ps)|SSE|intrin.h|__m128 _mm_cmpngt_ps (\__m128、\__m128)|
|[_mm_cmpngt_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpngt_sd)|SSE2|intrin.h|__m128d _mm_cmpngt_sd (\__m128d、\__m128d)|
|[_mm_cmpngt_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpngt_ss)|SSE|intrin.h|__m128 _mm_cmpngt_ss (\__m128、\__m128)|
|[_mm_cmpnle_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpnle_pd)|SSE2|intrin.h|__m128d _mm_cmpnle_pd (\__m128d、\__m128d)|
|[_mm_cmpnle_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpnle_ps)|SSE|intrin.h|__m128 _mm_cmpnle_ps (\__m128、\__m128)|
|[_mm_cmpnle_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpnle_sd)|SSE2|intrin.h|__m128d _mm_cmpnle_sd (\__m128d、\__m128d)|
|[_mm_cmpnle_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpnle_ss)|SSE|intrin.h|__m128 _mm_cmpnle_ss (\__m128、\__m128)|
|[_mm_cmpnlt_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpnlt_pd)|SSE2|intrin.h|__m128d _mm_cmpnlt_pd (\__m128d、\__m128d)|
|[_mm_cmpnlt_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpnlt_ps)|SSE|intrin.h|__m128 _mm_cmpnlt_ps (\__m128、\__m128)|
|[_mm_cmpnlt_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpnlt_sd)|SSE2|intrin.h|__m128d _mm_cmpnlt_sd (\__m128d、\__m128d)|
|[_mm_cmpnlt_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpnlt_ss)|SSE|intrin.h|__m128 _mm_cmpnlt_ss (\__m128、\__m128)|
|[_mm_cmpord_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpord_pd)|SSE2|intrin.h|__m128d _mm_cmpord_pd (\__m128d、\__m128d)|
|[_mm_cmpord_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpord_ps)|SSE|intrin.h|__m128 _mm_cmpord_ps (\__m128、\__m128)|
|[_mm_cmpord_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpord_sd)|SSE2|intrin.h|__m128d _mm_cmpord_sd (\__m128d、\__m128d)|
|[_mm_cmpord_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpord_ss)|SSE|intrin.h|__m128 _mm_cmpord_ss (\__m128、\__m128)|
|[_mm_cmpunord_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpunord_pd)|SSE2|intrin.h|__m128d _mm_cmpunord_pd (\__m128d、\__m128d)|
|[_mm_cmpunord_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpunord_ps)|SSE|intrin.h|__m128 _mm_cmpunord_ps (\__m128、\__m128)|
|[_mm_cmpunord_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpunord_sd)|SSE2|intrin.h|__m128d _mm_cmpunord_sd (\__m128d、\__m128d)|
|[_mm_cmpunord_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cmpunord_ss)|SSE|intrin.h|__m128 _mm_cmpunord_ss (\__m128、\__m128)|
|_mm_com_epi16|XOP [1]|ammintrin.h|__m128i _mm_com_epi16 (\__m128i、\__m128i、int)|
|_mm_com_epi32|XOP [1]|ammintrin.h|__m128i _mm_com_epi32 (\__m128i、\__m128i、int)|
|_mm_com_epi64|XOP [1]|ammintrin.h|__m128i _mm_com_epi32 (\__m128i、\__m128i、int)|
|_mm_com_epi8|XOP [1]|ammintrin.h|__m128i _mm_com_epi8 (\__m128i、\__m128i、int)|
|_mm_com_epu16|XOP [1]|ammintrin.h|__m128i _mm_com_epu16 (\__m128i、\__m128i、int)|
|_mm_com_epu32|XOP [1]|ammintrin.h|__m128i _mm_com_epu32 (\__m128i、\__m128i、int)|
|_mm_com_epu64|XOP [1]|ammintrin.h|__m128i _mm_com_epu32 (\__m128i、\__m128i、int)|
|_mm_com_epu8|XOP [1]|ammintrin.h|__m128i _mm_com_epu8 (\__m128i、\__m128i、int)|
|[_mm_comieq_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_comieq_sd)|SSE2|intrin.h|int _mm_comieq_sd (\__m128d、\__m128d)|
|[_mm_comieq_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_comieq_ss)|SSE|intrin.h|int _mm_comieq_ss (\__m128、\__m128)|
|[_mm_comige_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_comige_sd)|SSE2|intrin.h|int _mm_comige_sd (\__m128d、\__m128d)|
|[_mm_comige_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_comige_ss)|SSE|intrin.h|int _mm_comige_ss (\__m128、\__m128)|
|[_mm_comigt_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_comigt_sd)|SSE2|intrin.h|int _mm_comigt_sd (\__m128d、\__m128d)|
|[_mm_comigt_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_comigt_ss)|SSE|intrin.h|int _mm_comigt_ss (\__m128、\__m128)|
|[_mm_comile_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_comile_sd)|SSE2|intrin.h|int _mm_comile_sd (\__m128d、\__m128d)|
|[_mm_comile_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_comile_ss)|SSE|intrin.h|int _mm_comile_ss (\__m128、\__m128)|
|[_mm_comilt_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_comilt_sd)|SSE2|intrin.h|int _mm_comilt_sd (\__m128d、\__m128d)|
|[_mm_comilt_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_comilt_ss)|SSE|intrin.h|int _mm_comilt_ss (\__m128、\__m128)|
|[_mm_comineq_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_comineq_sd)|SSE2|intrin.h|int _mm_comineq_sd (\__m128d、\__m128d)|
|[_mm_comineq_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_comineq_ss)|SSE|intrin.h|int _mm_comineq_ss (\__m128、\__m128)|
|[_mm_crc32_u16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_crc32_u16)|SSE42|intrin.h|unsigned int _mm_crc32_u16 (符号なし int, unsigned short)|
|[_mm_crc32_u32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_crc32_u32)|SSE42|intrin.h|unsigned int _mm_crc32_u32(unsigned int, unsigned int)|
|[_mm_crc32_u8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_crc32_u8)|SSE42|intrin.h|unsigned int _mm_crc32_u8 (符号なし int, unsigned char)|
|[_mm_cvt_pi2ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvt_pi2ps)|SSE|intrin.h|__m128 _mm_cvt_pi2ps (\__m128、\__m64)|
|[_mm_cvt_ps2pi](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvt_ps2pi)|SSE|intrin.h|__m64 _mm_cvt_ps2pi (\__m128)|
|[_mm_cvt_si2ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvt_si2ss)|SSE|intrin.h|__m128 _mm_cvt_si2ss (\__m128、int)|
|[_mm_cvt_ss2si](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvt_ss2si)|SSE|intrin.h|int _mm_cvt_ss2si (\__m128)|
|[_mm_cvtepi16_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtepi16_epi32)|SSE41|intrin.h|__m128i _mm_cvtepi16_epi32 (\__m128i)|
|[_mm_cvtepi16_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtepi16_epi64)|SSE41|intrin.h|__m128i _mm_cvtepi16_epi64 (\__m128i)|
|[_mm_cvtepi32_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtepi32_epi64)|SSE41|intrin.h|__m128i _mm_cvtepi32_epi64 (\__m128i)|
|[_mm_cvtepi32_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtepi32_pd)|SSE2|intrin.h|__m128d _mm_cvtepi32_pd (\__m128i)|
|[_mm_cvtepi32_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtepi32_ps)|SSE2|intrin.h|__m128 _mm_cvtepi32_ps (\__m128i)|
|[_mm_cvtepi8_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtepi8_epi16)|SSE41|intrin.h|__m128i _mm_cvtepi8_epi16 (\__m128i)|
|[_mm_cvtepi8_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtepi8_epi32)|SSE41|intrin.h|__m128i _mm_cvtepi8_epi32 (\__m128i)|
|[_mm_cvtepi8_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtepi8_epi64)|SSE41|intrin.h|__m128i _mm_cvtepi8_epi64 (\__m128i)|
|[_mm_cvtepu16_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtepu16_epi32)|SSE41|intrin.h|__m128i _mm_cvtepu16_epi32 (\__m128i)|
|[_mm_cvtepu16_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtepu16_epi64)|SSE41|intrin.h|__m128i _mm_cvtepu16_epi64 (\__m128i)|
|[_mm_cvtepu32_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtepu32_epi64)|SSE41|intrin.h|__m128i _mm_cvtepu32_epi64 (\__m128i)|
|[_mm_cvtepu8_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtepu8_epi16)|SSE41|intrin.h|__m128i _mm_cvtepu8_epi16 (\__m128i)|
|[_mm_cvtepu8_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtepu8_epi32)|SSE41|intrin.h|__m128i _mm_cvtepu8_epi32 (\__m128i)|
|[_mm_cvtepu8_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtepu8_epi64)|SSE41|intrin.h|__m128i _mm_cvtepu8_epi64 (\__m128i)|
|[_mm_cvtpd_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtpd_epi32)|SSE2|intrin.h|__m128i _mm_cvtpd_epi32 (\__m128d)|
|[_mm_cvtpd_pi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtpd_pi32)|SSE2|intrin.h|__m64 _mm_cvtpd_pi32 (\__m128d)|
|[_mm_cvtpd_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtpd_ps)|SSE2|intrin.h|__m128 _mm_cvtpd_ps (\__m128d)|
|[_mm_cvtph_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtph_ps)|F16C [2]|immintrin.h|__m128 _mm_cvtph_ps (\__m128i)|
|[_mm_cvtpi32_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtpi32_pd)|SSE2|intrin.h|__m128d _mm_cvtpi32_pd (\__m64)|
|[_mm_cvtps_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtps_epi32)|SSE2|intrin.h|__m128i _mm_cvtps_epi32 (\__m128)|
|[_mm_cvtps_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtps_pd)|SSE2|intrin.h|__m128d _mm_cvtps_pd (\__m128)|
|[_mm_cvtps_ph](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtps_ph)|F16C [2]|immintrin.h|__m128i _mm_cvtps_ph (\__m128、const int)|
|[_mm_cvtsd_f64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtsd_f64)|SSSE3|intrin.h|double _mm_cvtsd_f64 (\__m128d)|
|[_mm_cvtsd_si32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtsd_si32)|SSE2|intrin.h|int _mm_cvtsd_si32 (\__m128d)|
|[_mm_cvtsd_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtsd_ss)|SSE2|intrin.h|__m128 _mm_cvtsd_ss (\__m128、\__m128d)|
|[_mm_cvtsi128_si32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtsi128_si32)|SSE2|intrin.h|int _mm_cvtsi128_si32 (\__m128i)|
|[_mm_cvtsi32_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtsi32_sd)|SSE2|intrin.h|__m128d _mm_cvtsi32_sd (\__m128d、int)|
|[_mm_cvtsi32_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtsi32_si128)|SSE2|intrin.h|__m128i _mm_cvtsi32_si128(int)|
|[_mm_cvtsi32_si64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtsi32_si64)|MMX|mmintrin .h|__m64 _mm_cvtsi32_si64 (int) [3]|
|[_mm_cvtsi64_si32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtsi64_si32)|MMX|mmintrin .h|int _mm_cvtsi64_si32 (__m64) [3]|
|[_mm_cvtss_f32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtss_f32)|SSSE3|intrin.h|float _mm_cvtss_f32 (\__m128)|
|[_mm_cvtss_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtss_sd)|SSE2|intrin.h|__m128d _mm_cvtss_sd (\__m128d、\__m128)|
|[_mm_cvtt_ps2pi](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtt_ps2pi)|SSE|intrin.h|__m64 _mm_cvtt_ps2pi (\__m128)|
|[_mm_cvtt_ss2si](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvtt_ss2si)|SSE|intrin.h|int _mm_cvtt_ss2si (\__m128)|
|[_mm_cvttpd_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvttpd_epi32)|SSE2|intrin.h|__m128i _mm_cvttpd_epi32 (\__m128d)|
|[_mm_cvttpd_pi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvttpd_pi32)|SSE2|intrin.h|__m64 _mm_cvttpd_pi32 (\__m128d)|
|[_mm_cvttps_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvttps_epi32)|SSE2|intrin.h|__m128i _mm_cvttps_epi32 (\__m128)|
|[_mm_cvttsd_si32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_cvttsd_si32)|SSE2|intrin.h|int _mm_cvttsd_si32 (\__m128d)|
|[_mm_div_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_div_pd)|SSE2|intrin.h|__m128d _mm_div_pd (\__m128d、\__m128d)|
|[_mm_div_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_div_ps)|SSE|intrin.h|__m128 _mm_div_ps (\__m128、\__m128)|
|[_mm_div_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_div_sd)|SSE2|intrin.h|__m128d _mm_div_sd (\__m128d、\__m128d)|
|[_mm_div_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_div_ss)|SSE|intrin.h|__m128 _mm_div_ss (\__m128、\__m128)|
|[_mm_dp_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_dp_pd)|SSE41|intrin.h|__m128d _mm_dp_pd (\__m128d、\__m128d、const int)|
|[_mm_dp_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_dp_ps)|SSE41|intrin.h|__m128 _mm_dp_ps (\__m128、\__m128、const int)|
|[_mm_empty](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_empty)|MMX|mmintrin .h|void _mm_empty (void) [3]|
|[_mm_extract_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_extract_epi16)|SSE2|intrin.h|int _mm_extract_epi16 (\__m128i、int)|
|[_mm_extract_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_extract_epi32)|SSE41|intrin.h|int _mm_extract_epi32 (\__m128i、const int)|
|[_mm_extract_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_extract_epi8)|SSE41|intrin.h|int _mm_extract_epi8 (\__m128i、const int)|
|[_mm_extract_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_extract_ps)|SSE41|intrin.h|int _mm_extract_ps (\__m128、const int)|
|[_mm_extract_si64](mm-extract-si64-mm-extracti-si64.md)|SSE4a|intrin.h|__m128i _mm_extract_si64 (\__m128i、\__m128i)|
|[_mm_extracti_si64](mm-extract-si64-mm-extracti-si64.md)|SSE4a|intrin.h|__m128i _mm_extracti_si64 (\__m128i、int、int)|
|[_mm_fmadd_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_fmadd_pd)|FMA [2]|immintrin.h|__m128d _mm_fmadd_pd (\__m128d、\__m128d、\__m128d)|
|[_mm_fmadd_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_fmadd_ps)|FMA [2]|immintrin.h|__m128 _mm_fmadd_ps (\__m128、\__m128、\__m128)|
|[_mm_fmadd_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_fmadd_sd)|FMA [2]|immintrin.h|__m128d _mm_fmadd_sd (\__m128d、\__m128d、\__m128d)|
|[_mm_fmadd_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_fmadd_ss)|FMA [2]|immintrin.h|__m128 _mm_fmadd_ss (\__m128、\__m128、\__m128)|
|[_mm_fmaddsub_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_fmaddsub_pd)|FMA [2]|immintrin.h|__m128d _mm_fmaddsub_pd (\__m128d、\__m128d、\__m128d)|
|[_mm_fmaddsub_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_fmaddsub_ps)|FMA [2]|immintrin.h|__m128 _mm_fmaddsub_ps (\__m128、\__m128、\__m128)|
|[_mm_fmsub_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_fmsub_pd)|FMA [2]|immintrin.h|__m128d _mm_fmsub_pd (\__m128d、\__m128d、\__m128d)|
|[_mm_fmsub_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_fmsub_ps)|FMA [2]|immintrin.h|__m128 _mm_fmsub_ps (\__m128、\__m128、\__m128)|
|[_mm_fmsub_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_fmsub_sd)|FMA [2]|immintrin.h|__m128d _mm_fmsub_sd (\__m128d、\__m128d、\__m128d)|
|[_mm_fmsub_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_fmsub_ss)|FMA [2]|immintrin.h|__m128 _mm_fmsub_ss (\__m128、\__m128、\__m128)|
|[_mm_fmsubadd_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_fmsubadd_pd)|FMA [2]|immintrin.h|__m128d _mm_fmsubadd_pd (\__m128d、\__m128d、\__m128d)|
|[_mm_fmsubadd_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_fmsubadd_ps)|FMA [2]|immintrin.h|__m128 _mm_fmsubadd_ps (\__m128、\__m128、\__m128)|
|[_mm_fnmadd_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_fnmadd_pd)|FMA [2]|immintrin.h|__m128d _mm_fnmadd_pd (\__m128d、\__m128d、\__m128d)|
|[_mm_fnmadd_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_fnmadd_ps)|FMA [2]|immintrin.h|__m128 _mm_fnmadd_ps (\__m128、\__m128、\__m128)|
|[_mm_fnmadd_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_fnmadd_sd)|FMA [2]|immintrin.h|__m128d _mm_fnmadd_sd (\__m128d、\__m128d、\__m128d)|
|[_mm_fnmadd_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_fnmadd_ss)|FMA [2]|immintrin.h|__m128 _mm_fnmadd_ss (\__m128、\__m128、\__m128)|
|[_mm_fnmsub_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_fnmsub_pd)|FMA [2]|immintrin.h|__m128d _mm_fnmsub_pd (\__m128d、\__m128d、\__m128d)|
|[_mm_fnmsub_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_fnmsub_ps)|FMA [2]|immintrin.h|__m128 _mm_fnmsub_ps (\__m128、\__m128、\__m128)|
|[_mm_fnmsub_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_fnmsub_sd)|FMA [2]|immintrin.h|__m128d _mm_fnmsub_sd (\__m128d、\__m128d、\__m128d)|
|[_mm_fnmsub_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_fnmsub_ss)|FMA [2]|immintrin.h|__m128 _mm_fnmsub_ss (\__m128、\__m128、\__m128)|
|_mm_frcz_pd|XOP [1]|ammintrin.h|__m128d _mm_frcz_pd (\__m128d)|
|_mm_frcz_ps|XOP [1]|ammintrin.h|__m128 _mm_frcz_ps (\__m128)|
|_mm_frcz_sd|XOP [1]|ammintrin.h|__m128d _mm_frcz_sd (\__m128d、\__m128d)|
|_mm_frcz_ss|XOP [1]|ammintrin.h|__m128 _mm_frcz_ss (\__m128、\__m128)|
|[_mm_getcsr](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_getcsr)|SSE|intrin.h|unsigned int _mm_getcsr(void)|
|[_mm_hadd_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_hadd_epi16)|SSSE3|intrin.h|__m128i _mm_hadd_epi16 (\__m128i、\__m128i)|
|[_mm_hadd_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_hadd_epi32)|SSSE3|intrin.h|__m128i _mm_hadd_epi32 (\__m128i、\__m128i)|
|[_mm_hadd_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_hadd_pd)|SSE3|intrin.h|__m128d _mm_hadd_pd (\__m128d、\__m128d)|
|[_mm_hadd_pi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_hadd_pi16)|SSSE3|intrin.h|__m64 _mm_hadd_pi16 (\__m64、\__m64)|
|[_mm_hadd_pi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_hadd_pi32)|SSSE3|intrin.h|__m64 _mm_hadd_pi32 (\__m64、\__m64)|
|[_mm_hadd_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_hadd_ps)|SSE3|intrin.h|__m128 _mm_hadd_ps (\__m128、\__m128)|
|_mm_haddd_epi16|XOP [1]|ammintrin.h|__m128i _mm_haddd_epi16 (\__m128i)|
|_mm_haddd_epi8|XOP [1]|ammintrin.h|__m128i _mm_haddd_epi8 (\__m128i)|
|_mm_haddd_epu16|XOP [1]|ammintrin.h|__m128i _mm_haddd_epu16 (\__m128i)|
|_mm_haddd_epu8|XOP [1]|ammintrin.h|__m128i _mm_haddd_epu8 (\__m128i)|
|_mm_haddq_epi16|XOP [1]|ammintrin.h|__m128i _mm_haddq_epi16 (\__m128i)|
|_mm_haddq_epi32|XOP [1]|ammintrin.h|__m128i _mm_haddq_epi32 (\__m128i)|
|_mm_haddq_epi8|XOP [1]|ammintrin.h|__m128i _mm_haddq_epi8 (\__m128i)|
|_mm_haddq_epu16|XOP [1]|ammintrin.h|__m128i _mm_haddq_epu16 (\__m128i)|
|_mm_haddq_epu32|XOP [1]|ammintrin.h|__m128i _mm_haddq_epu32 (\__m128i)|
|_mm_haddq_epu8|XOP [1]|ammintrin.h|__m128i _mm_haddq_epu8 (\__m128i)|
|[_mm_hadds_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_hadds_epi16)|SSSE3|intrin.h|__m128i _mm_hadds_epi16 (\__m128i、\__m128i)|
|[_mm_hadds_pi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_hadds_pi16)|SSSE3|intrin.h|__m64 _mm_hadds_pi16 (\__m64、\__m64)|
|_mm_haddw_epi8|XOP [1]|ammintrin.h|__m128i _mm_haddw_epi8 (\__m128i)|
|_mm_haddw_epu8|XOP [1]|ammintrin.h|__m128i _mm_haddw_epu8 (\__m128i)|
|[_mm_hsub_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_hsub_epi16)|SSSE3|intrin.h|__m128i _mm_hsub_epi16 (\__m128i、\__m128i)|
|[_mm_hsub_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_hsub_epi32)|SSSE3|intrin.h|__m128i _mm_hsub_epi32 (\__m128i、\__m128i)|
|[_mm_hsub_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_hsub_pd)|SSE3|intrin.h|__m128d _mm_hsub_pd (\__m128d、\__m128d)|
|[_mm_hsub_pi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_hsub_pi16)|SSSE3|intrin.h|__m64 _mm_hsub_pi16 (\__m64、\__m64)|
|[_mm_hsub_pi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_hsub_pi32)|SSSE3|intrin.h|__m64 _mm_hsub_pi32 (\__m64、\__m64)|
|[_mm_hsub_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_hsub_ps)|SSE3|intrin.h|__m128 _mm_hsub_ps (\__m128、\__m128)|
|_mm_hsubd_epi16|XOP [1]|ammintrin.h|__m128i _mm_hsubd_epi16 (\__m128i)|
|_mm_hsubq_epi32|XOP [1]|ammintrin.h|__m128i _mm_hsubq_epi32 (\__m128i)|
|[_mm_hsubs_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_hsubs_epi16)|SSSE3|intrin.h|__m128i _mm_hsubs_epi16 (\__m128i、\__m128i)|
|[_mm_hsubs_pi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_hsubs_pi16)|SSSE3|intrin.h|__m64 _mm_hsubs_pi16 (\__m64、\__m64)|
|_mm_hsubw_epi8|XOP [1]|ammintrin.h|__m128i _mm_hsubw_epi8 (\__m128i)|
|[_mm_i32gather_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_i32gather_epi32)|AVX2 [2]|immintrin.h|__m128i _mm_i32gather_epi32 (int const \*、\__m128i、const int)|
|[_mm_i32gather_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_i32gather_epi64)|AVX2 [2]|immintrin.h|__m128i _mm_i32gather_epi64 (\__int64 const \*、\__m128i、const int)|
|[_mm_i32gather_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_i32gather_pd)|AVX2 [2]|immintrin.h|__m128d _mm_i32gather_pd (二重 const \*、\__m128i、const int)|
|[_mm_i32gather_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_i32gather_ps)|AVX2 [2]|immintrin.h|__m128 _mm_i32gather_ps (float const \*、\__m128i、const int)|
|[_mm_i64gather_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_i64gather_epi32)|AVX2 [2]|immintrin.h|__m128i _mm_i64gather_epi32 (int const \*、\__m128i、const int)|
|[_mm_i64gather_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_i64gather_epi64)|AVX2 [2]|immintrin.h|__m128i _mm_i64gather_epi64 (\__int64 const \*、\__m128i、const int)|
|[_mm_i64gather_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_i64gather_pd)|AVX2 [2]|immintrin.h|__m128d _mm_i64gather_pd (二重 const \*、\__m128i、const int)|
|[_mm_i64gather_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_i64gather_ps)|AVX2 [2]|immintrin.h|__m128 _mm_i64gather_ps (float const \*、\__m128i、const int)|
|[_mm_insert_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_insert_epi16)|SSE2|intrin.h|__m128i _mm_insert_epi16 (\__m128i、int、int)|
|[_mm_insert_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_insert_epi32)|SSE41|intrin.h|__m128i _mm_insert_epi32 (\__m128i、int、const int)|
|[_mm_insert_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_insert_epi8)|SSE41|intrin.h|__m128i _mm_insert_epi8 (\__m128i、int、const int)|
|[_mm_insert_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_insert_ps)|SSE41|intrin.h|__m128 _mm_insert_ps (\__m128、\__m128、const int)|
|[_mm_insert_si64](mm-insert-si64-mm-inserti-si64.md)|SSE4a|intrin.h|__m128i _mm_insert_si64 (\__m128i、\__m128i)|
|[_mm_inserti_si64](mm-insert-si64-mm-inserti-si64.md)|SSE4a|intrin.h|__m128i _mm_inserti_si64 (\__m128i、\__m128i、int、int)|
|[_mm_lddqu_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_lddqu_si128)|SSE3|intrin.h|__m128i _mm_lddqu_si128 (\__m128i const\*)|
|[_mm_lfence](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_lfence)|SSE2|intrin.h|void _mm_lfence(void)|
|[_mm_load_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_load_pd)|SSE2|intrin.h|__m128d _mm_load_pd (ダブル\*)|
|[_mm_load_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_load_ps)|SSE|intrin.h|__m128 _mm_load_ps (float\*)|
|[_mm_load_ps1](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_load_ps1)|SSE|intrin.h|__m128 _mm_load_ps1 (float\*)|
|[_mm_load_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_load_sd)|SSE2|intrin.h|__m128d _mm_load_sd (ダブル\*)|
|[_mm_load_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_load_si128)|SSE2|intrin.h|__m128i _mm_load_si128 (\__m128i\*)|
|[_mm_load_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_load_ss)|SSE|intrin.h|__m128 _mm_load_ss (float\*)|
|[_mm_load1_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_load1_pd)|SSE2|intrin.h|__m128d _mm_load1_pd (ダブル\*)|
|[_mm_loaddup_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_loaddup_pd)|SSE3|intrin.h|__m128d _mm_loaddup_pd (二重 const\*)|
|[_mm_loadh_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_loadh_pd)|SSE2|intrin.h|__m128d _mm_loadh_pd (\__m128d、ダブル\*)|
|[_mm_loadh_pi](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_loadh_pi)|SSE|intrin.h|__m128 _mm_loadh_pi (\__m128、\__m64\*)|
|[_mm_loadl_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_loadl_epi64)|SSE2|intrin.h|__m128i _mm_loadl_epi64 (\__m128i\*)|
|[_mm_loadl_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_loadl_pd)|SSE2|intrin.h|__m128d _mm_loadl_pd (\__m128d、ダブル\*)|
|[_mm_loadl_pi](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_loadl_pi)|SSE|intrin.h|__m128 _mm_loadl_pi (\__m128、\__m64\*)|
|[_mm_loadr_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_loadr_pd)|SSE2|intrin.h|__m128d _mm_loadr_pd (ダブル\*)|
|[_mm_loadr_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_loadr_ps)|SSE|intrin.h|__m128 _mm_loadr_ps (float\*)|
|[_mm_loadu_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_loadu_pd)|SSE2|intrin.h|__m128d _mm_loadu_pd (ダブル\*)|
|[_mm_loadu_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_loadu_ps)|SSE|intrin.h|__m128 _mm_loadu_ps (float\*)|
|[_mm_loadu_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_loadu_si128)|SSE2|intrin.h|__m128i _mm_loadu_si128 (\__m128i\*)|
|_mm_macc_epi16|XOP [1]|ammintrin.h|__m128i _mm_macc_epi16 (\__m128i、\__m128i、\__m128i)|
|_mm_macc_epi32|XOP [1]|ammintrin.h|__m128i _mm_macc_epi32 (\__m128i、\__m128i、\__m128i)|
|_mm_macc_pd|FMA4 [1]|ammintrin.h|__m128d _mm_macc_pd (\__m128d、\__m128d、\__m128d)|
|_mm_macc_ps|FMA4 [1]|ammintrin.h|__m128 _mm_macc_ps (\__m128、\__m128、\__m128)|
|_mm_macc_sd|FMA4 [1]|ammintrin.h|__m128d _mm_macc_sd (\__m128d、\__m128d、\__m128d)|
|_mm_macc_ss|FMA4 [1]|ammintrin.h|__m128 _mm_macc_ss (\__m128、\__m128、\__m128)|
|_mm_maccd_epi16|XOP [1]|ammintrin.h|__m128i _mm_maccd_epi16 (\__m128i、\__m128i、\__m128i)|
|_mm_macchi_epi32|XOP [1]|ammintrin.h|__m128i _mm_macchi_epi32 (\__m128i、\__m128i、\__m128i)|
|_mm_macclo_epi32|XOP [1]|ammintrin.h|__m128i _mm_macclo_epi32 (\__m128i、\__m128i、\__m128i)|
|_mm_maccs_epi16|XOP [1]|ammintrin.h|__m128i _mm_maccs_epi16 (\__m128i、\__m128i、\__m128i)|
|_mm_maccs_epi32|XOP [1]|ammintrin.h|__m128i _mm_maccs_epi32 (\__m128i、\__m128i、\__m128i)|
|_mm_maccsd_epi16|XOP [1]|ammintrin.h|__m128i _mm_maccsd_epi16 (\__m128i、\__m128i、\__m128i)|
|_mm_maccshi_epi32|XOP [1]|ammintrin.h|__m128i _mm_maccshi_epi32 (\__m128i、\__m128i、\__m128i)|
|_mm_maccslo_epi32|XOP [1]|ammintrin.h|__m128i _mm_maccslo_epi32 (\__m128i、\__m128i、\__m128i)|
|[_mm_madd_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_madd_epi16)|SSE2|intrin.h|__m128i _mm_madd_epi16 (\__m128i、\__m128i)|
|[_mm_madd_pi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_madd_pi16)|MMX|mmintrin .h|__m64 _mm_madd_pi16 (\__m64、\__m64) [3]|
|_mm_maddd_epi16|XOP [1]|ammintrin.h|__m128i _mm_maddd_epi16 (\__m128i、\__m128i、\__m128i)|
|_mm_maddsd_epi16|XOP [1]|ammintrin.h|__m128i _mm_maddsd_epi16 (\__m128i、\__m128i、\__m128i)|
|_mm_maddsub_pd|FMA4 [1]|ammintrin.h|__m128d _mm_maddsub_pd (\__m128d、\__m128d、\__m128d)|
|_mm_maddsub_ps|FMA4 [1]|ammintrin.h|__m128 _mm_maddsub_ps (\__m128、\__m128、\__m128)|
|[_mm_maddubs_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_maddubs_epi16)|SSSE3|intrin.h|__m128i _mm_maddubs_epi16 (\__m128i、\__m128i)|
|[_mm_maddubs_pi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_maddubs_pi16)|SSSE3|intrin.h|__m64 _mm_maddubs_pi16 (\__m64、\__m64)|
|[_mm_mask_i32gather_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mask_i32gather_epi32)|AVX2 [2]|immintrin.h|__m128i _mm_mask_i32gather_epi32 (\__m128i、int const \*、\__m128i、\__m128i、const int)|
|[_mm_mask_i32gather_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mask_i32gather_epi64)|AVX2 [2]|immintrin.h|__m128i _mm_mask_i32gather_epi64 (\__m128i、\__int64 const \*、\__m128i、\__m128i、const int)|
|[_mm_mask_i32gather_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mask_i32gather_pd)|AVX2 [2]|immintrin.h|__m128d _mm_mask_i32gather_pd (\__m128d、二重 const \*、\__m128i、\__m128d、const int)|
|[_mm_mask_i32gather_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mask_i32gather_ps)|AVX2 [2]|immintrin.h|__m128 _mm_mask_i32gather_ps (\__m128、float const \*、\__m128i、\__m128、const int)|
|[_mm_mask_i64gather_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mask_i64gather_epi32)|AVX2 [2]|immintrin.h|__m128i _mm_mask_i64gather_epi32 (\__m128i、int const \*、\__m128i、\__m128i、const int)|
|[_mm_mask_i64gather_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mask_i64gather_epi64)|AVX2 [2]|immintrin.h|__m128i _mm_mask_i64gather_epi64 (\__m128i、\__int64 const \*、\__m128i、\__m128i、const int)|
|[_mm_mask_i64gather_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mask_i64gather_pd)|AVX2 [2]|immintrin.h|__m128d _mm_mask_i64gather_pd (\__m128d、二重 const \*、\__m128i、\__m128d、const int)|
|[_mm_mask_i64gather_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mask_i64gather_ps)|AVX2 [2]|immintrin.h|__m128 _mm_mask_i64gather_ps (\__m128、float const \*、\__m128i、\__m128、const int)|
|[_mm_maskload_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_maskload_epi32)|AVX2 [2]|immintrin.h|__m128i _mm_maskload_epi32 (int const \*、\__m128i)|
|[_mm_maskload_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_maskload_epi64)|AVX2 [2]|immintrin.h|__m128i _mm_maskload_epi64 (\__int64 const \*、\__m128i)|
|[_mm_maskload_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_maskload_pd)|AVX [2]|immintrin.h|__m128d _mm_maskload_pd (二重 const \*、\__m128i)|
|[_mm_maskload_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_maskload_ps)|AVX [2]|immintrin.h|__m128 _mm_maskload_ps (float const \*、\__m128i)|
|[_mm_maskmoveu_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_maskmoveu_si128)|SSE2|intrin.h|void _mm_maskmoveu_si128 (\__m128i、\__m128i、char\*)|
|[_mm_maskstore_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_maskstore_epi32)|AVX2 [2]|immintrin.h|void _mm_maskstore_epi32 (int \*、\__m128i、\__m128i)|
|[_mm_maskstore_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_maskstore_epi64)|AVX2 [2]|immintrin.h|void _mm_maskstore_epi64 (\__int64 \*、\__m128i、\__m128i)|
|[_mm_maskstore_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_maskstore_pd)|AVX [2]|immintrin.h|void _mm_maskstore_pd (double \*、\__m128i、\__m128d)|
|[_mm_maskstore_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_maskstore_ps)|AVX [2]|immintrin.h|void _mm_maskstore_ps (float \*、\__m128i、\__m128)|
|[_mm_max_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_max_epi16)|SSE2|intrin.h|__m128i _mm_max_epi16 (\__m128i、\__m128i)|
|[_mm_max_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_max_epi32)|SSE41|intrin.h|__m128i _mm_max_epi32 (\__m128i、\__m128i)|
|[_mm_max_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_max_epi8)|SSE41|intrin.h|__m128i _mm_max_epi8 (\__m128i、\__m128i)|
|[_mm_max_epu16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_max_epu16)|SSE41|intrin.h|__m128i _mm_max_epu16 (\__m128i、\__m128i)|
|[_mm_max_epu32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_max_epu32)|SSE41|intrin.h|__m128i _mm_max_epu32 (\__m128i、\__m128i)|
|[_mm_max_epu8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_max_epu8)|SSE2|intrin.h|__m128i _mm_max_epu8 (\__m128i、\__m128i)|
|[_mm_max_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_max_pd)|SSE2|intrin.h|__m128d _mm_max_pd (\__m128d、\__m128d)|
|[_mm_max_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_max_ps)|SSE|intrin.h|__m128 _mm_max_ps (\__m128、\__m128)|
|[_mm_max_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_max_sd)|SSE2|intrin.h|__m128d _mm_max_sd (\__m128d、\__m128d)|
|[_mm_max_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_max_ss)|SSE|intrin.h|__m128 _mm_max_ss (\__m128、\__m128)|
|[_mm_mfence](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mfence)|SSE2|intrin.h|void _mm_mfence(void)|
|[_mm_min_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_min_epi16)|SSE2|intrin.h|__m128i _mm_min_epi16 (\__m128i、\__m128i)|
|[_mm_min_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_min_epi32)|SSE41|intrin.h|__m128i _mm_min_epi32 (\__m128i、\__m128i)|
|[_mm_min_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_min_epi8)|SSE41|intrin.h|__m128i _mm_min_epi8 (\__m128i、\__m128i)|
|[_mm_min_epu16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_min_epu16)|SSE41|intrin.h|__m128i _mm_min_epu16 (\__m128i、\__m128i)|
|[_mm_min_epu32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_min_epu32)|SSE41|intrin.h|__m128i _mm_min_epu32 (\__m128i、\__m128i)|
|[_mm_min_epu8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_min_epu8)|SSE2|intrin.h|__m128i _mm_min_epu8 (\__m128i、\__m128i)|
|[_mm_min_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_min_pd)|SSE2|intrin.h|__m128d _mm_min_pd (\__m128d、\__m128d)|
|[_mm_min_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_min_ps)|SSE|intrin.h|__m128 _mm_min_ps (\__m128、\__m128)|
|[_mm_min_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_min_sd)|SSE2|intrin.h|__m128d _mm_min_sd (\__m128d、\__m128d)|
|[_mm_min_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_min_ss)|SSE|intrin.h|__m128 _mm_min_ss (\__m128、\__m128)|
|[_mm_minpos_epu16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_minpos_epu16)|SSE41|intrin.h|__m128i _mm_minpos_epu16 (\__m128i)|
|[_mm_monitor](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_monitor)|SSE3|intrin.h|void _mm_monitor(void const*, unsigned int, unsigned int)|
|[_mm_move_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_move_epi64)|SSE2|intrin.h|__m128i _mm_move_epi64 (\__m128i)|
|[_mm_move_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_move_sd)|SSE2|intrin.h|__m128d _mm_move_sd (\__m128d、\__m128d)|
|[_mm_move_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_move_ss)|SSE|intrin.h|__m128 _mm_move_ss (\__m128、\__m128)|
|[_mm_movedup_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_movedup_pd)|SSE3|intrin.h|__m128d _mm_movedup_pd (\__m128d)|
|[_mm_movehdup_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_movehdup_ps)|SSE3|intrin.h|__m128 _mm_movehdup_ps (\__m128)|
|[_mm_movehl_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_movehl_ps)|SSE|intrin.h|__m128 _mm_movehl_ps (\__m128、\__m128)|
|[_mm_moveldup_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_moveldup_ps)|SSE3|intrin.h|__m128 _mm_moveldup_ps (\__m128)|
|[_mm_movelh_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_movelh_ps)|SSE|intrin.h|__m128 _mm_movelh_ps (\__m128、\__m128)|
|[_mm_movemask_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_movemask_epi8)|SSE2|intrin.h|int _mm_movemask_epi8 (\__m128i)|
|[_mm_movemask_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_movemask_pd)|SSE2|intrin.h|int _mm_movemask_pd (\__m128d)|
|[_mm_movemask_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_movemask_ps)|SSE|intrin.h|int _mm_movemask_ps (\__m128)|
|[_mm_movepi64_pi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_movepi64_pi64)|SSE2|intrin.h|__m64 _mm_movepi64_pi64 (\__m128i)|
|[_mm_movpi64_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_movpi64_epi64)|SSE2|intrin.h|__m128i _mm_movpi64_epi64 (\__m64)|
|[_mm_mpsadbw_epu8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mpsadbw_epu8)|SSE41|intrin.h|__m128i _mm_mpsadbw_epu8 (\__m128i、\__m128i、const int)|
|_mm_msub_pd|FMA4 [1]|ammintrin.h|__m128d _mm_msub_pd (\__m128d、\__m128d、\__m128d)|
|_mm_msub_ps|FMA4 [1]|ammintrin.h|__m128 _mm_msub_ps (\__m128、\__m128、\__m128)|
|_mm_msub_sd|FMA4 [1]|ammintrin.h|__m128d _mm_msub_sd (\__m128d、\__m128d、\__m128d)|
|_mm_msub_ss|FMA4 [1]|ammintrin.h|__m128 _mm_msub_ss (\__m128、\__m128、\__m128)|
|_mm_msubadd_pd|FMA4 [1]|ammintrin.h|__m128d _mm_msubadd_pd (\__m128d、\__m128d、\__m128d)|
|_mm_msubadd_ps|FMA4 [1]|ammintrin.h|__m128 _mm_msubadd_ps (\__m128、\__m128、\__m128)|
|[_mm_mul_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mul_epi32)|SSE41|intrin.h|__m128i _mm_mul_epi32 (\__m128i、\__m128i)|
|[_mm_mul_epu32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mul_epu32)|SSE2|intrin.h|__m128i _mm_mul_epu32 (\__m128i、\__m128i)|
|[_mm_mul_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mul_pd)|SSE2|intrin.h|__m128d _mm_mul_pd (\__m128d、\__m128d)|
|[_mm_mul_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mul_ps)|SSE|intrin.h|__m128 _mm_mul_ps (\__m128、\__m128)|
|[_mm_mul_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mul_sd)|SSE2|intrin.h|__m128d _mm_mul_sd (\__m128d、\__m128d)|
|[_mm_mul_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mul_ss)|SSE|intrin.h|__m128 _mm_mul_ss (\__m128、\__m128)|
|[_mm_mul_su32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mul_su32)|SSE2|intrin.h|__m64 _mm_mul_su32 (\__m64、\__m64)|
|[_mm_mulhi_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mulhi_epi16)|SSE2|intrin.h|__m128i _mm_mulhi_epi16 (\__m128i、\__m128i)|
|[_mm_mulhi_epu16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mulhi_epu16)|SSE2|intrin.h|__m128i _mm_mulhi_epu16 (\__m128i、\__m128i)|
|[_mm_mulhi_pi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mulhi_pi16)|MMX|mmintrin .h|__m64 _mm_mulhi_pi16 (\__m64、\__m64) [3]|
|[_mm_mulhrs_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mulhrs_epi16)|SSSE3|intrin.h|__m128i _mm_mulhrs_epi16 (\__m128i、\__m128i)|
|[_mm_mulhrs_pi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mulhrs_pi16)|SSSE3|intrin.h|__m64 _mm_mulhrs_pi16 (\__m64、\__m64)|
|[_mm_mullo_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mullo_epi16)|SSE2|intrin.h|__m128i _mm_mullo_epi16 (\__m128i、\__m128i)|
|[_mm_mullo_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mullo_epi32)|SSE41|intrin.h|__m128i _mm_mullo_epi32 (\__m128i、\__m128i)|
|[_mm_mullo_pi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mullo_pi16)|MMX|mmintrin .h|__m64 _mm_mullo_pi16 (\__m64、\__m64) [3]|
|[_mm_mwait](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_mwait)|SSE3|intrin.h|void _mm_mwait(unsigned int, unsigned int)|
|_mm_nmacc_pd|FMA4 [1]|ammintrin.h|__m128d _mm_nmacc_pd (\__m128d、\__m128d、\__m128d)|
|_mm_nmacc_ps|FMA4 [1]|ammintrin.h|__m128 _mm_nmacc_ps (\__m128、\__m128、\__m128)|
|_mm_nmacc_sd|FMA4 [1]|ammintrin.h|__m128d _mm_nmacc_sd (\__m128d、\__m128d、\__m128d)|
|_mm_nmacc_ss|FMA4 [1]|ammintrin.h|__m128 _mm_nmacc_ss (\__m128、\__m128、\__m128)|
|_mm_nmsub_pd|FMA4 [1]|ammintrin.h|__m128d _mm_nmsub_pd (\__m128d、\__m128d、\__m128d)|
|_mm_nmsub_ps|FMA4 [1]|ammintrin.h|__m128 _mm_nmsub_ps (\__m128、\__m128、\__m128)|
|_mm_nmsub_sd|FMA4 [1]|ammintrin.h|__m128d _mm_nmsub_sd (\__m128d、\__m128d、\__m128d)|
|_mm_nmsub_ss|FMA4 [1]|ammintrin.h|__m128 _mm_nmsub_ss (\__m128、\__m128、\__m128)|
|[_mm_or_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_or_pd)|SSE2|intrin.h|__m128d _mm_or_pd (\__m128d、\__m128d)|
|[_mm_or_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_or_ps)|SSE|intrin.h|__m128 _mm_or_ps (\__m128、\__m128)|
|[_mm_or_si64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_or_si64)|MMX|mmintrin .h|__m64 _mm_or_si64 (\__m64、\__m64) [3]|
|[_mm_or_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_or_si128)|SSE2|intrin.h|__m128i _mm_or_si128 (\__m128i、\__m128i)|
|[_mm_packs_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_packs_epi16)|SSE2|intrin.h|__m128i _mm_packs_epi16 (\__m128i、\__m128i)|
|[_mm_packs_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_packs_epi32)|SSE2|intrin.h|__m128i _mm_packs_epi32 (\__m128i、\__m128i)|
|[_mm_packs_pi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_packs_pi16)|MMX|mmintrin .h|__m64 _mm_packs_pi16 (__m64、__m64) [3]|
|[_mm_packs_pi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_packs_pi32)|MMX|mmintrin .h|__m64 _mm_packs_pi32 (__m64、__m64) [3]|
|[_mm_packs_pu16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_packs_pu16)|MMX|mmintrin .h|__m64 _mm_packs_pu16 (__m64、__m64) [3]|
|[_mm_packus_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_packus_epi16)|SSE2|intrin.h|__m128i _mm_packus_epi16 (\__m128i、\__m128i)|
|[_mm_packus_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_packus_epi32)|SSE41|intrin.h|__m128i _mm_packus_epi32 (\__m128i、\__m128i)|
|[_mm_pause](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_pause)|SSE2|intrin.h|void _mm_pause(void)|
|_mm_perm_epi8|XOP [1]|ammintrin.h|__m128i _mm_perm_epi8 (\__m128i、\__m128i、\__m128i)|
|[_mm_permute_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_permute_pd)|AVX [2]|immintrin.h|__m128d _mm_permute_pd (\__m128d、int)|
|[_mm_permute_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_permute_ps)|AVX [2]|immintrin.h|__m128 _mm_permute_ps (\__m128、int)|
|_mm_permute2_pd|XOP [1]|ammintrin.h|__m128d _mm_permute2_pd (\__m128d、\__m128d、\__m128i、int)|
|_mm_permute2_ps|XOP [1]|ammintrin.h|__m128 _mm_permute2_ps (\__m128、\__m128、\__m128i、int)|
|[_mm_permutevar_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_permutevar_pd)|AVX [2]|immintrin.h|__m128d _mm_permutevar_pd (\__m128d、\__m128i)|
|[_mm_permutevar_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_permutevar_ps)|AVX [2]|immintrin.h|__m128 _mm_permutevar_ps (\__m128、\__m128i)|
|[_mm_popcnt_u32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_popcnt_u32)|POPCNT|intrin.h|int _mm_popcnt_u32(unsigned int)|
|[_mm_prefetch](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_prefetch)|SSE|intrin.h|void _mm_prefetch (char *, int)|
|[_mm_rcp_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_rcp_ps)|SSE|intrin.h|__m128 _mm_rcp_ps (\__m128)|
|[_mm_rcp_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_rcp_ss)|SSE|intrin.h|__m128 _mm_rcp_ss (\__m128)|
|_mm_rot_epi16|XOP [1]|ammintrin.h|__m128i _mm_rot_epi16 (\__m128i、\__m128i)|
|_mm_rot_epi32|XOP [1]|ammintrin.h|__m128i _mm_rot_epi32 (\__m128i、\__m128i)|
|_mm_rot_epi64|XOP [1]|ammintrin.h|__m128i _mm_rot_epi64 (\__m128i、\__m128i)|
|_mm_rot_epi8|XOP [1]|ammintrin.h|__m128i _mm_rot_epi8 (\__m128i、\__m128i)|
|_mm_roti_epi16|XOP [1]|ammintrin.h|__m128i _mm_rot_epi16 (\__m128i、int)|
|_mm_roti_epi32|XOP [1]|ammintrin.h|__m128i _mm_rot_epi32 (\__m128i、int)|
|_mm_roti_epi64|XOP [1]|ammintrin.h|__m128i _mm_rot_epi64 (\__m128i、int)|
|_mm_roti_epi8|XOP [1]|ammintrin.h|__m128i _mm_rot_epi8 (\__m128i、int)|
|[_mm_round_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_round_pd)|SSE41|intrin.h|__m128d _mm_round_pd (\__m128d、const int)|
|[_mm_round_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_round_ps)|SSE41|intrin.h|__m128 _mm_round_ps (\__m128、const int)|
|[_mm_round_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_round_sd)|SSE41|intrin.h|__m128d _mm_round_sd (\__m128d、\__m128d、const int)|
|[_mm_round_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_round_ss)|SSE41|intrin.h|__m128 _mm_round_ss (\__m128、\__m128、const int)|
|[_mm_rsqrt_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_rsqrt_ps)|SSE|intrin.h|__m128 _mm_rsqrt_ps (\__m128)|
|[_mm_rsqrt_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_rsqrt_ss)|SSE|intrin.h|__m128 _mm_rsqrt_ss (\__m128)|
|[_mm_sad_epu8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sad_epu8)|SSE2|intrin.h|__m128i _mm_sad_epu8 (\__m128i、\__m128i)|
|[_mm_set_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_set_epi16)|SSE2|intrin.h|__m128i _mm_set_epi16 (short、short、short、short、short、short、short、short)|
|[_mm_set_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_set_epi32)|SSE2|intrin.h|__m128i _mm_set_epi32 (int, int, int, int)|
|[_mm_set_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_set_epi64)|SSE2|intrin.h|__m128i _mm_set_epi64 (\__m64、\__m64)|
|[_mm_set_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_set_epi8)|SSE2|intrin.h|__m128i _mm_set_epi8 (char, char, char, char, char, char, char, char, char, char, char, char, char, char, char, char)|
|[_mm_set_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_set_pd)|SSE2|intrin.h|__m128d _mm_set_pd (double、double)|
|[_mm_set_pi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_set_pi16)|MMX|intrin.h|__m64 _mm_set_pi16 (short、short、short、short)|
|[_mm_set_pi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_set_pi32)|MMX|intrin.h|__m64 _mm_set_pi32 (int, int)|
|[_mm_set_pi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_set_pi8)|MMX|intrin.h|__m64 _mm_set_pi8 (char、char、char、char、char、char、char、char)|
|[_mm_set_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_set_ps)|SSE|intrin.h|__m128 _mm_set_ps (float、float、float、float)|
|[_mm_set_ps1](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_set_ps1)|SSE|intrin.h|__m128 _mm_set_ps1(float)|
|[_mm_set_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_set_sd)|SSE2|intrin.h|__m128d _mm_set_sd(double)|
|[_mm_set_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_set_ss)|SSE|intrin.h|__m128 _mm_set_ss(float)|
|[_mm_set1_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_set1_epi16)|SSE2|intrin.h|__m128i _mm_set1_epi16(short)|
|[_mm_set1_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_set1_epi32)|SSE2|intrin.h|__m128i _mm_set1_epi32(int)|
|[_mm_set1_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_set1_epi64)|SSE2|intrin.h|__m128i _mm_set1_epi64 (\__m64)|
|[_mm_set1_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_set1_epi8)|SSE2|intrin.h|__m128i _mm_set1_epi8(char)|
|[_mm_set1_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_set1_pd)|SSE2|intrin.h|__m128d _mm_set1_pd(double)|
|[_mm_set1_pi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_set1_pi16)|MMX|intrin.h|__m64 _mm_set1_pi16(short)|
|[_mm_set1_pi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_set1_pi32)|MMX|intrin.h|__m64 _mm_set1_pi32(int)|
|[_mm_set1_pi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_set1_pi8)|MMX|intrin.h|__m64 _mm_set1_pi8(char)|
|[_mm_setcsr](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_setcsr)|SSE|intrin.h|void _mm_setcsr(unsigned int)|
|_mm_setl_epi64|SSE2|intrin.h|__m128i _mm_setl_epi64 (\__m128i)|
|[_mm_setr_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_setr_epi16)|SSE2|intrin.h|__m128i _mm_setr_epi16 (short、short、short、short、short、short、short、short)|
|[_mm_setr_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_setr_epi32)|SSE2|intrin.h|__m128i _mm_setr_epi32 (int, int, int, int)|
|[_mm_setr_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_setr_epi64)|SSE2|intrin.h|__m128i _mm_setr_epi64 (\__m64、\__m64)|
|[_mm_setr_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_setr_epi8)|SSE2|intrin.h|__m128i _mm_setr_epi8 (char, char, char, char, char, char, char, char, char, char, char, char, char, char, char, char)|
|[_mm_setr_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_setr_pd)|SSE2|intrin.h|__m128d _mm_setr_pd (double、double)|
|[_mm_setr_pi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_setr_pi16)|MMX|intrin.h|__m64 _mm_setr_pi16 (short、short、short、short)|
|[_mm_setr_pi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_setr_pi32)|MMX|intrin.h|__m64 _mm_setr_pi32 (int, int)|
|[_mm_setr_pi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_setr_pi8)|MMX|intrin.h|__m64 _mm_setr_pi8 (char、char、char、char、char、char、char、char)|
|[_mm_setr_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_setr_ps)|SSE|intrin.h|__m128 _mm_setr_ps (float、float、float、float)|
|[_mm_setzero_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_setzero_pd)|SSE2|intrin.h|__m128d _mm_setzero_pd(void)|
|[_mm_setzero_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_setzero_ps)|SSE|intrin.h|__m128 _mm_setzero_ps(void)|
|[_mm_setzero_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_setzero_si128)|SSE2|intrin.h|__m128i _mm_setzero_si128(void)|
|[_mm_setzero_si64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_setzero_si64)|MMX|intrin.h|__m64 _mm_setzero_si64(void)|
|[_mm_sfence](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sfence)|SSE|intrin.h|void _mm_sfence(void)|
|_mm_sha_epi16|XOP [1]|ammintrin.h|__m128i _mm_sha_epi16 (\__m128i、\__m128i)|
|_mm_sha_epi32|XOP [1]|ammintrin.h|__m128i _mm_sha_epi32 (\__m128i、\__m128i)|
|_mm_sha_epi64|XOP [1]|ammintrin.h|__m128i _mm_sha_epi64 (\__m128i、\__m128i)|
|_mm_sha_epi8|XOP [1]|ammintrin.h|__m128i _mm_sha_epi8 (\__m128i、\__m128i)|
|_mm_shl_epi16|XOP [1]|ammintrin.h|__m128i _mm_shl_epi16 (\__m128i、\__m128i)|
|_mm_shl_epi32|XOP [1]|ammintrin.h|__m128i _mm_shl_epi32 (\__m128i、\__m128i)|
|_mm_shl_epi64|XOP [1]|ammintrin.h|__m128i _mm_shl_epi64 (\__m128i、\__m128i)|
|_mm_shl_epi8|XOP [1]|ammintrin.h|__m128i _mm_shl_epi8 (\__m128i、\__m128i)|
|[_mm_shuffle_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_shuffle_epi32)|SSE2|intrin.h|__m128i _mm_shuffle_epi32 (\__m128i、int)|
|[_mm_shuffle_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_shuffle_epi8)|SSSE3|intrin.h|__m128i _mm_shuffle_epi8 (\__m128i、\__m128i)|
|[_mm_shuffle_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_shuffle_pd)|SSE2|intrin.h|__m128d _mm_shuffle_pd (\__m128d、\__m128d、int)|
|[_mm_shuffle_pi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_shuffle_pi8)|SSSE3|intrin.h|__m64 _mm_shuffle_pi8 (\__m64、\__m64)|
|[_mm_shuffle_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_shuffle_ps)|SSE|intrin.h|__m128 _mm_shuffle_ps (\__m128、\__m128、unsigned int)|
|[_mm_shufflehi_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_shufflehi_epi16)|SSE2|intrin.h|__m128i _mm_shufflehi_epi16 (\__m128i、int)|
|[_mm_shufflelo_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_shufflelo_epi16)|SSE2|intrin.h|__m128i _mm_shufflelo_epi16 (\__m128i、int)|
|[_mm_sign_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sign_epi16)|SSSE3|intrin.h|__m128i _mm_sign_epi16 (\__m128i、\__m128i)|
|[_mm_sign_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sign_epi32)|SSSE3|intrin.h|__m128i _mm_sign_epi32 (\__m128i、\__m128i)|
|[_mm_sign_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sign_epi8)|SSSE3|intrin.h|__m128i _mm_sign_epi8 (\__m128i、\__m128i)|
|[_mm_sign_pi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sign_pi16)|SSSE3|intrin.h|__m64 _mm_sign_pi16 (\__m64、\__m64)|
|[_mm_sign_pi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sign_pi32)|SSSE3|intrin.h|__m64 _mm_sign_pi32 (\__m64、\__m64)|
|[_mm_sign_pi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sign_pi8)|SSSE3|intrin.h|__m64 _mm_sign_pi8 (\__m64、\__m64)|
|[_mm_sll_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sll_epi16)|SSE2|intrin.h|__m128i _mm_sll_epi16 (\__m128i、\__m128i)|
|[_mm_sll_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sll_epi32)|SSE2|intrin.h|__m128i _mm_sll_epi32 (\__m128i、\__m128i)|
|[_mm_sll_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sll_epi64)|SSE2|intrin.h|__m128i _mm_sll_epi64 (\__m128i、\__m128i)|
|[_mm_sll_pi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sll_pi16)|MMX|mmintrin .h|__m64 _mm_sll_pi16 (\__m64、\__m64) [3]|
|[_mm_sll_pi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sll_pi32)|MMX|mmintrin .h|__m64 _mm_sll_pi32 (\__m64、\__m64) [3]|
|[_mm_sll_si64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sll_si64)|MMX|mmintrin .h|__m64 _mm_sll_si64 (\__m64、\__m64) [3]|
|[_mm_slli_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_slli_epi16)|SSE2|intrin.h|__m128i _mm_slli_epi16 (\__m128i、int)|
|[_mm_slli_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_slli_epi32)|SSE2|intrin.h|__m128i _mm_slli_epi32 (\__m128i、int)|
|[_mm_slli_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_slli_epi64)|SSE2|intrin.h|__m128i _mm_slli_epi64 (\__m128i、int)|
|[_mm_slli_pi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_slli_pi16)|MMX|mmintrin .h|__m64 _mm_slli_pi16 (\__m64、int) [3]|
|[_mm_slli_pi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_slli_pi32)|MMX|mmintrin .h|__m64 _mm_slli_pi32 (\__m64、int) [3]|
|[_mm_slli_si64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_slli_si64)|MMX|mmintrin .h|__m64 _mm_slli_si64 (\__m64、int) [3]|
|[_mm_slli_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_slli_si128)|SSE2|intrin.h|__m128i _mm_slli_si128 (\__m128i、int)|
|[_mm_sllv_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sllv_epi32)|AVX2 [2]|immintrin.h|__m128i _mm_sllv_epi32 (\__m128i、\__m128i)|
|[_mm_sllv_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sllv_epi64)|AVX2 [2]|immintrin.h|__m128i _mm_sllv_epi64 (\__m128i、\__m128i)|
|[_mm_sqrt_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sqrt_pd)|SSE2|intrin.h|__m128d _mm_sqrt_pd (\__m128d)|
|[_mm_sqrt_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sqrt_ps)|SSE|intrin.h|__m128 _mm_sqrt_ps (\__m128)|
|[_mm_sqrt_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sqrt_sd)|SSE2|intrin.h|__m128d _mm_sqrt_sd (\__m128d、\__m128d)|
|[_mm_sqrt_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sqrt_ss)|SSE|intrin.h|__m128 _mm_sqrt_ss (\__m128)|
|[_mm_sra_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sra_epi16)|SSE2|intrin.h|__m128i _mm_sra_epi16 (\__m128i、\__m128i)|
|[_mm_sra_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sra_epi32)|SSE2|intrin.h|__m128i _mm_sra_epi32 (\__m128i、\__m128i)|
|[_mm_sra_pi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sra_pi16)|MMX|mmintrin .h|__m64 _mm_sra_pi16 (\__m64、\__m64) [3]|
|[_mm_sra_pi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sra_pi32)|MMX|mmintrin .h|__m64 _mm_sra_pi32 (\__m64、\__m64) [3]|
|[_mm_srai_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_srai_epi16)|SSE2|intrin.h|__m128i _mm_srai_epi16 (\__m128i、int)|
|[_mm_srai_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_srai_epi32)|SSE2|intrin.h|__m128i _mm_srai_epi32 (\__m128i、int)|
|[_mm_srai_pi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_srai_pi16)|MMX|mmintrin .h|__m64 _mm_srai_pi16 (\__m64、int) [3]|
|[_mm_srai_pi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_srai_pi32)|MMX|mmintrin .h|__m64 _mm_srai_pi32 (\__m64、int) [3]|
|[_mm_srav_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_srav_epi32)|AVX2 [2]|immintrin.h|__m128i _mm_srav_epi32 (\__m128i、\__m128i)|
|[_mm_srl_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_srl_epi16)|SSE2|intrin.h|__m128i _mm_srl_epi16 (\__m128i、\__m128i)|
|[_mm_srl_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_srl_epi32)|SSE2|intrin.h|__m128i _mm_srl_epi32 (\__m128i、\__m128i)|
|[_mm_srl_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_srl_epi64)|SSE2|intrin.h|__m128i _mm_srl_epi64 (\__m128i、\__m128i)|
|[_mm_srl_pi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_srl_pi16)|MMX|mmintrin .h|__m64 _mm_srl_pi16 (\__m64、\__m64) [3]|
|[_mm_srl_pi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_srl_pi32)|MMX|mmintrin .h|__m64 _mm_srl_pi32 (\__m64、\__m64) [3]|
|[_mm_srl_si64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_srl_si64)|MMX|mmintrin .h|__m64 _mm_srl_si64 (\__m64、\__m64) [3]|
|[_mm_srli_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_srli_epi16)|SSE2|intrin.h|__m128i _mm_srli_epi16 (\__m128i、int)|
|[_mm_srli_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_srli_epi32)|SSE2|intrin.h|__m128i _mm_srli_epi32 (\__m128i、int)|
|[_mm_srli_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_srli_epi64)|SSE2|intrin.h|__m128i _mm_srli_epi64 (\__m128i、int)|
|[_mm_srli_pi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_srli_pi16)|MMX|mmintrin .h|__m64 _mm_srli_pi16 (\__m64、int) [3]|
|[_mm_srli_pi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_srli_pi32)|MMX|mmintrin .h|__m64 _mm_srli_pi32 (\__m64、int) [3]|
|[_mm_srli_si64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_srli_si64)|MMX|mmintrin .h|__m64 _mm_srli_si64 (\__m64、int) [3]|
|[_mm_srli_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_srli_si128)|SSE2|intrin.h|__m128i _mm_srli_si128 (\__m128i、int)|
|[_mm_srlv_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_srlv_epi32)|AVX2 [2]|immintrin.h|__m128i _mm_srlv_epi32 (\__m128i、\__m128i)|
|[_mm_srlv_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_srlv_epi64)|AVX2 [2]|immintrin.h|__m128i _mm_srlv_epi64 (\__m128i、\__m128i)|
|[_mm_store_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_store_pd)|SSE2|intrin.h|void _mm_store_pd (double\*、\__m128d)|
|[_mm_store_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_store_ps)|SSE|intrin.h|void _mm_store_ps (float\*、\__m128)|
|[_mm_store_ps1](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_store_ps1)|SSE|intrin.h|void _mm_store_ps1 (float\*、\__m128)|
|[_mm_store_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_store_sd)|SSE2|intrin.h|void _mm_store_sd (double\*、\__m128d)|
|[_mm_store_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_store_si128)|SSE2|intrin.h|void _mm_store_si128 (\__m128i\*、\__m128i)|
|[_mm_store_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_store_ss)|SSE|intrin.h|void _mm_store_ss (float\*、\__m128)|
|[_mm_store1_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_store1_pd)|SSE2|intrin.h|void _mm_store1_pd (double\*、\__m128d)|
|[_mm_storeh_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_storeh_pd)|SSE2|intrin.h|void _mm_storeh_pd (double\*、\__m128d)|
|[_mm_storeh_pi](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_storeh_pi)|SSE|intrin.h|void _mm_storeh_pi (\__m64\*、\__m128)|
|[_mm_storel_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_storel_epi64)|SSE2|intrin.h|void _mm_storel_epi64 (\__m128i\*、\__m128i)|
|[_mm_storel_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_storel_pd)|SSE2|intrin.h|void _mm_storel_pd (double\*、\__m128d)|
|[_mm_storel_pi](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_storel_pi)|SSE|intrin.h|void _mm_storel_pi (\__m64\*、\__m128)|
|[_mm_storer_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_storer_pd)|SSE2|intrin.h|void _mm_storer_pd (double\*、\__m128d)|
|[_mm_storer_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_storer_ps)|SSE|intrin.h|void _mm_storer_ps (float\*、\__m128)|
|[_mm_storeu_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_storeu_pd)|SSE2|intrin.h|void _mm_storeu_pd (double\*、\__m128d)|
|[_mm_storeu_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_storeu_ps)|SSE|intrin.h|void _mm_storeu_ps (float\*、\__m128)|
|[_mm_storeu_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_storeu_si128)|SSE2|intrin.h|void _mm_storeu_si128 (\__m128i\*、\__m128i)|
|[_mm_stream_load_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_stream_load_si128)|SSE41|intrin.h|__m128i _mm_stream_load_si128 (\__m128i\*)|
|[_mm_stream_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_stream_pd)|SSE2|intrin.h|void _mm_stream_pd (double\*、\__m128d)|
|[_mm_stream_pi](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_stream_pi)|SSE|intrin.h|void _mm_stream_pi (\__m64\*、\__m64)|
|[_mm_stream_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_stream_ps)|SSE|intrin.h|void _mm_stream_ps (float\*、\__m128)|
|[_mm_stream_sd](mm-stream-sd.md)|SSE4a|intrin.h|void _mm_stream_sd (double\*、\__m128d)|
|[_mm_stream_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_stream_si128)|SSE2|intrin.h|void _mm_stream_si128 (\__m128i\*、\__m128i)|
|[_mm_stream_si32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_stream_si32)|SSE2|intrin.h|void _mm_stream_si32 (int\*, int)|
|[_mm_stream_ss](mm-stream-ss.md)|SSE4a|intrin.h|void _mm_stream_ss (float\*、\__m128)|
|[_mm_sub_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sub_epi16)|SSE2|intrin.h|__m128i _mm_sub_epi16 (\__m128i、\__m128i)|
|[_mm_sub_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sub_epi32)|SSE2|intrin.h|__m128i _mm_sub_epi32 (\__m128i、\__m128i)|
|[_mm_sub_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sub_epi64)|SSE2|intrin.h|__m128i _mm_sub_epi64 (\__m128i、\__m128i)|
|[_mm_sub_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sub_epi8)|SSE2|intrin.h|__m128i _mm_sub_epi8 (\__m128i、\__m128i)|
|[_mm_sub_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sub_pd)|SSE2|intrin.h|__m128d _mm_sub_pd (\__m128d、\__m128d)|
|[_mm_sub_pi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sub_pi8)|MMX|mmintrin .h|__m64 _mm_sub_pi8 (\__m64、\__m64) [3]|
|[_mm_sub_pi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sub_pi16)|MMX|mmintrin .h|__m64 _mm_sub_pi16 (\__m64、\__m64) [3]|
|[_mm_sub_pi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sub_pi32)|MMX|mmintrin .h|__m64 _mm_sub_pi32 (\__m64、\__m64) [3]|
|[_mm_sub_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sub_ps)|SSE|intrin.h|__m128 _mm_sub_ps (\__m128、\__m128)|
|[_mm_sub_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sub_sd)|SSE2|intrin.h|__m128d _mm_sub_sd (\__m128d、\__m128d)|
|[_mm_sub_si64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sub_si64)|SSE2|intrin.h|__m64 _mm_sub_si64 (\__m64、\__m64)|
|[_mm_sub_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_sub_ss)|SSE|intrin.h|__m128 _mm_sub_ss (\__m128、\__m128)|
|[_mm_subs_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_subs_epi16)|SSE2|intrin.h|__m128i _mm_subs_epi16 (\__m128i、\__m128i)|
|[_mm_subs_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_subs_epi8)|SSE2|intrin.h|__m128i _mm_subs_epi8 (\__m128i、\__m128i)|
|[_mm_subs_epu16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_subs_epu16)|SSE2|intrin.h|__m128i _mm_subs_epu16 (\__m128i、\__m128i)|
|[_mm_subs_epu8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_subs_epu8)|SSE2|intrin.h|__m128i _mm_subs_epu8 (\__m128i、\__m128i)|
|[_mm_subs_pi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_subs_pi8)|MMX|mmintrin .h|__m64 _mm_subs_pi8 (\__m64、\__m64) [3]|
|[_mm_subs_pi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_subs_pi16)|MMX|mmintrin .h|__m64 _mm_subs_pi16 (\__m64、\__m64) [3]|
|[_mm_subs_pu8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_subs_pu8)|MMX|mmintrin .h|__m64 _mm_subs_pu8 (\__m64、\__m64) [3]|
|[_mm_subs_pu16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_subs_pu16)|MMX|mmintrin .h|__m64 _mm_subs_pu16 (\__m64、\__m64) [3]|
|[_mm_testc_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_testc_pd)|AVX [2]|immintrin.h|int _mm_testc_pd (\__m128d、\__m128d)|
|[_mm_testc_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_testc_ps)|AVX [2]|immintrin.h|int _mm_testc_ps (\__m128、\__m128)|
|[_mm_testc_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_testc_si128)|SSE41|intrin.h|int _mm_testc_si128 (\__m128i、\__m128i)|
|[_mm_testnzc_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_testnzc_pd)|AVX [2]|immintrin.h|int _mm_testnzc_pd (\__m128d、\__m128d)|
|[_mm_testnzc_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_testnzc_ps)|AVX [2]|immintrin.h|int _mm_testnzc_ps (\__m128、\__m128)|
|[_mm_testnzc_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_testnzc_si128)|SSE41|intrin.h|int _mm_testnzc_si128 (\__m128i、\__m128i)|
|[_mm_testz_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_testz_pd)|AVX [2]|immintrin.h|int _mm_testz_pd (\__m128d、\__m128d)|
|[_mm_testz_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_testz_ps)|AVX [2]|immintrin.h|int _mm_testz_ps (\__m128、\__m128)|
|[_mm_testz_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_testz_si128)|SSE41|intrin.h|int _mm_testz_si128 (\__m128i、\__m128i)|
|[_mm_ucomieq_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_ucomieq_sd)|SSE2|intrin.h|int _mm_ucomieq_sd (\__m128d、\__m128d)|
|[_mm_ucomieq_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_ucomieq_ss)|SSE|intrin.h|int _mm_ucomieq_ss (\__m128、\__m128)|
|[_mm_ucomige_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_ucomige_sd)|SSE2|intrin.h|int _mm_ucomige_sd (\__m128d、\__m128d)|
|[_mm_ucomige_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_ucomige_ss)|SSE|intrin.h|int _mm_ucomige_ss (\__m128、\__m128)|
|[_mm_ucomigt_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_ucomigt_sd)|SSE2|intrin.h|int _mm_ucomigt_sd (\__m128d、\__m128d)|
|[_mm_ucomigt_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_ucomigt_ss)|SSE|intrin.h|int _mm_ucomigt_ss (\__m128、\__m128)|
|[_mm_ucomile_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_ucomile_sd)|SSE2|intrin.h|int _mm_ucomile_sd (\__m128d、\__m128d)|
|[_mm_ucomile_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_ucomile_ss)|SSE|intrin.h|int _mm_ucomile_ss (\__m128、\__m128)|
|[_mm_ucomilt_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_ucomilt_sd)|SSE2|intrin.h|int _mm_ucomilt_sd (\__m128d、\__m128d)|
|[_mm_ucomilt_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_ucomilt_ss)|SSE|intrin.h|int _mm_ucomilt_ss (\__m128、\__m128)|
|[_mm_ucomineq_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_ucomineq_sd)|SSE2|intrin.h|int _mm_ucomineq_sd (\__m128d、\__m128d)|
|[_mm_ucomineq_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_ucomineq_ss)|SSE|intrin.h|int _mm_ucomineq_ss (\__m128、\__m128)|
|[_mm_unpackhi_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_unpackhi_epi16)|SSE2|intrin.h|__m128i _mm_unpackhi_epi16 (\__m128i、\__m128i)|
|[_mm_unpackhi_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_unpackhi_epi32)|SSE2|intrin.h|__m128i _mm_unpackhi_epi32 (\__m128i、\__m128i)|
|[_mm_unpackhi_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_unpackhi_epi64)|SSE2|intrin.h|__m128i _mm_unpackhi_epi64 (\__m128i、\__m128i)|
|[_mm_unpackhi_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_unpackhi_epi8)|SSE2|intrin.h|__m128i _mm_unpackhi_epi8 (\__m128i、\__m128i)|
|[_mm_unpackhi_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_unpackhi_pd)|SSE2|intrin.h|__m128d _mm_unpackhi_pd (\__m128d、\__m128d)|
|[_mm_unpackhi_pi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_unpackhi_pi8)|MMX|mmintrin .h|__m64 _mm_unpackhi_pi8 (__m64、__m64) [3]|
|[_mm_unpackhi_pi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_unpackhi_pi16)|MMX|mmintrin .h|__m64 _mm_unpackhi_pi16 (__m64、__m64) [3]|
|[_mm_unpackhi_pi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_unpackhi_pi32)|MMX|mmintrin .h|__m64 _mm_unpackhi_pi32 (__m64、__m64) [3]|
|[_mm_unpackhi_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_unpackhi_ps)|SSE|intrin.h|__m128 _mm_unpackhi_ps (\__m128、\__m128)|
|[_mm_unpacklo_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_unpacklo_epi16)|SSE2|intrin.h|__m128i _mm_unpacklo_epi16 (\__m128i、\__m128i)|
|[_mm_unpacklo_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_unpacklo_epi32)|SSE2|intrin.h|__m128i _mm_unpacklo_epi32 (\__m128i、\__m128i)|
|[_mm_unpacklo_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_unpacklo_epi64)|SSE2|intrin.h|__m128i _mm_unpacklo_epi64 (\__m128i、\__m128i)|
|[_mm_unpacklo_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_unpacklo_epi8)|SSE2|intrin.h|__m128i _mm_unpacklo_epi8 (\__m128i、\__m128i)|
|[_mm_unpacklo_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_unpacklo_pd)|SSE2|intrin.h|__m128d _mm_unpacklo_pd (\__m128d、\__m128d)|
|[_mm_unpacklo_pi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_unpacklo_pi8)|MMX|mmintrin .h|__m64 _mm_unpacklo_pi8 (__m64、__m64) [3]|
|[_mm_unpacklo_pi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_unpacklo_pi16)|MMX|mmintrin .h|__m64 _mm_unpacklo_pi16 (__m64、__m64) [3]|
|[_mm_unpacklo_pi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_unpacklo_pi32)|MMX|mmintrin .h|__m64 _mm_unpacklo_pi32 (__m64、__m64) [3]|
|[_mm_unpacklo_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_unpacklo_ps)|SSE|intrin.h|__m128 _mm_unpacklo_ps (\__m128、\__m128)|
|[_mm_xor_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_xor_pd)|SSE2|intrin.h|__m128d _mm_xor_pd (\__m128d、\__m128d)|
|[_mm_xor_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_xor_ps)|SSE|intrin.h|__m128 _mm_xor_ps (\__m128、\__m128)|
|[_mm_xor_si64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_xor_si64)|MMX|mmintrin .h|__m64 _mm_xor_si64 (\__m64、\__m64) [3]|
|[_mm_xor_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm_xor_si128)|SSE2|intrin.h|__m128i _mm_xor_si128 (\__m128i、\__m128i)|
|[_mm256_abs_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_abs_epi16)|AVX2 [2]|immintrin.h|__m256i _mm256_abs_epi16 (\__m256i)|
|[_mm256_abs_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_abs_epi32)|AVX2 [2]|immintrin.h|__m256i _mm256_abs_epi32 (\__m256i)|
|[_mm256_abs_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_abs_epi8)|AVX2 [2]|immintrin.h|__m256i _mm256_abs_epi8 (\__m256i)|
|[_mm256_add_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_add_epi16)|AVX2 [2]|immintrin.h|__m256i _mm256_add_epi16 (\__m256i、\__m256i)|
|[_mm256_add_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_add_epi32)|AVX2 [2]|immintrin.h|__m256i _mm256_add_epi32 (\__m256i、\__m256i)|
|[_mm256_add_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_add_epi64)|AVX2 [2]|immintrin.h|__m256i _mm256_add_epi64 (\__m256i、\__m256i)|
|[_mm256_add_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_add_epi8)|AVX2 [2]|immintrin.h|__m256i _mm256_add_epi8 (\__m256i、\__m256i)|
|[_mm256_add_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_add_pd)|AVX [2]|immintrin.h|__m256d _mm256_add_pd (\__m256d、\__m256d)|
|[_mm256_add_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_add_ps)|AVX [2]|immintrin.h|__m256 _mm256_add_ps (\__m256、\__m256)|
|[_mm256_adds_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_adds_epi16)|AVX2 [2]|immintrin.h|__m256i _mm256_adds_epi16 (\__m256i、\__m256i)|
|[_mm256_adds_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_adds_epi8)|AVX2 [2]|immintrin.h|__m256i _mm256_adds_epi8 (\__m256i、\__m256i)|
|[_mm256_adds_epu16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_adds_epu16)|AVX2 [2]|immintrin.h|__m256i _mm256_adds_epu16 (\__m256i、\__m256i)|
|[_mm256_adds_epu8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_adds_epu8)|AVX2 [2]|immintrin.h|__m256i _mm256_adds_epu8 (\__m256i、\__m256i)|
|[_mm256_addsub_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_addsub_pd)|AVX [2]|immintrin.h|__m256d _mm256_addsub_pd (\__m256d、\__m256d)|
|[_mm256_addsub_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_addsub_ps)|AVX [2]|immintrin.h|__m256 _mm256_addsub_ps (\__m256、\__m256)|
|[_mm256_alignr_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_alignr_epi8)|AVX2 [2]|immintrin.h|__m256i _mm256_alignr_epi8 (\__m256i、\__m256i、const int)|
|[_mm256_and_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_and_pd)|AVX [2]|immintrin.h|__m256d _mm256_and_pd (\__m256d、\__m256d)|
|[_mm256_and_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_and_ps)|AVX [2]|immintrin.h|__m256 _mm256_and_ps (\__m256、\__m256)|
|[_mm256_and_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_and_si256)|AVX2 [2]|immintrin.h|__m256i _mm256_and_si256 (\__m256i、\__m256i)|
|[_mm256_andnot_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_andnot_pd)|AVX [2]|immintrin.h|__m256d _mm256_andnot_pd (\__m256d、\__m256d)|
|[_mm256_andnot_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_andnot_ps)|AVX [2]|immintrin.h|__m256 _mm256_andnot_ps (\__m256、\__m256)|
|[_mm256_andnot_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_andnot_si256)|AVX2 [2]|immintrin.h|__m256i _mm256_andnot_si256 (\__m256i、\__m256i)|
|[_mm256_avg_epu16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_avg_epu16)|AVX2 [2]|immintrin.h|__m256i _mm256_avg_epu16 (\__m256i、\__m256i)|
|[_mm256_avg_epu8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_avg_epu8)|AVX2 [2]|immintrin.h|__m256i _mm256_avg_epu8 (\__m256i、\__m256i)|
|[_mm256_blend_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_blend_epi16)|AVX2 [2]|immintrin.h|__m256i _mm256_blend_epi16 (\__m256i、\__m256i、const int)|
|[_mm256_blend_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_blend_epi32)|AVX2 [2]|immintrin.h|__m256i _mm256_blend_epi32 (\__m256i、\__m256i、const int)|
|[_mm256_blend_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_blend_pd)|AVX [2]|immintrin.h|__m256d _mm256_blend_pd (\__m256d、\__m256d、const int)|
|[_mm256_blend_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_blend_ps)|AVX [2]|immintrin.h|__m256 _mm256_blend_ps (\__m256、\__m256、const int)|
|[_mm256_blendv_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_blendv_epi8)|AVX2 [2]|immintrin.h|__m256i _mm256_blendv_epi8 (\__m256i、\__m256i、\__m256i)|
|[_mm256_blendv_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_blendv_pd)|AVX [2]|immintrin.h|__m256d _mm256_blendv_pd (\__m256d、\__m256d、\__m256d)|
|[_mm256_blendv_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_blendv_ps)|AVX [2]|immintrin.h|__m256 _mm256_blendv_ps (\__m256、\__m256、\__m256)|
|[_mm256_broadcast_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_broadcast_pd)|AVX [2]|immintrin.h|__m256d _mm256_broadcast_pd (\__m128d const \*)|
|[_mm256_broadcast_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_broadcast_ps)|AVX [2]|immintrin.h|__m256 _mm256_broadcast_ps (\__m128 const \*)|
|[_mm256_broadcast_sd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_broadcast_sd)|AVX [2]|immintrin.h|__m256d _mm256_broadcast_sd (二重 const \*)|
|[_mm256_broadcast_ss](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_broadcast_ss)|AVX [2]|immintrin.h|__m256 _mm256_broadcast_ss (float const \*)|
|[_mm256_broadcastb_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_broadcastb_epi8)|AVX2 [2]|immintrin.h|__m256i _mm256_broadcastb_epi8 (\__m128i)|
|[_mm256_broadcastd_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_broadcastd_epi32)|AVX2 [2]|immintrin.h|__m256i _mm256_broadcastd_epi32 (\__m128i)|
|[_mm256_broadcastq_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_broadcastq_epi64)|AVX2 [2]|immintrin.h|__m256i _mm256_broadcastq_epi64 (\__m128i)|
|[_mm256_broadcastsd_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_broadcastsd_pd)|AVX2 [2]|immintrin.h|__m256d _mm256_broadcastsd_pd (\__m128d)|
|[_mm256_broadcastsi128_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_broadcastsi128_si256)|AVX2 [2]|immintrin.h|__m256i _mm256_broadcastsi128_si256 (\__m128i)|
|[_mm256_broadcastss_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_broadcastss_ps)|AVX2 [2]|immintrin.h|__m256 _mm256_broadcastss_ps (\__m128)|
|[_mm256_broadcastw_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_broadcastw_epi16)|AVX2 [2]|immintrin.h|__m256i _mm256_broadcastw_epi16 (\__m128i)|
|[_mm256_castpd_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_castpd_ps)|AVX [2]|immintrin.h|__m256 _mm256_castpd_ps (\__m256d)|
|[_mm256_castpd_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_castpd_si256)|AVX [2]|immintrin.h|__m256i _mm256_castpd_si256 (\__m256d)|
|[_mm256_castpd128_pd256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_castpd128_pd256)|AVX [2]|immintrin.h|__m256d _mm256_castpd128_pd256 (\__m128d)|
|[_mm256_castpd256_pd128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_castpd256_pd128)|AVX [2]|immintrin.h|__m128d _mm256_castpd256_pd128 (\__m256d)|
|[_mm256_castps_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_castps_pd)|AVX [2]|immintrin.h|__m256d _mm256_castps_pd (\__m256)|
|[_mm256_castps_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_castps_si256)|AVX [2]|immintrin.h|__m256i _mm256_castps_si256 (\__m256)|
|[_mm256_castps128_ps256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_castps128_ps256)|AVX [2]|immintrin.h|__m256 _mm256_castps128_ps256 (\__m128)|
|[_mm256_castps256_ps128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_castps256_ps128)|AVX [2]|immintrin.h|__m128 _mm256_castps256_ps128 (\__m256)|
|[_mm256_castsi128_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_castsi128_si256)|AVX [2]|immintrin.h|__m256i _mm256_castsi128_si256 (\__m128i)|
|[_mm256_castsi256_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_castsi256_pd)|AVX [2]|immintrin.h|__m256d _mm256_castsi256_pd (\__m256i)|
|[_mm256_castsi256_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_castsi256_ps)|AVX [2]|immintrin.h|__m256 _mm256_castsi256_ps (\__m256i)|
|[_mm256_castsi256_si128](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_castsi256_si128)|AVX [2]|immintrin.h|__m128i _mm256_castsi256_si128 (\__m256i)|
|_mm256_cmov_si256|XOP [1]|ammintrin.h|__m256i _mm256_cmov_si256 (\__m256i、\__m256i、\__m256i)|
|[_mm256_cmp_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cmp_pd)|AVX [2]|immintrin.h|__m256d _mm256_cmp_pd (\__m256d、\__m256d、const int)|
|[_mm256_cmp_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cmp_ps)|AVX [2]|immintrin.h|__m256 _mm256_cmp_ps (\__m256、\__m256、const int)|
|[_mm256_cmpeq_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cmpeq_epi16)|AVX2 [2]|immintrin.h|__m256i _mm256_cmpeq_epi16 (\__m256i、\__m256i)|
|[_mm256_cmpeq_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cmpeq_epi32)|AVX2 [2]|immintrin.h|__m256i _mm256_cmpeq_epi32 (\__m256i、\__m256i)|
|[_mm256_cmpeq_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cmpeq_epi64)|AVX2 [2]|immintrin.h|__m256i _mm256_cmpeq_epi64 (\__m256i、\__m256i)|
|[_mm256_cmpeq_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cmpeq_epi8)|AVX2 [2]|immintrin.h|__m256i _mm256_cmpeq_epi8 (\__m256i、\__m256i)|
|[_mm256_cmpgt_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cmpgt_epi16)|AVX2 [2]|immintrin.h|__m256i _mm256_cmpgt_epi16 (\__m256i、\__m256i)|
|[_mm256_cmpgt_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cmpgt_epi32)|AVX2 [2]|immintrin.h|__m256i _mm256_cmpgt_epi32 (\__m256i、\__m256i)|
|[_mm256_cmpgt_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cmpgt_epi64)|AVX2 [2]|immintrin.h|__m256i _mm256_cmpgt_epi64 (\__m256i、\__m256i)|
|[_mm256_cmpgt_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cmpgt_epi8)|AVX2 [2]|immintrin.h|__m256i _mm256_cmpgt_epi8 (\__m256i、\__m256i)|
|[_mm256_cvtepi16_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cvtepi16_epi32)|AVX2 [2]|immintrin.h|__m256i _mm256_cvtepi16_epi32 (\__m128i)|
|[_mm256_cvtepi16_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cvtepi16_epi64)|AVX2 [2]|immintrin.h|__m256i _mm256_cvtepi16_epi64 (\__m128i)|
|[_mm256_cvtepi32_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cvtepi32_epi64)|AVX2 [2]|immintrin.h|__m256i _mm256_cvtepi32_epi64 (\__m128i)|
|[_mm256_cvtepi32_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cvtepi32_pd)|AVX [2]|immintrin.h|__m256d _mm256_cvtepi32_pd (\__m128i)|
|[_mm256_cvtepi32_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cvtepi32_ps)|AVX [2]|immintrin.h|__m256 _mm256_cvtepi32_ps (\__m256i)|
|[_mm256_cvtepi8_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cvtepi8_epi16)|AVX2 [2]|immintrin.h|__m256i _mm256_cvtepi8_epi16 (\__m128i)|
|[_mm256_cvtepi8_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cvtepi8_epi32)|AVX2 [2]|immintrin.h|__m256i _mm256_cvtepi8_epi32 (\__m128i)|
|[_mm256_cvtepi8_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cvtepi8_epi64)|AVX2 [2]|immintrin.h|__m256i _mm256_cvtepi8_epi64 (\__m128i)|
|[_mm256_cvtepu16_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cvtepu16_epi32)|AVX2 [2]|immintrin.h|__m256i _mm256_cvtepu16_epi32 (\__m128i)|
|[_mm256_cvtepu16_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cvtepu16_epi64)|AVX2 [2]|immintrin.h|__m256i _mm256_cvtepu16_epi64 (\__m128i)|
|[_mm256_cvtepu32_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cvtepu32_epi64)|AVX2 [2]|immintrin.h|__m256i _mm256_cvtepu32_epi64 (\__m128i)|
|[_mm256_cvtepu8_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cvtepu8_epi16)|AVX2 [2]|immintrin.h|__m256i _mm256_cvtepu8_epi16 (\__m128i)|
|[_mm256_cvtepu8_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cvtepu8_epi32)|AVX2 [2]|immintrin.h|__m256i _mm256_cvtepu8_epi32 (\__m128i)|
|[_mm256_cvtepu8_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cvtepu8_epi64)|AVX2 [2]|immintrin.h|__m256i _mm256_cvtepu8_epi64 (\__m128i)|
|[_mm256_cvtpd_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cvtpd_epi32)|AVX [2]|immintrin.h|__m128i _mm256_cvtpd_epi32 (\__m256d)|
|[_mm256_cvtpd_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cvtpd_ps)|AVX [2]|immintrin.h|__m128 _mm256_cvtpd_ps (\__m256d)|
|[_mm256_cvtph_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cvtph_ps)|F16C [2]|immintrin.h|__m256 _mm256_cvtph_ps (\__m128i)|
|[_mm256_cvtps_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cvtps_epi32)|AVX [2]|immintrin.h|__m256i _mm256_cvtps_epi32 (\__m256)|
|[_mm256_cvtps_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cvtps_pd)|AVX [2]|immintrin.h|__m256d _mm256_cvtps_pd (\__m128)|
|[_mm256_cvtps_ph](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cvtps_ph)|F16C [2]|immintrin.h|__m128i _mm256_cvtps_ph (\__m256、const int)|
|[_mm256_cvttpd_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cvttpd_epi32)|AVX [2]|immintrin.h|__m128i _mm256_cvttpd_epi32 (\__m256d)|
|[_mm256_cvttps_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_cvttps_epi32)|AVX [2]|immintrin.h|__m256i _mm256_cvttps_epi32 (\__m256)|
|[_mm256_div_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_div_pd)|AVX [2]|immintrin.h|__m256d _mm256_div_pd (\__m256d、\__m256d)|
|[_mm256_div_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_div_ps)|AVX [2]|immintrin.h|__m256 _mm256_div_ps (\__m256、\__m256)|
|[_mm256_dp_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_dp_ps)|AVX [2]|immintrin.h|__m256 _mm256_dp_ps (\__m256、\__m256、const int)|
|[_mm256_extractf128_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_extractf128_pd)|AVX [2]|immintrin.h|__m128d _mm256_extractf128_pd (\__m256d、const int)|
|[_mm256_extractf128_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_extractf128_ps)|AVX [2]|immintrin.h|__m128 _mm256_extractf128_ps (\__m256、const int)|
|[_mm256_extractf128_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_extractf128_si256)|AVX [2]|immintrin.h|__m128i _mm256_extractf128_si256 (\__m256i、const int)|
|[_mm256_extracti128_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_extracti128_si256)|AVX2 [2]|immintrin.h|__m128i _mm256_extracti128_si256 (\__m256i、int)|
|[_mm256_fmadd_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_fmadd_pd)|FMA [2]|immintrin.h|__m256d _mm256_fmadd_pd (\__m256d、\__m256d、\__m256d)|
|[_mm256_fmadd_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_fmadd_ps)|FMA [2]|immintrin.h|__m256 _mm256_fmadd_ps (\__m256、\__m256、\__m256)|
|[_mm256_fmaddsub_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_fmaddsub_pd)|FMA [2]|immintrin.h|__m256d _mm256_fmaddsub_pd (\__m256d、\__m256d、\__m256d)|
|[_mm256_fmaddsub_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_fmaddsub_ps)|FMA [2]|immintrin.h|__m256 _mm256_fmaddsub_ps (\__m256、\__m256、\__m256)|
|[_mm256_fmsub_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_fmsub_pd)|FMA [2]|immintrin.h|__m256d _mm256_fmsub_pd (\__m256d、\__m256d、\__m256d)|
|[_mm256_fmsub_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_fmsub_ps)|FMA [2]|immintrin.h|__m256 _mm256_fmsub_ps (\__m256、\__m256、\__m256)|
|[_mm256_fmsubadd_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_fmsubadd_pd)|FMA [2]|immintrin.h|__m256d _mm256_fmsubadd_pd (\__m256d、\__m256d、\__m256d)|
|[_mm256_fmsubadd_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_fmsubadd_ps)|FMA [2]|immintrin.h|__m256 _mm256_fmsubadd_ps (\__m256、\__m256、\__m256)|
|[_mm256_fnmadd_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_fnmadd_pd)|FMA [2]|immintrin.h|__m256d _mm256_fnmadd_pd (\__m256d、\__m256d、\__m256d)|
|[_mm256_fnmadd_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_fnmadd_ps)|FMA [2]|immintrin.h|__m256 _mm256_fnmadd_ps (\__m256、\__m256、\__m256)|
|[_mm256_fnmsub_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_fnmsub_pd)|FMA [2]|immintrin.h|__m256d _mm256_fnmsub_pd (\__m256d、\__m256d、\__m256d)|
|[_mm256_fnmsub_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_fnmsub_ps)|FMA [2]|immintrin.h|__m256 _mm256_fnmsub_ps (\__m256、\__m256、\__m256)|
|_mm256_frcz_pd|XOP [1]|ammintrin.h|__m256d _mm256_frcz_pd (\__m256d)|
|_mm256_frcz_ps|XOP [1]|ammintrin.h|__m256 _mm256_frcz_ps (\__m256)|
|[_mm256_hadd_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_hadd_epi16)|AVX2 [2]|immintrin.h|__m256i _mm256_hadd_epi16 (\__m256i、\__m256i)|
|[_mm256_hadd_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_hadd_epi32)|AVX2 [2]|immintrin.h|__m256i _mm256_hadd_epi32 (\__m256i、\__m256i)|
|[_mm256_hadd_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_hadd_pd)|AVX [2]|immintrin.h|__m256d _mm256_hadd_pd (\__m256d、\__m256d)|
|[_mm256_hadd_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_hadd_ps)|AVX [2]|immintrin.h|__m256 _mm256_hadd_ps (\__m256、\__m256)|
|[_mm256_hadds_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_hadds_epi16)|AVX2 [2]|immintrin.h|__m256i _mm256_hadds_epi16 (\__m256i、\__m256i)|
|[_mm256_hsub_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_hsub_epi16)|AVX2 [2]|immintrin.h|__m256i _mm256_hsub_epi16 (\__m256i、\__m256i)|
|[_mm256_hsub_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_hsub_epi32)|AVX2 [2]|immintrin.h|__m256i _mm256_hsub_epi32 (\__m256i、\__m256i)|
|[_mm256_hsub_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_hsub_pd)|AVX [2]|immintrin.h|__m256d _mm256_hsub_pd (\__m256d、\__m256d)|
|[_mm256_hsub_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_hsub_ps)|AVX [2]|immintrin.h|__m256 _mm256_hsub_ps (\__m256、\__m256)|
|[_mm256_hsubs_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_hsubs_epi16)|AVX2 [2]|immintrin.h|__m256i _mm256_hsubs_epi16 (\__m256i、\__m256i)|
|[_mm256_i32gather_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_i32gather_epi32)|AVX2 [2]|immintrin.h|__m256i _mm256_i32gather_epi32 (int const \*、\__m256i、const int)|
|[_mm256_i32gather_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_i32gather_epi64)|AVX2 [2]|immintrin.h|__m256i _mm256_i32gather_epi64 (\__int64 const \*、\__m128i、const int)|
|[_mm256_i32gather_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_i32gather_pd)|AVX2 [2]|immintrin.h|__m256d _mm256_i32gather_pd (二重 const \*、\__m128i、const int)|
|[_mm256_i32gather_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_i32gather_ps)|AVX2 [2]|immintrin.h|__m256 _mm256_i32gather_ps (float const \*、\__m256i、const int)|
|[_mm256_i64gather_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_i64gather_epi32)|AVX2 [2]|immintrin.h|__m256i _mm256_i64gather_epi32 (int const \*、\__m256i、const int)|
|[_mm256_i64gather_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_i64gather_epi64)|AVX2 [2]|immintrin.h|__m256i _mm256_i64gather_epi64 (\__int64 const \*、\__m256i、const int)|
|[_mm256_i64gather_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_i64gather_pd)|AVX2 [2]|immintrin.h|__m256d _mm256_i64gather_pd (二重 const \*、\__m256i、const int)|
|[_mm256_i64gather_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_i64gather_ps)|AVX2 [2]|immintrin.h|__m128 _mm256_i64gather_ps (float const \*、\__m256i、const int)|
|[_mm256_insertf128_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_insertf128_pd)|AVX [2]|immintrin.h|__m256d _mm256_insertf128_pd (\__m256d、\__m128d、int)|
|[_mm256_insertf128_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_insertf128_ps)|AVX [2]|immintrin.h|__m256 _mm256_insertf128_ps (\__m256、\__m128、int)|
|[_mm256_insertf128_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_insertf128_si256)|AVX [2]|immintrin.h|__m256i _mm256_insertf128_si256 (\__m256i、\__m128i、int)|
|[_mm256_inserti128_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_inserti128_si256)|AVX2 [2]|immintrin.h|__m256i _mm256_inserti128_si256 (\__m256i、\__m128i、int)|
|[_mm256_lddqu_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_lddqu_si256)|AVX [2]|immintrin.h|__m256i _mm256_lddqu_si256 (\__m256i \*)|
|[_mm256_load_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_load_pd)|AVX [2]|immintrin.h|__m256d _mm256_load_pd (二重 const \*)|
|[_mm256_load_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_load_ps)|AVX [2]|immintrin.h|__m256 _mm256_load_ps (float const \*)|
|[_mm256_load_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_load_si256)|AVX [2]|immintrin.h|__m256i _mm256_load_si256 (\__m256i \*)|
|[_mm256_loadu_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_loadu_pd)|AVX [2]|immintrin.h|__m256d _mm256_loadu_pd (二重 const \*)|
|[_mm256_loadu_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_loadu_ps)|AVX [2]|immintrin.h|__m256 _mm256_loadu_ps (float const \*)|
|[_mm256_loadu_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_loadu_si256)|AVX [2]|immintrin.h|__m256i _mm256_loadu_si256 (\__m256i \*)|
|_mm256_macc_pd|FMA4 [1]|ammintrin.h|__m256d _mm_macc_pd (\__m256d、\__m256d、\__m256d)|
|_mm256_macc_ps|FMA4 [1]|ammintrin.h|__m256 _mm_macc_ps (\__m256、\__m256、\__m256)|
|[_mm256_madd_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_madd_epi16)|AVX2 [2]|immintrin.h|__m256i _mm256_madd_epi16 (\__m256i、\__m256i)|
|_mm256_maddsub_pd|FMA4 [1]|ammintrin.h|__m256d _mm_maddsub_pd (\__m256d、\__m256d、\__m256d)|
|_mm256_maddsub_ps|FMA4 [1]|ammintrin.h|__m256 _mm_maddsub_ps (\__m256、\__m256、\__m256)|
|[_mm256_maddubs_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_maddubs_epi16)|AVX2 [2]|immintrin.h|__m256i _mm256_maddubs_epi16 (\__m256i、\__m256i)|
|[_mm256_mask_i32gather_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_mask_i32gather_epi32)|AVX2 [2]|immintrin.h|__m256i _mm256_mask_i32gather_epi32 (\__m256i、int const \*、\__m256i、\__m256i、const int)|
|[_mm256_mask_i32gather_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_mask_i32gather_epi64)|AVX2 [2]|immintrin.h|__m256i _mm256_mask_i32gather_epi64 (\__m256i、\__int64 const \*、\__m128i、\__m256i、const int)|
|[_mm256_mask_i32gather_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_mask_i32gather_pd)|AVX2 [2]|immintrin.h|__m256d _mm256_mask_i32gather_pd (\__m256d、二重 const \*、\__m128i、\__m256d、const int)|
|[_mm256_mask_i32gather_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_mask_i32gather_ps)|AVX2 [2]|immintrin.h|__m256 _mm256_mask_i32gather_ps (\__m256、float const \*、\__m256i、\__m256、const int)|
|[_mm256_mask_i64gather_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_mask_i64gather_epi32)|AVX2 [2]|immintrin.h|__m128i _mm256_mask_i64gather_epi32 (\__m128i、int const \*、\__m256i、\__m128i、const int)|
|[_mm256_mask_i64gather_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_mask_i64gather_epi64)|AVX2 [2]|immintrin.h|__m256i _mm256_mask_i64gather_epi64 (\__m256i、\__int64 const \*、\__m256i、\__m256i、const int)|
|[_mm256_mask_i64gather_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_mask_i64gather_pd)|AVX2 [2]|immintrin.h|__m256d _mm256_mask_i64gather_pd (\__m256d、二重 const \*、\__m256i、\__m256d、const int)|
|[_mm256_mask_i64gather_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_mask_i64gather_ps)|AVX2 [2]|immintrin.h|__m128 _mm256_mask_i64gather_ps (\__m128、float const \*、\__m256i、\__m128、const int)|
|[_mm256_maskload_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_maskload_epi32)|AVX2 [2]|immintrin.h|__m256i _mm256_maskload_epi32 (int const \*、\__m256i)|
|[_mm256_maskload_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_maskload_epi64)|AVX2 [2]|immintrin.h|__m256i _mm256_maskload_epi64 (\__int64 const \*、\__m256i)|
|[_mm256_maskload_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_maskload_pd)|AVX [2]|immintrin.h|__m256d _mm256_maskload_pd (二重 const \*、\__m256i)|
|[_mm256_maskload_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_maskload_ps)|AVX [2]|immintrin.h|__m256 _mm256_maskload_ps (float const \*、\__m256i)|
|[_mm256_maskstore_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_maskstore_epi32)|AVX2 [2]|immintrin.h|void _mm256_maskstore_epi32 (int \*、\__m256i、\__m256i)|
|[_mm256_maskstore_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_maskstore_epi64)|AVX2 [2]|immintrin.h|void _mm256_maskstore_epi64 (\__int64 \*、\__m256i、\__m256i)|
|[_mm256_maskstore_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_maskstore_pd)|AVX [2]|immintrin.h|void _mm256_maskstore_pd (double \*、\__m256i、\__m256d)|
|[_mm256_maskstore_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_maskstore_ps)|AVX [2]|immintrin.h|void _mm256_maskstore_ps (float \*、\__m256i、\__m256)|
|[_mm256_max_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_max_epi16)|AVX2 [2]|immintrin.h|__m256i _mm256_max_epi16 (\__m256i、\__m256i)|
|[_mm256_max_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_max_epi32)|AVX2 [2]|immintrin.h|__m256i _mm256_max_epi32 (\__m256i、\__m256i)|
|[_mm256_max_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_max_epi8)|AVX2 [2]|immintrin.h|__m256i _mm256_max_epi8 (\__m256i、\__m256i)|
|[_mm256_max_epu16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_max_epu16)|AVX2 [2]|immintrin.h|__m256i _mm256_max_epu16 (\__m256i、\__m256i)|
|[_mm256_max_epu32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_max_epu32)|AVX2 [2]|immintrin.h|__m256i _mm256_max_epu32 (\__m256i、\__m256i)|
|[_mm256_max_epu8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_max_epu8)|AVX2 [2]|immintrin.h|__m256i _mm256_max_epu8 (\__m256i、\__m256i)|
|[_mm256_max_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_max_pd)|AVX [2]|immintrin.h|__m256d _mm256_max_pd (\__m256d、\__m256d)|
|[_mm256_max_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_max_ps)|AVX [2]|immintrin.h|__m256 _mm256_max_ps (\__m256、\__m256)|
|[_mm256_min_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_min_epi16)|AVX2 [2]|immintrin.h|__m256i _mm256_min_epi16 (\__m256i、\__m256i)|
|[_mm256_min_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_min_epi32)|AVX2 [2]|immintrin.h|__m256i _mm256_min_epi32 (\__m256i、\__m256i)|
|[_mm256_min_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_min_epi8)|AVX2 [2]|immintrin.h|__m256i _mm256_min_epi8 (\__m256i、\__m256i)|
|[_mm256_min_epu16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_min_epu16)|AVX2 [2]|immintrin.h|__m256i _mm256_min_epu16 (\__m256i、\__m256i)|
|[_mm256_min_epu32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_min_epu32)|AVX2 [2]|immintrin.h|__m256i _mm256_min_epu32 (\__m256i、\__m256i)|
|[_mm256_min_epu8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_min_epu8)|AVX2 [2]|immintrin.h|__m256i _mm256_min_epu8 (\__m256i、\__m256i)|
|[_mm256_min_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_min_pd)|AVX [2]|immintrin.h|__m256d _mm256_min_pd (\__m256d、\__m256d)|
|[_mm256_min_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_min_ps)|AVX [2]|immintrin.h|__m256 _mm256_min_ps (\__m256、\__m256)|
|[_mm256_movedup_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_movedup_pd)|AVX [2]|immintrin.h|__m256d _mm256_movedup_pd (\__m256d)|
|[_mm256_movehdup_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_movehdup_ps)|AVX [2]|immintrin.h|__m256 _mm256_movehdup_ps (\__m256)|
|[_mm256_moveldup_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_moveldup_ps)|AVX [2]|immintrin.h|__m256 _mm256_moveldup_ps (\__m256)|
|[_mm256_movemask_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_movemask_epi8)|AVX2 [2]|immintrin.h|int _mm256_movemask_epi8 (\__m256i)|
|[_mm256_movemask_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_movemask_pd)|AVX [2]|immintrin.h|int _mm256_movemask_pd (\__m256d)|
|[_mm256_movemask_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_movemask_ps)|AVX [2]|immintrin.h|int _mm256_movemask_ps (\__m256)|
|[_mm256_mpsadbw_epu8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_mpsadbw_epu8)|AVX2 [2]|immintrin.h|__m256i _mm256_mpsadbw_epu8 (\__m256i、\__m256i、const int)|
|_mm256_msub_pd|FMA4 [1]|ammintrin.h|__m256d _mm_msub_pd (\__m256d、\__m256d、\__m256d)|
|_mm256_msub_ps|FMA4 [1]|ammintrin.h|__m256 _mm_msub_ps (\__m256、\__m256、\__m256)|
|_mm256_msubadd_pd|FMA4 [1]|ammintrin.h|__m256d _mm_msubadd_pd (\__m256d、\__m256d、\__m256d)|
|_mm256_msubadd_ps|FMA4 [1]|ammintrin.h|__m256 _mm_msubadd_ps (\__m256、\__m256、\__m256)|
|[_mm256_mul_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_mul_epi32)|AVX2 [2]|immintrin.h|__m256i _mm256_mul_epi32 (\__m256i、\__m256i)|
|[_mm256_mul_epu32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_mul_epu32)|AVX2 [2]|immintrin.h|__m256i _mm256_mul_epu32 (\__m256i、\__m256i)|
|[_mm256_mul_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_mul_pd)|AVX [2]|immintrin.h|__m256d _mm256_mul_pd (\__m256d、\__m256d)|
|[_mm256_mul_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_mul_ps)|AVX [2]|immintrin.h|__m256 _mm256_mul_ps (\__m256、\__m256)|
|[_mm256_mulhi_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_mulhi_epi16)|AVX2 [2]|immintrin.h|__m256i _mm256_mulhi_epi16 (\__m256i、\__m256i)|
|[_mm256_mulhi_epu16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_mulhi_epu16)|AVX2 [2]|immintrin.h|__m256i _mm256_mulhi_epu16 (\__m256i、\__m256i)|
|[_mm256_mulhrs_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_mulhrs_epi16)|AVX2 [2]|immintrin.h|__m256i _mm256_mulhrs_epi16 (\__m256i、\__m256i)|
|[_mm256_mullo_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_mullo_epi16)|AVX2 [2]|immintrin.h|__m256i _mm256_mullo_epi16 (\__m256i、\__m256i)|
|[_mm256_mullo_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_mullo_epi32)|AVX2 [2]|immintrin.h|__m256i _mm256_mullo_epi32 (\__m256i、\__m256i)|
|_mm256_nmacc_pd|FMA4 [1]|ammintrin.h|__m256d _mm_nmacc_pd (\__m256d、\__m256d、\__m256d)|
|_mm256_nmacc_ps|FMA4 [1]|ammintrin.h|__m256 _mm_nmacc_ps (\__m256、\__m256、\__m256)|
|_mm256_nmsub_pd|FMA4 [1]|ammintrin.h|__m256d _mm_nmsub_pd (\__m256d、\__m256d、\__m256d)|
|_mm256_nmsub_ps|FMA4 [1]|ammintrin.h|__m256 _mm_nmsub_ps (\__m256、\__m256、\__m256)|
|[_mm256_or_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_or_pd)|AVX [2]|immintrin.h|__m256d _mm256_or_pd (\__m256d、\__m256d)|
|[_mm256_or_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_or_ps)|AVX [2]|immintrin.h|__m256 _mm256_or_ps (\__m256、\__m256)|
|[_mm256_or_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_or_si256)|AVX2 [2]|immintrin.h|__m256i _mm256_or_si256 (\__m256i、\__m256i)|
|[_mm256_packs_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_packs_epi16)|AVX2 [2]|immintrin.h|__m256i _mm256_packs_epi16 (\__m256i、\__m256i)|
|[_mm256_packs_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_packs_epi32)|AVX2 [2]|immintrin.h|__m256i _mm256_packs_epi32 (\__m256i、\__m256i)|
|[_mm256_packus_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_packus_epi16)|AVX2 [2]|immintrin.h|__m256i _mm256_packus_epi16 (\__m256i、\__m256i)|
|[_mm256_packus_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_packus_epi32)|AVX2 [2]|immintrin.h|__m256i _mm256_packus_epi32 (\__m256i、\__m256i)|
|[_mm256_permute_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_permute_pd)|AVX [2]|immintrin.h|__m256d _mm256_permute_pd (\__m256d、int)|
|[_mm256_permute_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_permute_ps)|AVX [2]|immintrin.h|__m256 _mm256_permute_ps (\__m256、int)|
|_mm256_permute2_pd|XOP [1]|ammintrin.h|__m256d _mm256_permute2_pd (\__m256d、\__m256d、\__m256i、int)|
|_mm256_permute2_ps|XOP [1]|ammintrin.h|__m256 _mm256_permute2_ps (\__m256、\__m256、\__m256i、int)|
|[_mm256_permute2f128_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_permute2f128_pd)|AVX [2]|immintrin.h|__m256d _mm256_permute2f128_pd (\__m256d、\__m256d、int)|
|[_mm256_permute2f128_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_permute2f128_ps)|AVX [2]|immintrin.h|__m256 _mm256_permute2f128_ps (\__m256、\__m256、int)|
|[_mm256_permute2f128_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_permute2f128_si256)|AVX [2]|immintrin.h|__m256i _mm256_permute2f128_si256 (\__m256i、\__m256i、int)|
|[_mm256_permute2x128_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_permute2x128_si256)|AVX2 [2]|immintrin.h|__m256i _mm256_permute2x128_si256 (\__m256i、\__m256i、const int)|
|[_mm256_permute4x64_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_permute4x64_epi64)|AVX2 [2]|immintrin.h|__m256i _mm256_permute4x64_epi64 (\__m256i、const int)|
|[_mm256_permute4x64_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_permute4x64_pd)|AVX2 [2]|immintrin.h|__m256d _mm256_permute4x64_pd (\__m256d、const int)|
|[_mm256_permutevar_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_permutevar_pd)|AVX [2]|immintrin.h|__m256d _mm256_permutevar_pd (\__m256d、\__m256i)|
|[_mm256_permutevar_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_permutevar_ps)|AVX [2]|immintrin.h|__m256 _mm256_permutevar_ps (\__m256、\__m256i)|
|[_mm256_permutevar8x32_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_permutevar8x32_epi32)|AVX2 [2]|immintrin.h|__m256i _mm256_permutevar8x32_epi32 (\__m256i、\__m256i)|
|[_mm256_permutevar8x32_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_permutevar8x32_ps)|AVX2 [2]|immintrin.h|__m256 _mm256_permutevar8x32_ps (\__m256、\__m256i)|
|[_mm256_rcp_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_rcp_ps)|AVX [2]|immintrin.h|__m256 _mm256_rcp_ps (\__m256)|
|[_mm256_round_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_round_pd)|AVX [2]|immintrin.h|__m256d _mm256_round_pd (\__m256d、int)|
|[_mm256_round_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_round_ps)|AVX [2]|immintrin.h|__m256 _mm256_round_ps (\__m256、int)|
|[_mm256_rsqrt_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_rsqrt_ps)|AVX [2]|immintrin.h|__m256 _mm256_rsqrt_ps (\__m256)|
|[_mm256_sad_epu8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_sad_epu8)|AVX2 [2]|immintrin.h|__m256i _mm256_sad_epu8 (\__m256i、\__m256i)|
|[_mm256_set_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_set_epi16)|AVX [2]|immintrin.h|(__m256i _mm256_set_epi16(short|
|[_mm256_set_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_set_epi32)|AVX [2]|immintrin.h|__m256i _mm256_set_epi32 (int、int、int、int、int、int、int、int)|
|[_mm256_set_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_set_epi8)|AVX [2]|immintrin.h|__m256i _mm256_set_epi8 (char, char, char, char, char, char, char, char, char, char, char, char, char, char, char, char, char, char, char, char, char, char, char, char, char, char, char, char, char, char, char, char, char, char, char, char, char)|
|[_mm256_set_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_set_pd)|AVX [2]|immintrin.h|__m256d _mm256_set_pd (double、double、double、double)|
|[_mm256_set_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_set_ps)|AVX [2]|immintrin.h|__m256 _mm256_set_ps (float、float、float、float、float、float、float、float)|
|[_mm256_set1_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_set1_epi16)|AVX [2]|immintrin.h|__m256i _mm256_set1_epi16(short)|
|[_mm256_set1_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_set1_epi32)|AVX [2]|immintrin.h|__m256i _mm256_set1_epi32(int)|
|[_mm256_set1_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_set1_epi8)|AVX [2]|immintrin.h|__m256i _mm256_set1_epi8(char)|
|[_mm256_set1_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_set1_pd)|AVX [2]|immintrin.h|__m256d _mm256_set1_pd(double)|
|[_mm256_set1_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_set1_ps)|AVX [2]|immintrin.h|__m256 _mm256_set1_ps(float)|
|[_mm256_setr_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_setr_epi16)|AVX [2]|immintrin.h|(__m256i _mm256_setr_epi16(short|
|[_mm256_setr_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_setr_epi32)|AVX [2]|immintrin.h|__m256i _mm256_setr_epi32 (int、int、int、int、int、int、int、int)|
|[_mm256_setr_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_setr_epi8)|AVX [2]|immintrin.h|(__m256i _mm256_setr_epi8(char|
|[_mm256_setr_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_setr_pd)|AVX [2]|immintrin.h|__m256d _mm256_setr_pd (double、double、double、double)|
|[_mm256_setr_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_setr_ps)|AVX [2]|immintrin.h|__m256 _mm256_setr_ps (float、float、float、float、float、float、float、float)|
|[_mm256_setzero_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_setzero_pd)|AVX [2]|immintrin.h|__m256d _mm256_setzero_pd(void)|
|[_mm256_setzero_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_setzero_ps)|AVX [2]|immintrin.h|__m256 _mm256_setzero_ps(void)|
|[_mm256_setzero_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_setzero_si256)|AVX [2]|immintrin.h|__m256i _mm256_setzero_si256(void)|
|[_mm256_shuffle_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_shuffle_epi32)|AVX2 [2]|immintrin.h|__m256i _mm256_shuffle_epi32 (\__m256i、const int)|
|[_mm256_shuffle_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_shuffle_epi8)|AVX2 [2]|immintrin.h|__m256i _mm256_shuffle_epi8 (\__m256i、\__m256i)|
|[_mm256_shuffle_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_shuffle_pd)|AVX [2]|immintrin.h|__m256d _mm256_shuffle_pd (\__m256d、\__m256d、const int)|
|[_mm256_shuffle_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_shuffle_ps)|AVX [2]|immintrin.h|__m256 _mm256_shuffle_ps (\__m256、\__m256、const int)|
|[_mm256_shufflehi_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_shufflehi_epi16)|AVX2 [2]|immintrin.h|__m256i _mm256_shufflehi_epi16 (\__m256i、const int)|
|[_mm256_shufflelo_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_shufflelo_epi16)|AVX2 [2]|immintrin.h|__m256i _mm256_shufflelo_epi16 (\__m256i、const int)|
|[_mm256_sign_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_sign_epi16)|AVX2 [2]|immintrin.h|__m256i _mm256_sign_epi16 (\__m256i、\__m256i)|
|[_mm256_sign_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_sign_epi32)|AVX2 [2]|immintrin.h|__m256i _mm256_sign_epi32 (\__m256i、\__m256i)|
|[_mm256_sign_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_sign_epi8)|AVX2 [2]|immintrin.h|__m256i _mm256_sign_epi8 (\__m256i、\__m256i)|
|[_mm256_sll_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_sll_epi16)|AVX2 [2]|immintrin.h|__m256i _mm256_sll_epi16 (\__m256i、\__m128i)|
|[_mm256_sll_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_sll_epi32)|AVX2 [2]|immintrin.h|__m256i _mm256_sll_epi32 (\__m256i、\__m128i)|
|[_mm256_sll_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_sll_epi64)|AVX2 [2]|immintrin.h|__m256i _mm256_sll_epi64 (\__m256i、\__m128i)|
|[_mm256_slli_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_slli_epi16)|AVX2 [2]|immintrin.h|__m256i _mm256_slli_epi16 (\__m256i、int)|
|[_mm256_slli_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_slli_epi32)|AVX2 [2]|immintrin.h|__m256i _mm256_slli_epi32 (\__m256i、int)|
|[_mm256_slli_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_slli_epi64)|AVX2 [2]|immintrin.h|__m256i _mm256_slli_epi64 (\__m256i、int)|
|[_mm256_slli_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_slli_si256)|AVX2 [2]|immintrin.h|__m256i _mm256_slli_si256 (\__m256i、int)|
|[_mm256_sllv_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_sllv_epi32)|AVX2 [2]|immintrin.h|__m256i _mm256_sllv_epi32 (\__m256i、\__m256i)|
|[_mm256_sllv_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_sllv_epi64)|AVX2 [2]|immintrin.h|__m256i _mm256_sllv_epi64 (\__m256i、\__m256i)|
|[_mm256_sqrt_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_sqrt_pd)|AVX [2]|immintrin.h|__m256d _mm256_sqrt_pd (\__m256d)|
|[_mm256_sqrt_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_sqrt_ps)|AVX [2]|immintrin.h|__m256 _mm256_sqrt_ps (\__m256)|
|[_mm256_sra_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_sra_epi16)|AVX2 [2]|immintrin.h|__m256i _mm256_sra_epi16 (\__m256i、\__m128i)|
|[_mm256_sra_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_sra_epi32)|AVX2 [2]|immintrin.h|__m256i _mm256_sra_epi32 (\__m256i、\__m128i)|
|[_mm256_srai_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_srai_epi16)|AVX2 [2]|immintrin.h|__m256i _mm256_srai_epi16 (\__m256i、int)|
|[_mm256_srai_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_srai_epi32)|AVX2 [2]|immintrin.h|__m256i _mm256_srai_epi32 (\__m256i、int)|
|[_mm256_srav_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_srav_epi32)|AVX2 [2]|immintrin.h|__m256i _mm256_srav_epi32 (\__m256i、\__m256i)|
|[_mm256_srl_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_srl_epi16)|AVX2 [2]|immintrin.h|__m256i _mm256_srl_epi16 (\__m256i、\__m128i)|
|[_mm256_srl_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_srl_epi32)|AVX2 [2]|immintrin.h|__m256i _mm256_srl_epi32 (\__m256i、\__m128i)|
|[_mm256_srl_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_srl_epi64)|AVX2 [2]|immintrin.h|__m256i _mm256_srl_epi64 (\__m256i、\__m128i)|
|[_mm256_srli_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_srli_epi16)|AVX2 [2]|immintrin.h|__m256i _mm256_srli_epi16 (\__m256i、int)|
|[_mm256_srli_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_srli_epi32)|AVX2 [2]|immintrin.h|__m256i _mm256_srli_epi32 (\__m256i、int)|
|[_mm256_srli_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_srli_epi64)|AVX2 [2]|immintrin.h|__m256i _mm256_srli_epi64 (\__m256i、int)|
|[_mm256_srli_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_srli_si256)|AVX2 [2]|immintrin.h|__m256i _mm256_srli_si256 (\__m256i、int)|
|[_mm256_srlv_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_srlv_epi32)|AVX2 [2]|immintrin.h|__m256i _mm256_srlv_epi32 (\__m256i、\__m256i)|
|[_mm256_srlv_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_srlv_epi64)|AVX2 [2]|immintrin.h|__m256i _mm256_srlv_epi64 (\__m256i、\__m256i)|
|[_mm256_store_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_store_pd)|AVX [2]|immintrin.h|void _mm256_store_pd (double \*、\__m256d)|
|[_mm256_store_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_store_ps)|AVX [2]|immintrin.h|void _mm256_store_ps (float \*、\__m256)|
|[_mm256_store_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_store_si256)|AVX [2]|immintrin.h|void _mm256_store_si256 (\__m256i \*、\__m256i)|
|[_mm256_storeu_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_storeu_pd)|AVX [2]|immintrin.h|void _mm256_storeu_pd (double \*、\__m256d)|
|[_mm256_storeu_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_storeu_ps)|AVX [2]|immintrin.h|void _mm256_storeu_ps (float \*、\__m256)|
|[_mm256_storeu_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_storeu_si256)|AVX [2]|immintrin.h|void _mm256_storeu_si256 (\__m256i \*、\__m256i)|
|[_mm256_stream_load_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_stream_load_si256)|AVX2 [2]|immintrin.h|__m256i _mm256_stream_load_si256 (\__m256i const \*)|
|[_mm256_stream_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_stream_pd)|AVX [2]|immintrin.h|void __mm256_stream_pd (double \*、\__m256d)|
|[_mm256_stream_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_stream_ps)|AVX [2]|immintrin.h|void _mm256_stream_ps (float \*、\__m256)|
|[_mm256_stream_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_stream_si256)|AVX [2]|immintrin.h|void __mm256_stream_si256 (\__m256i \*、\__m256i)|
|[_mm256_sub_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_sub_epi16)|AVX2 [2]|immintrin.h|__m256i _mm256_sub_epi16 (\__m256i、\__m256i)|
|[_mm256_sub_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_sub_epi32)|AVX2 [2]|immintrin.h|__m256i _mm256_sub_epi32 (\__m256i、\__m256i)|
|[_mm256_sub_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_sub_epi64)|AVX2 [2]|immintrin.h|__m256i _mm256_sub_epi64 (\__m256i、\__m256i)|
|[_mm256_sub_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_sub_epi8)|AVX2 [2]|immintrin.h|__m256i _mm256_sub_epi8 (\__m256i、\__m256i)|
|[_mm256_sub_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_sub_pd)|AVX [2]|immintrin.h|__m256d _mm256_sub_pd (\__m256d、\__m256d)|
|[_mm256_sub_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_sub_ps)|AVX [2]|immintrin.h|__m256 _mm256_sub_ps (\__m256、\__m256)|
|[_mm256_subs_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_subs_epi16)|AVX2 [2]|immintrin.h|__m256i _mm256_subs_epi16 (\__m256i、\__m256i)|
|[_mm256_subs_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_subs_epi8)|AVX2 [2]|immintrin.h|__m256i _mm256_subs_epi8 (\__m256i、\__m256i)|
|[_mm256_subs_epu16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_subs_epu16)|AVX2 [2]|immintrin.h|__m256i _mm256_subs_epu16 (\__m256i、\__m256i)|
|[_mm256_subs_epu8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_subs_epu8)|AVX2 [2]|immintrin.h|__m256i _mm256_subs_epu8 (\__m256i、\__m256i)|
|[_mm256_testc_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_testc_pd)|AVX [2]|immintrin.h|int _mm256_testc_pd (\__m256d、\__m256d)|
|[_mm256_testc_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_testc_ps)|AVX [2]|immintrin.h|int _mm256_testc_ps (\__m256、\__m256)|
|[_mm256_testc_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_testc_si256)|AVX [2]|immintrin.h|int _mm256_testc_si256 (\__m256i、\__m256i)|
|[_mm256_testnzc_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_testnzc_pd)|AVX [2]|immintrin.h|int _mm256_testnzc_pd (\__m256d、\__m256d)|
|[_mm256_testnzc_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_testnzc_ps)|AVX [2]|immintrin.h|int _mm256_testnzc_ps (\__m256、\__m256)|
|[_mm256_testnzc_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_testnzc_si256)|AVX [2]|immintrin.h|int _mm256_testnzc_si256 (\__m256i、\__m256i)|
|[_mm256_testz_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_testz_pd)|AVX [2]|immintrin.h|int _mm256_testz_pd (\__m256d、\__m256d)|
|[_mm256_testz_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_testz_ps)|AVX [2]|immintrin.h|int _mm256_testz_ps (\__m256、\__m256)|
|[_mm256_testz_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_testz_si256)|AVX [2]|immintrin.h|int _mm256_testz_si256 (\__m256i、\__m256i)|
|[_mm256_unpackhi_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_unpackhi_epi16)|AVX2 [2]|immintrin.h|__m256i _mm256_unpackhi_epi16 (\__m256i、\__m256i)|
|[_mm256_unpackhi_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_unpackhi_epi32)|AVX2 [2]|immintrin.h|__m256i _mm256_unpackhi_epi32 (\__m256i、\__m256i)|
|[_mm256_unpackhi_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_unpackhi_epi64)|AVX2 [2]|immintrin.h|__m256i _mm256_unpackhi_epi64 (\__m256i、\__m256i)|
|[_mm256_unpackhi_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_unpackhi_epi8)|AVX2 [2]|immintrin.h|__m256i _mm256_unpackhi_epi8 (\__m256i、\__m256i)|
|[_mm256_unpackhi_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_unpackhi_pd)|AVX [2]|immintrin.h|__m256d _mm256_unpackhi_pd (\__m256d、\__m256d)|
|[_mm256_unpackhi_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_unpackhi_ps)|AVX [2]|immintrin.h|__m256 _mm256_unpackhi_ps (\__m256、\__m256)|
|[_mm256_unpacklo_epi16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_unpacklo_epi16)|AVX2 [2]|immintrin.h|__m256i _mm256_unpacklo_epi16 (\__m256i、\__m256i)|
|[_mm256_unpacklo_epi32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_unpacklo_epi32)|AVX2 [2]|immintrin.h|__m256i _mm256_unpacklo_epi32 (\__m256i、\__m256i)|
|[_mm256_unpacklo_epi64](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_unpacklo_epi64)|AVX2 [2]|immintrin.h|__m256i _mm256_unpacklo_epi64 (\__m256i、\__m256i)|
|[_mm256_unpacklo_epi8](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_unpacklo_epi8)|AVX2 [2]|immintrin.h|__m256i _mm256_unpacklo_epi8 (\__m256i、\__m256i)|
|[_mm256_unpacklo_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_unpacklo_pd)|AVX [2]|immintrin.h|__m256d _mm256_unpacklo_pd (\__m256d、\__m256d)|
|[_mm256_unpacklo_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_unpacklo_ps)|AVX [2]|immintrin.h|__m256 _mm256_unpacklo_ps (\__m256、\__m256)|
|[_mm256_xor_pd](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_xor_pd)|AVX [2]|immintrin.h|__m256d _mm256_xor_pd (\__m256d、\__m256d)|
|[_mm256_xor_ps](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_xor_ps)|AVX [2]|immintrin.h|__m256 _mm256_xor_ps (\__m256、\__m256)|
|[_mm256_xor_si256](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_xor_si256)|AVX2 [2]|immintrin.h|__m256i _mm256_xor_si256 (\__m256i、\__m256i)|
|[_mm256_zeroall](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_zeroall)|AVX [2]|immintrin.h|void _mm256_zeroall(void)|
|[_mm256_zeroupper](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_mm256_zeroupper)|AVX [2]|immintrin.h|void _mm256_zeroupper(void)|
|[__movsb](movsb.md)||intrin.h|void __movsb (unsigned char \*、unsigned char const \*、size_t)|
|[__movsd](movsd.md)||intrin.h|void __movsd (unsigned long \*、unsigned long const \*、size_t)|
|[__movsw](movsw.md)||intrin.h|void __movsw (unsigned short \*、unsigned short const \*、size_t)|
|_mulx_u32|BMI [2]|immintrin.h|unsigned int _mulx_u32 (unsigned int、unsigned int、unsigned int\*)|
|[__nop](nop.md)||intrin.h|void __nop(void)|
|__nvreg_restore_fence||intrin.h|void __nvreg_restore_fence(void)|
|__nvreg_save_fence||intrin.h|void __nvreg_save_fence(void)|
|[__outbyte](outbyte.md)||intrin.h|void __outbyte(unsigned short, unsigned char)|
|[__outbytestring](outbytestring.md)||intrin.h|void __outbytestring (unsigned short、unsigned char \*、unsigned long)|
|[__outdword](outdword.md)||intrin.h|void __outdword (unsigned short、unsigned long)|
|[__outdwordstring](outdwordstring.md)||intrin.h|void __outdwordstring (unsigned short、unsigned long \*、unsigned long)|
|[__outword](outword.md)||intrin.h|void __outword (unsigned short、unsigned short)|
|[__outwordstring](outwordstring.md)||intrin.h|void __outwordstring (unsigned short、unsigned short \*、unsigned long)|
|[_pdep_u32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_pdep_u32)|BMI [2]|immintrin.h|unsigned int _pdep_u32(unsigned int, unsigned int)|
|[_pext_u32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_pext_u32)|BMI [2]|immintrin.h|unsigned int _pext_u32(unsigned int, unsigned int)|
|[__popcnt](popcnt16-popcnt-popcnt64.md)|POPCNT|intrin.h|unsigned int __popcnt(unsigned int)|
|[__popcnt16](popcnt16-popcnt-popcnt64.md)|POPCNT|intrin.h|unsigned short __popcnt16(unsigned short)|
|[_rdrand16_step](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_rdrand16_step)|RDRAND [2]|immintrin.h|int _rdrand16_step (unsigned short \*)|
|[_rdrand32_step](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_rdrand32_step)|RDRAND [2]|immintrin.h|int _rdrand32_step (unsigned int \*)|
|[_rdseed16_step](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_rdseed16_step)|RDSEED [2]|immintrin.h|int _rdseed16_step (unsigned short \*)|
|[_rdseed32_step](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_rdseed32_step)|RDSEED [2]|immintrin.h|int _rdseed32_step (unsigned int \*)|
|[__rdtsc](rdtsc.md)||intrin.h|署名されていない __int64 \__rdtsc (void)|
|[__rdtscp](rdtscp.md)|RDTSCP|intrin.h|署名されていない __int64 \__rdtscp (unsigned int\*)|
|[_ReadBarrier](readbarrier.md)||intrin.h|void _ReadBarrier(void)|
|[__readcr0](readcr0.md)||intrin.h|unsigned long __readcr0(void)|
|[__readcr2](readcr2.md)||intrin.h|unsigned long __readcr2(void)|
|[__readcr3](readcr3.md)||intrin.h|unsigned long __readcr3(void)|
|[__readcr4](readcr4.md)||intrin.h|unsigned long __readcr4(void)|
|[__readcr8](readcr8.md)||intrin.h|unsigned long __readcr8(void)|
|[__readdr](readdr.md)||intrin.h|unsigned __readdr(unsigned)|
|[__readeflags](readeflags.md)||intrin.h|unsigned __readeflags(void)|
|[__readfsbyte](readfsbyte-readfsdword-readfsqword-readfsword.md)||intrin.h|unsigned char __readfsbyte(unsigned long)|
|[__readfsdword](readfsbyte-readfsdword-readfsqword-readfsword.md)||intrin.h|unsigned long __readfsdword (unsigned long)|
|[__readfsword](readfsbyte-readfsdword-readfsqword-readfsword.md)||intrin.h|unsigned short __readfsword (unsigned long)|
|[__readmsr](readmsr.md)||intrin.h|署名されていない __int64 \__readmsr (unsigned long)|
|[__readpmc](readpmc.md)||intrin.h|署名されていない __int64 \__readpmc (unsigned long)|
|[_ReadWriteBarrier](readwritebarrier.md)||intrin.h|void _ReadWriteBarrier(void)|
|[_ReturnAddress](returnaddress.md)||intrin.h|void \* _ReturnAddress (void)|
|_rorx_u32|BMI [2]|immintrin.h|unsigned int _rorx_u32(unsigned int, const unsigned int)|
|[_rotl16](rotl8-rotl16.md)||intrin.h|unsigned short _rotl16 (unsigned short、unsigned char)|
|[_rotl8](rotl8-rotl16.md)||intrin.h|unsigned char _rotl8 (unsigned char, unsigned char)|
|[_rotr16](rotr8-rotr16.md)||intrin.h|unsigned short _rotr16 (unsigned short、unsigned char)|
|[_rotr8](rotr8-rotr16.md)||intrin.h|unsigned char _rotr8 (unsigned char, unsigned char)|
|_rsm||intrin.h|void _rsm(void)|
|_sarx_i32|BMI [2]|immintrin.h|int _sarx_i32(int, unsigned int)|
|[__segmentlimit](segmentlimit.md)||intrin.h|unsigned long __segmentlimit(unsigned long)|
|_sgdt||intrin.h|void _sgdt (void\*)|
|_shlx_u32|BMI [2]|immintrin.h|unsigned int _shlx_u32(unsigned int, unsigned int)|
|_shrx_u32|BMI [2]|immintrin.h|unsigned int _shrx_u32(unsigned int, unsigned int)|
|[__sidt](sidt.md)||intrin.h|void __sidt (void\*)|
|__slwpcb|LWP [1]|ammintrin.h|void \*__slwpcb (void)|
|_stac|SMAP|intrin.h|void _stac(void)|
|_store_be_u16<br /><br /> [_storebe_i16](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_storebe_i16&expand=5141)|MOVBE|immintrin.h|void _store_be_u16 (void \*、unsigned short);<br /><br /> void _storebe_i16 (void \*, short);番|
|_store_be_u32<br /><br /> [_storebe_i32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_storebe_i32&expand=5142)|MOVBE|immintrin.h|void _store_be_u32 (void \*、unsigned int);<br /><br /> void _storebe_i32 (void \*, int);番|
|_Store_HLERelease|HLE [2]|immintrin.h|void _Store_HLERelease (long volatile \*、long)|
|_StorePointer_HLERelease|HLE [2]|immintrin.h|void _StorePointer_HLERelease (void \* volatile \*、void \*)|
|[__stosb](stosb.md)||intrin.h|void __stosb (unsigned char \*、unsigned char、size_t)|
|[__stosd](stosd.md)||intrin.h|void __stosd (unsigned long \*、unsigned long、size_t)|
|[__stosw](stosw.md)||intrin.h|void __stosw (unsigned short \*、unsigned short、size_t)|
|_subborrow_u16||intrin.h|unsigned char _subborrow_u16 (unsigned char、unsigned short、unsigned short、unsigned short \*)|
|[_subborrow_u32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_subborrow_u32)||intrin.h|unsigned char _subborrow_u32 (unsigned char、unsigned int、unsigned int、unsigned int \*)|
|_subborrow_u8||intrin.h|unsigned char _subborrow_u8 (unsigned char、unsigned char、unsigned char、unsigned char \*)|
|[__svm_clgi](svm-clgi.md)||intrin.h|void __svm_clgi(void)|
|[__svm_invlpga](svm-invlpga.md)||intrin.h|void __svm_invlpga (void\*, int)|
|[__svm_skinit](svm-skinit.md)||intrin.h|void __svm_skinit(int)|
|[__svm_stgi](svm-stgi.md)||intrin.h|void __svm_stgi(void)|
|[__svm_vmload](svm-vmload.md)||intrin.h|void __svm_vmload(size_t)|
|[__svm_vmrun](svm-vmrun.md)||intrin.h|void __svm_vmrun(size_t)|
|[__svm_vmsave](svm-vmsave.md)||intrin.h|void __svm_vmsave(size_t)|
|_t1mskc_u32|ABM [1]|ammintrin.h|unsigned int _t1mskc_u32(unsigned int)|
|[_tzcnt_u32](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_tzcnt_u32)|BMI|ammintrin.h, immintrin.h|unsigned int _tzcnt_u32(unsigned int)|
|_tzmsk_u32|ABM [1]|ammintrin.h|unsigned int _tzmsk_u32(unsigned int)|
|[__ud2](ud2.md)||intrin.h|void __ud2(void)|
|[_udiv64](udiv64.md)||intrin.h|unsigned int \_udiv64 (unsigned \__int64、unsigned int、unsigned int \*)|
|[__ull_rshift](ull-rshift.md)||intrin.h|署名されていない __int64 [pascal/cdecl] \__ull_rshift (符号なし \__int64, int)|
|[__vmx_off](vmx-off.md)||intrin.h|void __vmx_off(void)|
|[__vmx_vmptrst](vmx-vmptrst.md)||intrin.h|void __vmx_vmptrst (unsigned \__int64 \*)|
|[__wbinvd](wbinvd.md)||intrin.h|void __wbinvd(void)|
|[_WriteBarrier](writebarrier.md)||intrin.h|void _WriteBarrier(void)|
|[__writecr0](writecr0.md)||intrin.h|void __writecr0(unsigned long)|
|[__writecr3](writecr3.md)||intrin.h|void __writecr3(unsigned long)|
|[__writecr4](writecr4.md)||intrin.h|void __writecr4(unsigned long)|
|[__writecr8](writecr8.md)||intrin.h|void __writecr8(unsigned long)|
|[__writedr](writedr.md)||intrin.h|void __writedr (符号なし、符号なし)|
|[__writeeflags](writeeflags.md)||intrin.h|void __writeeflags(unsigned)|
|[__writefsbyte](writefsbyte-writefsdword-writefsqword-writefsword.md)||intrin.h|void __writefsbyte (unsigned long、unsigned char)|
|[__writefsdword](writefsbyte-writefsdword-writefsqword-writefsword.md)||intrin.h|void __writefsdword (unsigned long、unsigned long)|
|[__writefsword](writefsbyte-writefsdword-writefsqword-writefsword.md)||intrin.h|void __writefsword (unsigned long、unsigned short)|
|[__writemsr](writemsr.md)||intrin.h|void __writemsr (unsigned long、unsigned \__int64)|
|[_xabort](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_xabort)|RTM [2]|immintrin.h|void _xabort(unsigned int)|
|[_xbegin](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_xbegin)|RTM [2]|immintrin.h|unsigned _xbegin(void)|
|[_xend](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_xend)|RTM [2]|immintrin.h|void _xend(void)|
|[_xgetbv](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_xgetbv)|XSAVE [2]|immintrin.h|unsigned __int64 _xgetbv(unsigned int)|
|[_xrstor](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_xrstor)|XSAVE [2]|immintrin.h|void _xrstor (void const\*、unsigned \__int64)|
|[_xsave](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_xsave)|XSAVE [2]|immintrin.h|void _xsave (void\*、unsigned \__int64)|
|[_xsaveopt](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_xsaveopt)|XSAVEOPT [2]|immintrin.h|void _xsaveopt (void\*、unsigned \__int64)|
|[_xsetbv](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_xsetbv)|XSAVE [2]|immintrin.h|void _xsetbv (符号なし整数、符号なし \__int64)|
|[_xtest](https://software.intel.com/sites/landingpage/IntrinsicsGuide/#text=_xtest)|XTEST [2]|immintrin.h|unsigned char _xtest(void)|

## <a name="see-also"></a>参照

[コンパイラの組み込み](compiler-intrinsics.md)\
[ARM 組み込み](arm-intrinsics.md)\
[ARM64 組み込み](arm64-intrinsics.md)\
[x64 (amd64) 組み込み](x64-amd64-intrinsics-list.md)
