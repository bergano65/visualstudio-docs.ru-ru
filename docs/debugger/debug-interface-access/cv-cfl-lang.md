---
title: CV_CFL_LANG | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CV_CFL_LANG enumeration
ms.assetid: 4e8e0613-ad02-4de9-9f46-e4753c5b0251
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1f02545f1c19b57e46af302fbc0b2abaa7445612
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56646347"
---
# <a name="cvcfllang"></a>CV_CFL_LANG
Задает язык исходного кода приложения или связанном модуле.

## <a name="syntax"></a>Синтаксис

```C++
typedef enum CV_CFL_LANG {
    CV_CFL_C       = 0x00,
    CV_CFL_CXX     = 0x01,
    CV_CFL_FORTRAN = 0x02,
    CV_CFL_MASM    = 0x03,
    CV_CFL_PASCAL  = 0x04,
    CV_CFL_BASIC   = 0x05,
    CV_CFL_COBOL   = 0x06,
    CV_CFL_LINK    = 0x07,
    CV_CFL_CVTRES  = 0x08,
    CV_CFL_CVTPGD  = 0x09,
    CV_CFL_CSHARP  = 0x0A,
    CV_CFL_VB      = 0x0B,
    CV_CFL_ILASM   = 0x0C,
    CV_CFL_JAVA    = 0x0D,
    CV_CFL_JSCRIPT = 0x0E,
    CV_CFL_MSIL    = 0x0F,
    CV_CFL_HLSL    = 0x10
} CV_CFL_LANG;
```

## <a name="elements"></a>Элементы
Язык приложения CV_CFL_C — C.

Язык приложения CV_CFL_CXX — C++.

Язык приложения CV_CFL_FORTRAN — FORTRAN.

Язык CV_CFL_MASM приложения — Microsoft Macro Assembler.

Язык приложения CV_CFL_PASCAL — Pascal.

Язык приложения CV_CFL_BASIC — BASIC.

Язык приложения CV_CFL_COBOL — COBOL.

CV_CFL_LINK приложения — это модуль компоновщиком.

Приложение CV_CFL_CVTRES — преобразовать с помощью средства CVTRES модуля ресурсов.

CV_CFL_CVTPGD приложения — это модуль POGO оптимизированных для операций, созданных с помощью средства CVTPGD.

Язык приложения CV_CFL_CSHARP C#.

Приложение CV_CFL_VB языком является Visual Basic.

Язык приложения CV_CFL_ILASM — сборке на промежуточном языке (то есть сборка Common Language Runtime (CLR)).

Язык CV_CFL_JAVA приложения — Java.

Язык CV_CFL_JSCRIPT приложения является Jscript.

Язык приложения CV_CFL_MSIL — Неизвестный язык MSIL (Microsoft Intermediate), возможно, результат применения [/LTCG (Создание кода во время компоновки)](/cpp/build/reference/ltcg-link-time-code-generation) переключения.

Язык приложения CV_CFL_HLSL — High Level Shader Language.

## <a name="remarks"></a>Примечания
Значения в этом перечислении возвращаются путем вызова [IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md) метод.

## <a name="requirements"></a>Требования
Заголовок: cvconst.h

## <a name="see-also"></a>См. также раздел
- [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)
