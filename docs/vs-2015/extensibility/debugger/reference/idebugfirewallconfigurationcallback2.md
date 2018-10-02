---
title: IDebugFirewallConfigurationCallback2 | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugFirewallConfigurationCallback2 interface
ms.assetid: 0827361c-b97c-4851-9898-ab6d88c81811
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8d332b7dab143b1fedbbdfc5ac92dc2b123dfe1b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47571056"
---
# <a name="idebugfirewallconfigurationcallback2"></a>IDebugFirewallConfigurationCallback2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugFirewallConfigurationCallback2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugfirewallconfigurationcallback2).  
  
Включает отладчик, который использует DCOM попросить [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] пользовательского интерфейса, чтобы убедиться в том, что брандмауэр не блокирует удаленную отладку.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugFirewallConfigurationCallback2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Реализованный объект port диспетчер отладки сеансов.  
  
## <a name="methods"></a>Методы  
 В следующей таблице показаны методы `IDebugFirewallConfigurationCallback2`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[EnsureDCOMUnblocked](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2-ensuredcomunblocked.md)|Запросы, что брандмауэр не блокирует удаленную отладку.|  
  
## <a name="requirements"></a>Требования  
 Заголовок: Msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

