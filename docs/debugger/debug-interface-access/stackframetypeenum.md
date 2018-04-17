---
title: StackFrameTypeEnum | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- StackFrameTypeEnum enumeration
ms.assetid: 61e40163-eee0-4c1f-af47-cef3771bdc41
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9c791bbe28db35a33e433ce2e38fac2d34ba46f5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="stackframetypeenum"></a>StackFrameTypeEnum
Указывает тип кадра стека.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
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
 Указатель кадра опустить; FPO сведения недоступны.  
  
 `FrameTypeTrap`  
 Кадр перехвата ядра.  
  
 `FrameTypeTSS`  
 Кадр перехвата ядра.  
  
 `FrameTypeStandard`  
 Стандартная кадр стека EBP.  
  
 `FrameTypeFrameData`  
 Указатель кадра опустить; Сведения кадра данных недоступны.  
  
 `FrameTypeUnknown`  
 Кадр, не имеет сведений о отладки.  
  
## <a name="remarks"></a>Примечания  
 Значения в этом перечислении возвращаются путем вызова [IDiaStackFrame::get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md) метод.  
  
## <a name="requirements"></a>Требования  
 Заголовок: cvconst.h  
  
## <a name="see-also"></a>См. также  
 [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaStackFrame::get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)