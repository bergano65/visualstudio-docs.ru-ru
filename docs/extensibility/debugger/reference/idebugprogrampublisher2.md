---
title: IDebugПрограммаИздатель2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2
helpviewer_keywords:
- IDebugProgramPublisher2 interface
ms.assetid: b1d17f63-7146-4076-a588-034cfc6858b9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b17f5bab02e49951eb1647af95641af807c44863
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721523"
---
# <a name="idebugprogrampublisher2"></a>IDebugProgramPublisher2
Этот интерфейс позволяет отладке двигателя (DE) или пользовательских поставщиков порта для регистрации программ для отладки.

## <a name="syntax"></a>Синтаксис

```
IDebugProgramPublisher2 : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
Visual Studio реализует этот интерфейс для регистрации отладки программ, чтобы сделать их видимыми для отладки в нескольких процессах.

## <a name="notes-for-callers"></a>Заметки для абонентов
Функция COM `CoCreateInstance` с `CLSID_ProgramPublisher` для получения этого интерфейса (см. пример). DE или поставщик пользовательских портов использует этот интерфейс для регистрации узлов программы, представляющих отладудинированные программы.

## <a name="methods-in-vtable-order"></a>Методы в порядке Vtable
Этот интерфейс реализует следующие методы:

|Метод|Описание|
|------------|-----------------|
|[PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)|Делает узло программы доступным для DEs и менеджера отладки сеанса (SDM).|
|[UnpublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogramnode.md)|Удаляет узла программы, чтобы он больше не был доступен.|
|[PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)|Делает программу доступной для DEs и SDM.|
|[UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)|Удаляет программу, чтобы она больше не была доступна.|
|[SetDebuggerPresent](../../../extensibility/debugger/reference/idebugprogrampublisher2-setdebuggerpresent.md)|Устанавливает флаг, указывающий на наличие отладчика.|

## <a name="remarks"></a>Примечания
Этот интерфейс делает программы и узлы программы доступными (т.е. «публикует» их) для использования DEs и диспетчером отладки сеансов (SDM). Чтобы получить доступ к опубликованным программам и узлам программы, используйте интерфейс [IDebugProgramProvider2.](../../../extensibility/debugger/reference/idebugprogramprovider2.md) Это единственный способ Visual Studio распознать, что программа отлажается.

## <a name="requirements"></a>Требования
Заголовок: msdbg.h

Название: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Пример
Этот пример показывает, как мгновенно узла программы и зарегистрировать узла программы. Это взято из учебника, [Публикация узла программы](https://msdn.microsoft.com/library/d0100e02-4e2b-4e72-9e90-f7bc11777bae).

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
