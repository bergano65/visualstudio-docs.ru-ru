---
title: StackFrameTypeEnum | Документация Майкрософт
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
- StackFrameTypeEnum enumeration
ms.assetid: 61e40163-eee0-4c1f-af47-cef3771bdc41
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 081be0d7b9369462bae703b571629897bd5df94c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47559909"
---
# <a name="stackframetypeenum"></a>StackFrameTypeEnum
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [StackFrameTypeEnum](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/stackframetypeenum).  
  
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
  
## <a name="see-also"></a>См. также  
 [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaStackFrame::get_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)



