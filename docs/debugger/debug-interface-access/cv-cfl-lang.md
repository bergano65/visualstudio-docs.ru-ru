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
ms.openlocfilehash: 0fb684d0ff68e5ede6b0847ef9aeba1821ecafcc
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745336"
---
# <a name="cv_cfl_lang"></a>CV_CFL_LANG
Указывает язык исходного кода приложения или связанного модуля.

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

Язык приложения CV_CFL_MASM — Microsoft Macro Assembler.

Язык приложения CV_CFL_PASCAL — это стиль Pascal.

Язык приложения CV_CFL_BASIC является БАЗОВым.

Язык приложения CV_CFL_COBOL — COBOL.

Приложение CV_CFL_LINK — это модуль, созданный компоновщиком.

CV_CFL_CVTRES приложение — это модуль ресурсов, преобразованный с помощью средства CVTRES.

CV_CFL_CVTPGD приложение — это оптимизированный для POGO модуль, созданный с помощью средства КВТПГД.

Язык приложения CV_CFL_CSHARP — C#.

Visual Basic язык приложения CV_CFL_VB.

Язык приложения CV_CFL_ILASM является сборкой промежуточного языка (то есть сборкой среды CLR).

Язык приложения CV_CFL_JAVA — Java.

Язык приложения CV_CFL_JSCRIPT — JScript.

Язык приложения CV_CFL_MSIL — это неизвестный MSIL-код, возможно, в результате использования параметра [/LTCG (создание кода во время компоновки)](/cpp/build/reference/ltcg-link-time-code-generation) .

Язык приложения CV_CFL_HLSL — это язык шейдера высокого уровня.

## <a name="remarks"></a>Заметки
Значения в этом перечислении возвращаются путем вызова метода [IDiaSymbol:: get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md) .

## <a name="requirements"></a>Требования
Заголовок: квконст. h

## <a name="see-also"></a>См. также
- [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)
