---
title: CV_call_e | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CV_call_e enumeration
ms.assetid: f230560b-4243-432d-8f19-46df112043b9
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cd1ee4c024894e5752277a5000d37745c88c4ac6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842865"
---
# <a name="cv_call_e"></a>CV_call_e
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Указывает соглашение о вызовах для функции.  
  
> [!NOTE]
> Здесь описаны только наиболее распространенные значения перечисления. Полное перечисление доступно в файле заголовка квконст. h.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
typedef enum CV_call_e {   
   CV_CALL_NEAR_C    = 0x00,  
   CV_CALL_NEAR_FAST = 0x04,  
   CV_CALL_NEAR_STD  = 0x07,  
   CV_CALL_NEAR_SYS  = 0x09,  
   CV_CALL_THISCALL  = 0x0b,  
   CV_CALL_CLRCALL   = 0x16  
} CV_call_e;  
```  
  
## <a name="elements"></a>Элементы  
 CV_CALL_NEAR_C  
 Указывает соглашение о вызове функции с помощью push-уведомлений NEAR слева направо. Вызывающая функция очищает стек.  
  
 CV_CALL_NEAR_FAST  
 Указывает соглашение о вызове функции с помощью push-уведомлений NEAR слева направо с регистрами. Вызываемая функция использует сумму байтов параметров для очистки стека.  
  
 CV_CALL_NEAR_STD  
 Указывает соглашение о вызове функции с использованием ближайших стандартных вызовов (push-уведомлений справа налево).  
  
 CV_CALL_NEAR_SYS  
 Указывает соглашение о вызове функции с помощью ближайшего системного вызова.  
  
 CV_CALL_THISCALL  
 Указывает соглашение о вызове функции с помощью `this` вызова ( `this` переданный указатель передается в регистр).  
  
 CV_CALL_CLRCALL  
 Указывает соглашение о вызове функции, используемое средой CLR (также известное как соглашение о вызовах управляемого кода).  
  
## <a name="remarks"></a>Remarks  
 Значения в этом перечислении возвращаются путем вызова метода [IDiaSymbol:: get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md) .  
  
## <a name="requirements"></a>Требования  
 Заголовок: квконст. h  
  
## <a name="see-also"></a>См. также:  
 [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)
