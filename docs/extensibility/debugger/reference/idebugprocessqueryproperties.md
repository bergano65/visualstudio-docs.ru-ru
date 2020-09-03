---
title: Идебугпроцесскуерипропертиес | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessQueryProperties
ms.assetid: ce29a248-81a0-42c0-99a7-1606e8c548ec
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 08abf401b4e8f0e7a33d882e8178d77e6f248318
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80723281"
---
# <a name="idebugprocessqueryproperties"></a>IDebugProcessQueryProperties
Этот интерфейс является интерфейсом расширения, реализованным разработчиками [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) . Он позволяет разработчику получить сведения о среде процесса отладки.

## <a name="syntax"></a>Синтаксис

```
IDebugProcessQueryProperties: IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Реализуйте этот интерфейс, чтобы получить сведения о среде выполнения процесса отладки.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugProcessQueryProperties` .

|Метод|Описание|
|------------|-----------------|
|[QueryProperty](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperty.md)|Запрашивает значение свойства.|
|[QueryProperties](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperties.md)|Запросы значений свойств.|

## <a name="remarks"></a>Remarks
 Этот интерфейс реализован редко.

## <a name="requirements"></a>Требования
 Заголовок: Портприв. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
