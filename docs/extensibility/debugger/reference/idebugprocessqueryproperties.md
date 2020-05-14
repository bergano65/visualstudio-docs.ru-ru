---
title: IDebugПроцессКЕвириСвойства (ru) Документы Майкрософт
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723281"
---
# <a name="idebugprocessqueryproperties"></a>IDebugProcessQueryProperties
Этот интерфейс представляет собой интерфейс расширения, реализованный исполнителями [IDebugProcess2.](../../../extensibility/debugger/reference/idebugprocess2.md) Это позволяет исполнителю получать информацию о среде процесса отладки.

## <a name="syntax"></a>Синтаксис

```
IDebugProcessQueryProperties: IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Реализация этого интерфейса для получения информации о среде выполнения процесса отладки.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugProcessQueryProperties`.

|Метод|Описание|
|------------|-----------------|
|[QueryProperty](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperty.md)|Запросы на стоимость свойства.|
|[QueryProperties](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperties.md)|Запросы на значения свойств.|

## <a name="remarks"></a>Примечания
 Этот интерфейс редко реализуется.

## <a name="requirements"></a>Требования
 Заголовок: Portpriv.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
