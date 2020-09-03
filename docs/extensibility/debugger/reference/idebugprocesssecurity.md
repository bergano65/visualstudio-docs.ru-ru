---
title: Идебугпроцесссекурити | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity interface
ms.assetid: 8a52ddca-bd99-49c0-9778-469dce7abd44
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 36c81cda3a27cfe1ef0fecfefc9bbb790d4d5217
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80723190"
---
# <a name="idebugprocesssecurity"></a>IDebugProcessSecurity
`IDebugProcessSecurity` реализуется поставщиком порта для предупреждения пользователя о том, что присоединение к процессу является ненадежным.

## <a name="syntax"></a>Синтаксис

```
IDebugProcessSecurity : IUnknown
```

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugProcessSecurity` .

|Метод|Описание|
|------------|-----------------|
|[GetUserName](../../../extensibility/debugger/reference/idebugprocesssecurity-getusername.md)|Возвращает имя пользователя от поставщика порта.|
|[QueryCanSafelyAttach](../../../extensibility/debugger/reference/idebugprocesssecurity-querycansafelyattach.md)|Предупреждает пользователя о том, что присоединение к процессу отладки является ненадежным.|

## <a name="remarks"></a>Remarks
 Реализуйте этот интерфейс, чтобы отобразить предупреждение и разрешить пользователю отменять, если процесс, к которому выполняется присоединение, может считаться небезопасным.

## <a name="requirements"></a>Требования
 Заголовок: мсдбг. h

 Пространство имен: Microsoft. VisualStudio. Debugger. Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также раздел
- [Порты](../../../extensibility/debugger/ports.md)
- [Поставщики портов](../../../extensibility/debugger/port-suppliers.md)
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
