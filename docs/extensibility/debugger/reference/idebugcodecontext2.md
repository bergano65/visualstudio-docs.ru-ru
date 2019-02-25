---
title: IDebugCodeContext2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2
helpviewer_keywords:
- IDebugCodeContext2 interface
ms.assetid: 3670439e-2171-405d-9d77-dedb0f1cba93
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4e15692a94e3f1c80d6bd6f12ecb0c2ce7271c8d
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56692610"
---
# <a name="idebugcodecontext2"></a>IDebugCodeContext2
Этот интерфейс представляет начальную позицию инструкции кода. Для большинства архитектур во время выполнения в настоящее время контекст кода может рассматриваться как адрес в поток выполнения программы.

## <a name="syntax"></a>Синтаксис

```
IDebugCodeContext2 : IDebugMemoryContext2
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Модуль отладки реализует этот интерфейс для связи позицию инструкции кода в место документа.

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
 Методы на многих интерфейсов возвращают этот интерфейс, чаще всего [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md). Он также используется широко с [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) интерфейсе также как сведения о разрешении точки останова.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В дополнение к методам на [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) интерфейс, этот интерфейс реализует следующие методы:

|Метод|Описание:|
|------------|-----------------|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)|Получает контекст документа, соответствующий контекст active кода.|
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugcodecontext2-getlanguageinfo.md)|Получает сведения о языке для этого контекста кода.|

## <a name="remarks"></a>Примечания
 Основное различие между `IDebugCodeContext2` интерфейс и [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) интерфейс является то, что `IDebugCodeContext2` всегда по краю инструкции. Это означает, что `IDebugCodeContext2` всегда указывает на начало инструкции, тогда как `IDebugMemoryContext2` может указывать на любой байт памяти в архитектуре во время выполнения. `IDebugCodeContext2` увеличивается по инструкции, а не по размеру основное хранилище (обычно в байтах).

## <a name="requirements"></a>Требования
 Header: msdbg.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)
- [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)
- [Вперед](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)