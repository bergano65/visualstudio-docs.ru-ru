---
title: Перечислитель кода команды | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- command code enumerator
- source control plug-ins, command code enumeration
ms.assetid: 5d2c360c-59e4-4da8-bcb4-dd07c7441e40
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 06f1a3f7146125e59d02efc72a4d4fc9ab33be39
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184390"
---
# <a name="command-code-enumerator"></a>Перечислитель кода команды
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Этот перечислитель используется в параметрах [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) и [сккпопулателист](../extensibility/sccpopulatelist-function.md)для указания команды, для которой указаны параметры.  
  
## <a name="syntax"></a>Синтаксис  
  
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
  
## <a name="members"></a>Участники  
 SCC_COMMAND_GET  
 Соответствует [сккжет](../extensibility/sccget-function.md).  
  
 SCC_COMMAND_CHECKOUT  
 Соответствует [сккчеккаут](../extensibility/scccheckout-function.md).  
  
 SCC_COMMAND_CHECKIN  
 Соответствует [сккчеккин](../extensibility/scccheckin-function.md).  
  
 SCC_COMMAND_UNCHECKOUT  
 Соответствует [сккунчеккаут](../extensibility/sccuncheckout-function.md).  
  
 SCC_COMMAND_ADD  
 Соответствует [сккадд](../extensibility/sccadd-function.md).  
  
 SCC_COMMAND_REMOVE  
 Соответствует [сккремове](../extensibility/sccremove-function.md).  
  
 SCC_COMMAND_DIFF  
 Соответствует [сккдифф](../extensibility/sccdiff-function.md).  
  
 SCC_COMMAND_HISTORY  
 Соответствует [скчистори](../extensibility/scchistory-function.md).  
  
 SCC_COMMAND_RENAME  
 Соответствует [сккренаме](../extensibility/sccrename-function.md).  
  
 SCC_COMMAND_PROPERTIES  
 Соответствует [сккпропертиес](../extensibility/sccproperties-function.md).  
  
 SCC_COMMAND_OPTIONS  
 Соответствует [скксетоптион](../extensibility/sccsetoption-function.md).  
  
## <a name="see-also"></a>См. также:  
 [Подключаемые модули системы управления версиями](../extensibility/source-control-plug-ins.md)   
 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)   
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)
