---
title: IDebugProcessQueryProperties | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessQueryProperties
ms.assetid: ce29a248-81a0-42c0-99a7-1606e8c548ec
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e54c51e4012bf129e7f8a8ad44fac8dca3e888c1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62917519"
---
# <a name="idebugprocessqueryproperties"></a>IDebugProcessQueryProperties
Этот интерфейс является расширением интерфейса, реализуемого [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) разработчиков. Он позволяет получить сведения о среде отладки процесса.

## <a name="syntax"></a>Синтаксис

```
IDebugProcessQueryProperties: IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Реализуйте этот интерфейс для получения сведений о среде выполнения процесса отладки.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugProcessQueryProperties`.

|Метод|Описание|
|------------|-----------------|
|[QueryProperty](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperty.md)|Запросы для значения свойства.|
|[QueryProperties](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperties.md)|Запросы для получения значений свойств.|

## <a name="remarks"></a>Примечания
 Этот интерфейс реализуется редко.

## <a name="requirements"></a>Требования
 Заголовок: Portpriv.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)