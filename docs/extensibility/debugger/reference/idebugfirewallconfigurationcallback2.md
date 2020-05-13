---
title: IDebugFireFirewallConfigurationCallback2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFirewallConfigurationCallback2 interface
ms.assetid: 0827361c-b97c-4851-9898-ab6d88c81811
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 635771fc87326b28566058a43d4922b131ae1975
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728712"
---
# <a name="idebugfirewallconfigurationcallback2"></a>IDebugFirewallConfigurationCallback2
Позволяет отладить двигатель, который использует [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] DCOM, чтобы спросить uI, чтобы убедиться, что брандмауэр не будет блокировать удаленную отладку.

## <a name="syntax"></a>Синтаксис

```
IDebugFirewallConfigurationCallback2 : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Реализовано портовым объектом диспетчера отладки сеанса.

## <a name="methods"></a>Методы
 В следующей таблице показаны методы `IDebugFirewallConfigurationCallback2`.

|Метод|Описание|
|------------|-----------------|
|[EnsureDCOMUnblocked](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2-ensuredcomunblocked.md)|Запросы, чтобы брандмауэр не блокировал удаленную отладку.|

## <a name="requirements"></a>Требования
 Заголовок: Msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll
