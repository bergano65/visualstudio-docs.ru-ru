---
title: "Интерфейс IEnumJsStackFrames | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 49e7b425-df17-4d7f-87ff-0bc82715c911
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Интерфейс IEnumJsStackFrames
Реализуется отладчиком для предоставления раскрутки стека для jscript9diag.dll для JavaScript.  
  
## Синтаксис  
  
```  
IEnumJsStackFrames : public IUnknown;  
```  
  
## Члены  
  
### Открытые методы  
  
|Имя|Описание|  
|---------|--------------|  
|[Метод IEnumJsStackFrames::Next](../../winscript/reference/ienumjsstackframes-next-method.md)|Получает указанное количество кадров.|  
|[Метод IEnumJsStackFrames::Reset](../../winscript/reference/ienumjsstackframes-reset-method.md)|Сбрасывает кадр стека в положение перед первым элементом.|  
  
## Требования  
 **Заголовок:** jscript9diag.h  
  
## См. также  
 [Справочник по интерфейсам скриптов Windows](../../winscript/reference/windows-script-interfaces-reference.md)