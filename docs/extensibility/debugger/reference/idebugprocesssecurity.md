---
title: IDebugProcessSecurity | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity interface
ms.assetid: 8a52ddca-bd99-49c0-9778-469dce7abd44
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 12c1cc5af90fa0ff337a105f6d3d7232b72ab6ac
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56695236"
---
# <a name="idebugprocesssecurity"></a>IDebugProcessSecurity
`IDebugProcessSecurity` реализуется, чтобы предупредить пользователя, что присоединение к процессу небезопасна поставщика порта.

## <a name="syntax"></a>Синтаксис

```
IDebugProcessSecurity : IUnknown
```

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugProcessSecurity`.

|Метод|Описание:|
|------------|-----------------|
|[GetUserName](../../../extensibility/debugger/reference/idebugprocesssecurity-getusername.md)|Возвращает имя пользователя от поставщика порта.|
|[QueryCanSafelyAttach](../../../extensibility/debugger/reference/idebugprocesssecurity-querycansafelyattach.md)|Предупреждает пользователя о небезопасна, присоединение к процессу отладки.|

## <a name="remarks"></a>Примечания
 Реализация этого интерфейса позволяет показать предупреждение и разрешить пользователю отменить, если процесс, к которому вы присоединяете может рассматриваться как небезопасные.

## <a name="requirements"></a>Требования
 Header: msdbg.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Порты](../../../extensibility/debugger/ports.md)
- [Поставщики портов](../../../extensibility/debugger/port-suppliers.md)
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)