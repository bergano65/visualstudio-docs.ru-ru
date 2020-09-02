---
title: CV_CFL_LANG | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CV_CFL_LANG enumeration
ms.assetid: 4e8e0613-ad02-4de9-9f46-e4753c5b0251
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9c1fabdb202d51b85eb2983360bdfd02757f7649
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65699364"
---
# <a name="cv_cfl_lang"></a>CV_CFL_LANG
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Указывает язык исходного кода приложения или связанного модуля.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
 Язык приложения — стиль Pascal.  
  
 CV_CFL_BASIC  
 Язык приложения является БАЗОВым.  
  
 CV_CFL_COBOL  
 Язык приложения — COBOL.  
  
 CV_CFL_LINK  
 Приложение — это модуль, созданный компоновщиком.  
  
 CV_CFL_CVTRES  
 Приложение — это модуль ресурсов, преобразованный с помощью средства CVTRES.  
  
 CV_CFL_CVTPGD  
 Приложение — это оптимизированный для POGO модуль, созданный с помощью средства КВТПГД.  
  
 CV_CFL_CSHARP  
 Язык приложения — C#.  
  
 CV_CFL_VB  
 Язык приложения Visual Basic.  
  
 CV_CFL_ILASM  
 Язык приложения — это сборка промежуточного языка (среда CLR).  
  
 CV_CFL_JAVA  
 Язык приложения — Java.  
  
 CV_CFL_JSCRIPT  
 Язык приложения — JScript.  
  
 CV_CFL_MSIL  
 Язык приложения — неизвестный промежуточный язык (MSIL), возможно, результат использования параметра [/LTCG (создание кода во время компоновки)](https://msdn.microsoft.com/library/788c6f52-fdb8-40c2-90af-4026ea2cf2e2) .  
  
 CV_CFL_HLSL  
 Язык приложения — это язык шейдера высокого уровня.  
  
## <a name="remarks"></a>Remarks  
 Значения в этом перечислении возвращаются путем вызова метода [IDiaSymbol:: get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md) .  
  
## <a name="requirements"></a>Требования  
 Заголовок: квконст. h  
  
## <a name="see-also"></a>См. также:  
 [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)
