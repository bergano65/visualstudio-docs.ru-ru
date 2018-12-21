---
title: CV_call_e | Документация Майкрософт
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
- CV_call_e enumeration
ms.assetid: f230560b-4243-432d-8f19-46df112043b9
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f687c9d95444fdad35213b86af2c3ee1a252544e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51726962"
---
# <a name="cvcalle"></a>CV_call_e
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

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



