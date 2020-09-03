---
title: IDebugProgramDestroyEventFlags2 | Документация Майкрософт
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80722501"
---
# <a name="idebugprogramdestroyeventflags2"></a>IDebugProgramDestroyEventFlags2
Позволяет подсистеме отладки переопределять поведение пользовательского интерфейса по умолчанию [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] при завершении сеанса отладки.

## <a name="syntax"></a>Синтаксис

```
IDebugProgramDestroyEventFlags2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Этот интерфейс реализуется механизмами отладки. Это полезно для узлов, которые могут создавать и уничтожать несколько программ в течение всего времени существования процесса.

## <a name="methods"></a>Методы
 В следующей таблице показаны методы `IDebugProgramDestroyEventFlags2` .

|Метод|Описание|
|------------|-----------------|
|[GetFlags](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2-getflags.md)|Получает флаги удаления программы.|

## <a name="remarks"></a>Remarks
 Поведение пользовательского интерфейса по умолчанию [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] — вернуться в режим конструктора после того, как все программы отправили событие уничтожения программы. Этот интерфейс позволяет механизму отладки изменить это поведение.

## <a name="requirements"></a>Требования
 Заголовок: Мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll
