---
title: CV_CFL_LANG | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CV_CFL_LANG enumeration
ms.assetid: 4e8e0613-ad02-4de9-9f46-e4753c5b0251
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c383fd188c035dfacf41cdf86a84b4afe8dfa40d
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
ms.locfileid: "31461058"
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
 CV_CFL_C  
 Язык приложения — C.  
  
 CV_CFL_CXX  
 Язык приложения — C++.  
  
 CV_CFL_FORTRAN  
 Язык приложения — FORTRAN.  
  
 CV_CFL_MASM  
 Язык приложения — Microsoft Macro Assembler.  
  
 CV_CFL_PASCAL  
 Язык приложения — стиль языка Pascal.  
  
 CV_CFL_BASIC  
 Язык приложения — BASIC.  
  
 CV_CFL_COBOL  
 Язык приложения — COBOL.  
  
 CV_CFL_LINK  
 Приложения — это модуль, создаваемой компоновщиком.  
  
 CV_CFL_CVTRES  
 Приложение — преобразовать с помощью средства CVTRES модуля ресурсов.  
  
 CV_CFL_CVTPGD  
 Приложения — это модуль POGO оптимизирован, созданные с помощью средства CVTPGD.  
  
 CV_CFL_CSHARP  
 Язык приложения — C#.  
  
 CV_CFL_VB  
 Язык приложения является Visual Basic.  
  
 CV_CFL_ILASM  
 Язык приложения — промежуточный язык сборки (то есть Common Language Runtime (CLR)).  
  
 CV_CFL_JAVA  
 Язык приложения — Java.  
  
 CV_CFL_JSCRIPT  
 Язык приложения — Jscript.  
  
 CV_CFL_MSIL  
 Язык приложения — Неизвестный Microsoft промежуточного языка MSIL, возможно результат использования [/LTCG (Создание кода во время компоновки)](/cpp/build/reference/ltcg-link-time-code-generation) переключения.  
  
 CV_CFL_HLSL  
 Приложения выбран язык шейдера высокий уровень.  
  
## <a name="remarks"></a>Примечания  
 Значения в этом перечислении возвращаются путем вызова [IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md) метод.  
  
## <a name="requirements"></a>Требования  
 Заголовок: cvconst.h  
  
## <a name="see-also"></a>См. также  
 [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)