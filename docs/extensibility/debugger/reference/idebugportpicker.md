---
title: "IDebugPortPicker | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Интерфейс IDebugPortPicker"
ms.assetid: 8b7f6685-a3c5-4355-b706-c1b574f6ff84
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugPortPicker
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Представляет настраиванный пользовательский интерфейс для выбора порт.  
  
## Синтаксис  
  
```  
IDebugPortPicker : IUnknown  
```  
  
## Примечания по реализации  
 Этот интерфейс реализуется поставщиками порта.  Поставщик порта определяет их выбор порта, предоставление его в качестве идентификатора CLSID и они указывали `metricPortPickerCLSID` показатель на предоставлянном CLSID.  
  
## Методы  
 В следующей таблице показаны методы `IDebugPortPicker`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[DisplayPortPicker](../../../extensibility/debugger/reference/idebugportpicker-displayportpicker.md)|Отображает заданное диалоговое окно, которое позволяет пользователю выбрать порт.|  
|[SetSite](../../../extensibility/debugger/reference/idebugportpicker-setsite.md)|Задает поставщика услуг.|  
  
## Требования  
 Заголовок: Msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll