---
title: "Перечисление JsMemoryEventType | Документы Майкрософт"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsMemoryEventType
helpviewer_keywords: JsMemoryEventType enumeration
ms.assetid: b4b176b6-b536-472e-8999-95b681a1df55
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ef39008ba84337cebdc9613db17cc9fbdfc8aa79
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="jsmemoryeventtype-enumeration"></a>Перечисление JsMemoryEventType
Тип события обратного вызова выделения.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
enum JsMemoryEventType;  
```  
  
## <a name="members"></a>Члены  
  
### <a name="values"></a>Значения  
  
|Имя|Описание|  
|----------|-----------------|  
|`JsMemoryAllocate`|Обозначает запрос на выделение памяти.|  
|`JsMemoryFailure`|Обозначает завершившееся сбоем событие выделения.|  
|`JsMemoryFree`|Обозначает событие освобождения памяти.|  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jsrt.h  
  
## <a name="see-also"></a>См. также  
 [Справочник (среда выполнения JavaScript)](../chakra-hosting/reference-javascript-runtime.md)