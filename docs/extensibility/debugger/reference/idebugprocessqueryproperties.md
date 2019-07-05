---
title: IDebugProcessQueryProperties | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessQueryProperties
ms.assetid: ce29a248-81a0-42c0-99a7-1606e8c548ec
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2ddb98c2d7e63fc27ad1469dfbfc76eaaee38582
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353104"
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