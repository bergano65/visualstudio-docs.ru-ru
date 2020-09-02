---
title: IDebugFirewallConfigurationCallback2 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugFirewallConfigurationCallback2 interface
ms.assetid: 0827361c-b97c-4851-9898-ab6d88c81811
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 04d64ac489858e3a912b144b494430aec5b925d5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197047"
---
# <a name="idebugfirewallconfigurationcallback2"></a>IDebugFirewallConfigurationCallback2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Включает модуль отладки, использующий DCOM для запроса [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] пользовательского интерфейса, чтобы убедиться, что брандмауэр не блокирует удаленную отладку.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugFirewallConfigurationCallback2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Реализуется объектом Port диспетчера отладки сеанса.  
  
## <a name="methods"></a>Методы  
 В следующей таблице показаны методы `IDebugFirewallConfigurationCallback2` .  
  
|Метод|Описание|  
|------------|-----------------|  
|[EnsureDCOMUnblocked](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2-ensuredcomunblocked.md)|Запрашивает, чтобы брандмауэр не блокировал удаленную отладку.|  
  
## <a name="requirements"></a>Требования  
 Заголовок: Мсдбг. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll
