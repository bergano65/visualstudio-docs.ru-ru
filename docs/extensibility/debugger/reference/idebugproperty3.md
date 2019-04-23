---
title: IDebugProperty3 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3
helpviewer_keywords:
- IDebugProperty3 interface
ms.assetid: 8f9be68d-4490-4eca-8f6b-8a10ed77e226
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e73310d8a1cff3b640896d9bb5883cf2508bda6e
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60069657"
---
# <a name="idebugproperty3"></a>IDebugProperty3
Этот интерфейс обеспечивает поддержку:

- Извлечение произвольной длины строки, связанный со свойством.

- Уникальный идентификатор сопоставление со свойством.

- Получение списка пользовательских средств просмотра для свойства.

- Значение свойства с возможностью отчетов все возникающие ошибки

## <a name="syntax"></a>Синтаксис

```
IDebugProperty3 : IDebugProperty2
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Модуль отладки (DE) реализует этот интерфейс на тот же объект, реализующий [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) для обеспечения поддержки длинных строк, идентификаторы свойств и пользовательских средств просмотра.

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
 Вызовите [QueryInterface](/cpp/atl/queryinterface) на `IDebugProperty2` интерфейс для получения этого интерфейса.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 Помимо методов, наследуемых от `IDebugProperty2`, `IDebugProperty3` интерфейс предоставляет следующие методы.

|Метод|Описание|
|------------|-----------------|
|[GetStringCharLength](../../../extensibility/debugger/reference/idebugproperty3-getstringcharlength.md)|Возвращает длину строки, связанной со свойством.|
|[GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md)|Возвращает строку в буфер, предоставленный пользователем.|
|[CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)|Создает уникальный идентификатор для этого свойства.|
|[DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)|Уничтожает уникальный идентификатор для этого свойства.|
|[GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)|Возвращает количество пользовательских средств просмотра, это свойство можно просмотреть при помощи.|
|[GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)|Возвращает список пользовательских средств просмотра, это свойство можно просмотреть при помощи.|
|[SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)|Задает значение этого свойства, возвращает сообщение об ошибке, если что-то пошло не так.|

## <a name="remarks"></a>Примечания
- [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) является более предпочтительным для диспетчера отладки сеанса (SDM), чтобы задать значение свойства.

## <a name="requirements"></a>Требования
 Header: msdbg.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)