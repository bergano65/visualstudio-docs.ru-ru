---
title: CV_call_e | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CV_call_e enumeration
ms.assetid: f230560b-4243-432d-8f19-46df112043b9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fbfde2000b0d22241d795cbb89aa8c28fc330293
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="cvcalle"></a>CV_call_e
Задает соглашение о вызовах для функции.  
  
> [!NOTE]
>  Здесь описаны только наиболее часто встречающихся значений перечисления. В файле заголовка cvconst.h доступен завершения перечисления.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
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
 Определяет соглашение о вызове функций, с помощью извещающей near справа налево. Вызываемая функция очищает стек.  
  
 CV_CALL_NEAR_FAST  
 Определяет соглашение о вызове функций, использование near принудительной справа налево с регистры. Вызываемая функция использует количеству байтов, параметр для очистки стека.  
  
 CV_CALL_NEAR_STD  
 Определяет соглашение о вызове функций, с помощью вызова near standard (Извещающая справа налево).  
  
 CV_CALL_NEAR_SYS  
 Задает соглашение о вызове функций, с помощью near системного вызова.  
  
 CV_CALL_THISCALL  
 Задает соглашение о вызове функций с помощью `this` вызова (`this` указатель передан в регистре).  
  
 CV_CALL_CLRCALL  
 Задает соглашение о вызове функций, используемое с Common Language Runtime (CLR) (также известный как управляемый код соглашение о вызовах).  
  
## <a name="remarks"></a>Примечания  
 Значения в этом перечислении возвращаются путем вызова [IDiaSymbol::get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md) метод.  
  
## <a name="requirements"></a>Требования  
 Заголовок: cvconst.h  
  
## <a name="see-also"></a>См. также  
 [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)