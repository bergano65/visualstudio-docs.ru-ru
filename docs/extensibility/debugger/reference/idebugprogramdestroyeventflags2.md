---
title: IDebugПрограммаУничтожениеСобытий2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgramDestroyEventFlags2 interface
ms.assetid: d384ff71-dc71-40b9-a871-801f8b6a3418
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d869304dd8b6dc82db78cc09ed9d51a54acdc3c0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722501"
---
# <a name="idebugprogramdestroyeventflags2"></a>IDebugProgramDestroyEventFlags2
Позволяет отладить движок, чтобы переопределить [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] поведение ui по умолчанию при конце сеанса отладки.

## <a name="syntax"></a>Синтаксис

```
IDebugProgramDestroyEventFlags2 : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Этот интерфейс реализован с помощью отладки двигателей. Это полезно для хостов, которые могут создавать и уничтожать несколько программ в течение всего срока действия процесса.

## <a name="methods"></a>Методы
 В следующей таблице показаны методы `IDebugProgramDestroyEventFlags2`.

|Метод|Описание|
|------------|-----------------|
|[GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md)|Получает программу уничтожить флаги.|

## <a name="remarks"></a>Примечания
 Поведение [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] uI по умолчанию заключается в том, чтобы вернуться в режим проектирования после того, как все программы отправили событие уничтожения программы. Этот интерфейс позволяет движку отладки изменить это поведение.

## <a name="requirements"></a>Требования
 Заголовок: Msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll
