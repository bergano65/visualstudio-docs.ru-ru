---
title: CV_call_e | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
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
- CV_call_e enumeration
ms.assetid: f230560b-4243-432d-8f19-46df112043b9
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8d4d001b1c6c2df10b8263fa9b0c5f5be360c9e9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47559472"
---
# <a name="cvcalle"></a>CV_call_e
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [CV_call_e](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/cv-call-e).  
  
Определяет соглашение вызова для функции.  
  
> [!NOTE]
>  Здесь описаны только наиболее часто встречающихся значений перечисления. В файле заголовка cvconst.h доступен полный перечисления.  
  
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
 Определяет соглашение о вызове функций, с помощью практически извещающей справа налево. Вызываемая функция очищает стек.  
  
 CV_CALL_NEAR_FAST  
 Определяет соглашение о вызове функций, с помощью практически извещающей слева направо с помощью регистров. Эта функция использует количеству байтов, параметр для очистки стека.  
  
 CV_CALL_NEAR_STD  
 Определяет соглашение о вызове функций, с помощью практически стандартный вызов (отправка справа налево).  
  
 CV_CALL_NEAR_SYS  
 Определяет соглашение о вызове функций, с помощью практически системного вызова.  
  
 CV_CALL_THISCALL  
 Задает соглашение о вызове функций с помощью `this` вызова (`this` указатель передан в регистре).  
  
 CV_CALL_CLRCALL  
 Определяет соглашение о вызове функций, используемые с Common Language Runtime (CLR) (также известный как управляемый код соглашение о вызовах).  
  
## <a name="remarks"></a>Примечания  
 Значения в этом перечислении возвращаются путем вызова [IDiaSymbol::get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md) метод.  
  
## <a name="requirements"></a>Требования  
 Заголовок: cvconst.h  
  
## <a name="see-also"></a>См. также  
 [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)



