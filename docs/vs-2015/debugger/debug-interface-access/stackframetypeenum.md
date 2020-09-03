---
title: Стаккфраметипинум | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- StackFrameTypeEnum enumeration
ms.assetid: 61e40163-eee0-4c1f-af47-cef3771bdc41
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 655911bac1efbafe1838e24e2056282f9036479b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179188"
---
# <a name="stackframetypeenum"></a>StackFrameTypeEnum
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Указывает тип кадра стека.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
enum StackFrameTypeEnum {  
   FrameTypeFPO,  
   FrameTypeTrap,  
   FrameTypeTSS,  
   FrameTypeStandard,  
   FrameTypeFrameData,  
   FrameTypeUnknown = -1  
};  
```  
  
## <a name="elements"></a>Элементы  
 `FrameTypeFPO`  
 Пропущен указатель фрейма; Сведения о FPO доступны.  
  
 `FrameTypeTrap`  
 Кадр ловушки ядра.  
  
 `FrameTypeTSS`  
 Кадр ловушки ядра.  
  
 `FrameTypeStandard`  
 Стандартный фрейм стека EBP.  
  
 `FrameTypeFrameData`  
 Пропущен указатель фрейма; Сведения о данных кадра доступны.  
  
 `FrameTypeUnknown`  
 Кадр, у которого нет отладочной информации.  
  
## <a name="remarks"></a>Remarks  
 Значения в этом перечислении возвращаются путем вызова метода [IDiaStackFrame:: get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md) .  
  
## <a name="requirements"></a>Требования  
 Заголовок: квконст. h  
  
## <a name="see-also"></a>См. также:  
 [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaStackFrame::get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)
