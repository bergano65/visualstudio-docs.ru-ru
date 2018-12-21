---
title: CV_CFL_LANG | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- CV_CFL_LANG enumeration
ms.assetid: 4e8e0613-ad02-4de9-9f46-e4753c5b0251
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f6e2aa402d3f882d83525b180707653b97533e32
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51724788"
---
# <a name="cvcfllang"></a>CV_CFL_LANG
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Задает язык исходного кода приложения или связанном модуле.  
  
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
 Язык — C.  
  
 CV_CFL_CXX  
 Язык приложения — C++.  
  
 CV_CFL_FORTRAN  
 Язык приложения — FORTRAN.  
  
 CV_CFL_MASM  
 Язык приложения — Microsoft Macro Assembler.  
  
 CV_CFL_PASCAL  
 Язык приложения — Pascal.  
  
 CV_CFL_BASIC  
 Язык — BASIC.  
  
 CV_CFL_COBOL  
 Язык приложения — COBOL.  
  
 CV_CFL_LINK  
 Приложения — это модуль компоновщиком.  
  
 CV_CFL_CVTRES  
 Приложение — преобразовать с помощью средства CVTRES модуля ресурсов.  
  
 CV_CFL_CVTPGD  
 Приложения — это модуль POGO оптимизированных для операций, созданных с помощью средства CVTPGD.  
  
 CV_CFL_CSHARP  
 Приложение языком является C#.  
  
 CV_CFL_VB  
 Язык приложения — Visual Basic.  
  
 CV_CFL_ILASM  
 Язык приложения — сборке на промежуточном языке (то есть сборка Common Language Runtime (CLR)).  
  
 CV_CFL_JAVA  
 Язык приложения — Java.  
  
 CV_CFL_JSCRIPT  
 Язык приложения является Jscript.  
  
 CV_CFL_MSIL  
 Язык приложения — Неизвестный язык MSIL (Microsoft Intermediate), возможно, результат применения [/LTCG (Создание кода во время компоновки)](http://msdn.microsoft.com/library/788c6f52-fdb8-40c2-90af-4026ea2cf2e2) переключения.  
  
 CV_CFL_HLSL  
 High Level Shader Language — язык приложения  
  
## <a name="remarks"></a>Примечания  
 Значения в этом перечислении возвращаются путем вызова [IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md) метод.  
  
## <a name="requirements"></a>Требования  
 Заголовок: cvconst.h  
  
## <a name="see-also"></a>См. также  
 [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)



