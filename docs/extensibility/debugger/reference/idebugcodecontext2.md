---
title: IDebugCodeКонтекст2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2
helpviewer_keywords:
- IDebugCodeContext2 interface
ms.assetid: 3670439e-2171-405d-9d77-dedb0f1cba93
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 778602cc29049d855c418fd8fa416feb1ad8e9fe
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734210"
---
# <a name="idebugcodecontext2"></a>IDebugCodeContext2
Этот интерфейс представляет собой исходное положение инструкции кода. Для большинства архитектур времени выполнения сегодня контекст кода можно рассматривать как адрес в потоке выполнения программы.

## <a name="syntax"></a>Синтаксис

```
IDebugCodeContext2 : IDebugMemoryContext2
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Отладка двигателя реализует этот интерфейс, чтобы связать положение инструкции кода с позицией документа.

## <a name="notes-for-callers"></a>Заметки для абонентов
 Методы на многих интерфейсах возвращают этот интерфейс, как правило, [GetCodeContext.](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md) Он также широко используется с интерфейсом [IDebugDisassemblyStream2,](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) а также в информации о разрешении моментов разрыва.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В дополнение к методам на интерфейсе [IDebugMemoryContext2,](../../../extensibility/debugger/reference/idebugmemorycontext2.md) этот интерфейс реализует следующие методы:

|Метод|Описание|
|------------|-----------------|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)|Получает контекст документа, соответствующий контексту активного кода.|
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugcodecontext2-getlanguageinfo.md)|Получает языковую информацию для этого контекста кода.|

## <a name="remarks"></a>Примечания
 Ключевое различие `IDebugCodeContext2` между интерфейсом и интерфейсом [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) заключается в том, что он `IDebugCodeContext2` всегда выровнен. Это означает, `IDebugCodeContext2` что an всегда указывает на начало `IDebugMemoryContext2` инструкции, в то время как может указывать на любой байт памяти в архитектуре времени выполнения. `IDebugCodeContext2`приращена инструкциями, а не базовым размером хранилища (обычно байт).

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)
- [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)
- [Далее](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
