---
title: IDebugPortRequest2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortRequest2
helpviewer_keywords:
- IDebugPortRequest2 interface
ms.assetid: 556e610d-7c4b-44a8-965a-76a9d02b601a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 163718fda344ba5f3f44ef630b4eba3e5613dc61
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724786"
---
# <a name="idebugportrequest2"></a>IDebugPortRequest2
Этот интерфейс описывает порт. Это описание используется для добавления порта к поставщику порта.

## <a name="syntax"></a>Синтаксис

```
IDebugPortRequest2 : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Visual Studio обычно реализует этот интерфейс в процессе получения порта отладки от поставщика порта.

## <a name="notes-for-callers"></a>Заметки для абонентов
 Этот интерфейс передается в [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) для создания порта отладки. Звонок [в GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md) возвращает этот интерфейс, представляющий запрос, используемый для создания порта в первую очередь.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugPortRequest2`.

|Метод|Описание|
|------------|-----------------|
|[GetPortName](../../../extensibility/debugger/reference/idebugportrequest2-getportname.md)|Получает название порта для создания.|

## <a name="remarks"></a>Примечания
 Двигатель отладки обычно не взаимодействует с поставщиком порта и не будет использовать этот интерфейс.

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
- [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)
