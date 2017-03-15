---
title: "IDebugNoSymbolsEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Интерфейс IDebugNoSymbolsEvent2"
ms.assetid: f6fb6388-47f6-4385-9ad5-95d62f9a7592
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# IDebugNoSymbolsEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Сигнализирует [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] пользовательский интерфейс отладчика для предупреждения пользователей, что символы не удалось обнаружить для запущенного исполняемого файла.  
  
## Синтаксис  
  
```  
IDebugNoSymbolsEvent2 : IUnknown  
```  
  
## Примечания по реализации  
 Реализация обработчиков отладки и используемых by [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] пользовательский интерфейс отладчика.  
  
## Требования  
 Заголовок: Msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll