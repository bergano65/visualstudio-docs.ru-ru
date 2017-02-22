---
title: "IDebugFirewallConfigurationCallback2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Интерфейс IDebugFirewallConfigurationCallback2"
ms.assetid: 0827361c-b97c-4851-9898-ab6d88c81811
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugFirewallConfigurationCallback2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Включает отладчик, использует DCOM для запроса [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Пользовательский интерфейс, чтобы убедиться в том, что брандмауэр не блокирует удаленная отладка.  
  
## Синтаксис  
  
```  
IDebugFirewallConfigurationCallback2 : IUnknown  
```  
  
## Примечания по реализации  
 Реализуется объектом порта сеанса отладки диспетчер.  
  
## Методы  
 В следующей таблице показаны методы `IDebugFirewallConfigurationCallback2`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[EnsureDCOMUnblocked](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2-ensuredcomunblocked.md)|Запросы, что удаленная отладка блока брандмауэра нет.|  
  
## Требования  
 Заголовок: Msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll