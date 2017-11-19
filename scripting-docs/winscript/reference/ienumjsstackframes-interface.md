---
title: "Интерфейс IEnumJsStackFrames | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 49e7b425-df17-4d7f-87ff-0bc82715c911
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 12583f73c9f3977371ebd193716f2513fc0befc4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="ienumjsstackframes-interface"></a>Интерфейс IEnumJsStackFrames
Реализованы отладчиком для предоставления стека очистки для jscript9diag.dll для JavaScript.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IEnumJsStackFrames : public IUnknown;  
```  
  
## <a name="members"></a>Члены  
  
### <a name="public-methods"></a>Открытые методы  
  
|Имя|Описание|  
|----------|-----------------|  
|[Метод IEnumJsStackFrames::Next](../../winscript/reference/ienumjsstackframes-next-method.md)|Возвращает заданное число кадров.|  
|[Метод IEnumJsStackFrames::Reset](../../winscript/reference/ienumjsstackframes-reset-method.md)|Возвращает кадра стека в позицию перед первым элементом.|  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jscript9diag.h  
  
## <a name="see-also"></a>См. также  
 [Справочник по интерфейсам скриптов Windows](../../winscript/reference/windows-script-interfaces-reference.md)