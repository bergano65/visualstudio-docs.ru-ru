---
title: "IDebugGenericFieldDefinition | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Интерфейс IDebugGenericFieldDefinition"
ms.assetid: b5a853b7-221e-4d62-8948-07423089d75d
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugGenericFieldDefinition
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Представляет определение поля для универсального типа управляемого кода.  
  
## Синтаксис  
  
```  
IDebugGenericFieldDefinition : IUnknown  
```  
  
## Методы  
 Этот интерфейс реализует следующие методы:  
  
|Метод|Описание|  
|-----------|--------------|  
|[ConstructInstantiation](../../../extensibility/debugger/reference/idebuggenericfielddefinition-constructinstantiation.md)|Создает экземпляр поля заданный массив аргументов типа.|  
|[GetFormalTypeParams](../../../extensibility/debugger/reference/idebuggenericfielddefinition-getformaltypeparams.md)|Получает параметры типа заданное число параметров.|  
|[TypeParamCount](../../../extensibility/debugger/reference/idebuggenericfielddefinition-typeparamcount.md)|Извлекает число параметров типа, связанных с родовым полем.|  
  
## Требования  
 Заголовок: Sh.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll