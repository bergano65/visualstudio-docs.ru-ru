---
title: "Перечислитель кода команды | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Перечислитель кода команды"
  - "Источник подключаемые модули управления, команда кода перечисления"
ms.assetid: 5d2c360c-59e4-4da8-bcb4-dd07c7441e40
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# Перечислитель кода команды
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Этот перечислитель используется в параметрах [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) и [SccPopulateList](../extensibility/sccpopulatelist-function.md)для указания команды, для которого заданы параметры.  
  
## Синтаксис  
  
```  
enum SCCCOMMAND {  
   SCC_COMMAND_GET,  
   SCC_COMMAND_CHECKOUT,  
   SCC_COMMAND_CHECKIN,  
   SCC_COMMAND_UNCHECKOUT,  
   SCC_COMMAND_ADD,  
   SCC_COMMAND_REMOVE,  
   SCC_COMMAND_DIFF,  
   SCC_COMMAND_HISTORY,  
   SCC_COMMAND_RENAME,  
   SCC_COMMAND_PROPERTIES,  
   SCC_COMMAND_OPTIONS  
};  
```  
  
## Участники  
 SCC\_COMMAND\_GET  
 Соответствует [SccGet](../extensibility/sccget-function.md).  
  
 SCC\_COMMAND\_CHECKOUT  
 Соответствует [SccCheckout](../extensibility/scccheckout-function.md).  
  
 SCC\_COMMAND\_CHECKIN  
 Соответствует [SccCheckin](../extensibility/scccheckin-function.md).  
  
 SCC\_COMMAND\_UNCHECKOUT  
 Соответствует [SccUncheckout](../extensibility/sccuncheckout-function.md).  
  
 SCC\_COMMAND\_ADD  
 Соответствует [SccAdd](../extensibility/sccadd-function.md).  
  
 SCC\_COMMAND\_REMOVE  
 Соответствует [SccRemove](../extensibility/sccremove-function.md).  
  
 SCC\_COMMAND\_DIFF  
 Соответствует [SccDiff](../extensibility/sccdiff-function.md).  
  
 SCC\_COMMAND\_HISTORY  
 Соответствует [SccHistory](../extensibility/scchistory-function.md).  
  
 SCC\_COMMAND\_RENAME  
 Соответствует [SccRename](../extensibility/sccrename-function.md).  
  
 SCC\_COMMAND\_PROPERTIES  
 Соответствует [SccProperties](../extensibility/sccproperties-function.md).  
  
 SCC\_COMMAND\_OPTIONS  
 Соответствует [SccSetOption](../extensibility/sccsetoption-function.md).  
  
## См. также  
 [Подключаемые модули управления версиями](../extensibility/source-control-plug-ins.md)   
 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)   
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)