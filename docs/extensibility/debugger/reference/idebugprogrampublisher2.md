---
title: IDebugProgramPublisher2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2
helpviewer_keywords:
- IDebugProgramPublisher2 interface
ms.assetid: b1d17f63-7146-4076-a588-034cfc6858b9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f94e7ea830a49db5b95bae3d0d6c50f73e6d3d64
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66343140"
---
# <a name="idebugprogrampublisher2"></a>IDebugProgramPublisher2
Этот интерфейс обеспечивает связь модуля отладки (DE) или поставщики настраиваемый порт для регистрации программы для отладки.

## <a name="syntax"></a>Синтаксис

```
IDebugProgramPublisher2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
Visual Studio реализует этот интерфейс для регистрации, чтобы сделать их видимыми для отладки в нескольких процессах отлаживаемых программ.

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
Вызов COM `CoCreateInstance` функционировать с `CLSID_ProgramPublisher` для получения этого интерфейса (см. пример). DE или пользовательский порт поставщик использует этот интерфейс для регистрации программы узлов, представляющих отлаживаемых программ.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
Этот интерфейс реализует следующие методы:

|Метод|Описание|
|------------|-----------------|
|[PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)|Предоставляет узел программы DEs и сеанс отладки manager (SDM).|
|[UnpublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogramnode.md)|Удаляет узел программы, чтобы он больше не доступен.|
|[PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)|Предоставляет программу DEs и SDM.|
|[UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)|Удаление программы, чтобы он больше не доступен.|
|[SetDebuggerPresent](../../../extensibility/debugger/reference/idebugprogrampublisher2-setdebuggerpresent.md)|Задает флаг, указывающий, что отладчик присутствует.|

## <a name="remarks"></a>Примечания
Этот интерфейс предоставляет эти программы и программы узлы (т. е «опубликовать» их) для использования DEs и диспетчер отладки сеансов (SDM). Для доступа к опубликованных программ и узлы программы, используйте [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) интерфейс. Это единственный способ Visual Studio может распознать, что программа отлаживается.

## <a name="requirements"></a>Требования
Header: msdbg.h

Пространство имен: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Пример
В этом примере показано, как создать экземпляр издателя программы и зарегистрировать узел программы. Метаданные берутся из учебника, [публикации узла программы](https://msdn.microsoft.com/library/d0100e02-4e2b-4e72-9e90-f7bc11777bae).

```cpp
// This is how m_srpProgramPublisher is defined in the class definition:
// CComPtr<IDebugProgramPublisher2> m_srpProgramPublisher.

void CProgram::Start(IDebugEngine2 * pEngine)
{
    m_spEngine = pEngine;

    HRESULT hr = m_srpProgramPublisher.CoCreateInstance(CLSID_ProgramPublisher);
    if ( FAILED(hr) )
    {
        ATLTRACE("Failed to create the program publisher: 0x%x.", hr);
        return;
    }

    // Register ourselves with the program publisher. Note that
    // CProgram implements the IDebgProgramNode2 interface, hence
    // the static cast on "this".
    hr = m_srpProgramPublisher->PublishProgramNode(
        static_cast<IDebugProgramNode2*>(this));
    if ( FAILED(hr) )
    {
        ATLTRACE("Failed to publish the program node: 0x%x.", hr);
        m_srpProgramPublisher.Release();
        return;
    }

    ATLTRACE("Added program node.\n");
}
```

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
