---
title: StackFrameTypeEnum | Документация Майкрософт
ms.date: 11/04/2016
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
ms.openlocfilehash: be9a07c961e62870319de10cad77eaee8e12ef1c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53864014"
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
 Указатель на фреймы опустить; FPO сведения недоступны.  
  
 `FrameTypeTrap`  
 Кадр перехвата ядра.  
  
 `FrameTypeTSS`  
 Кадр перехвата ядра.  
  
 `FrameTypeStandard`  
 Стандартный кадр стека EBP.  
  
 `FrameTypeFrameData`  
 Указатель на фреймы опустить; Кадр данных сведения о доступных.  
  
 `FrameTypeUnknown`  
 Кадр, который не поддерживает любой отладочной информации.  
  
## <a name="remarks"></a>Примечания  
 Значения в этом перечислении возвращаются путем вызова [IDiaStackFrame::get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md) метод.  
  
## <a name="requirements"></a>Требования  
 Заголовок: cvconst.h  
  
## <a name="see-also"></a>См. также раздел  
 [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaStackFrame::get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)