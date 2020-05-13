---
title: IEnumDebugCodeКонтекстс2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugCodeContexts2
helpviewer_keywords:
- IEnumDebugCodeContexts2
ms.assetid: 72915146-215f-4c99-a034-131b2b474e0e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6917c44bb3ddc80513e7c45a6aa4ea0207fd46c9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717281"
---
# <a name="ienumdebugcodecontexts2"></a>IEnumDebugCodeContexts2
Этот интерфейс перечисляет контексты кода, связанные с сеансом отладки, или с определенной программой или документом.

## <a name="syntax"></a>Синтаксис

```
IEnumDebugCodeContexts2 : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Движок отладки (DE) реализует этот интерфейс, чтобы представить список контекстов кода для определенной позиции текста в программе, или список контекстов кода для конкретного контекста документа.

## <a name="notes-for-callers"></a>Заметки для абонентов
 Позвоните [EnumCodeContexts,](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) чтобы получить этот интерфейс, представляющий список контекстов кода для определенной позиции текста в исходном документе программы.

 Позвоните [EnumCodeContexts,](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md) чтобы получить этот интерфейс, представляющий список всех контекстов кода в конкретном исходном документе.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IEnumDebugCodeContexts2`.

|Метод|Описание|
|------------|-----------------|
|[Далее](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)|Извлекает определенное количество контекстов кода в последовательности перечисления.|
|[Пропустить](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-skip.md)|Пропускает определенное количество контекстов кода в последовательности перечисления.|
|[Сбросить](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-reset.md)|Сбрасывает последовательность перечислений в начало.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-clone.md) (Клонировать)|Создает регистратор, содержащий то же состояние перечисления, что и текущий регистратор.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-getcount.md)|Получает количество контекстов кода в регистраторе.|

## <a name="remarks"></a>Примечания
 Visual Studio вызывает [EnumCodeContexts,](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) чтобы заполнить список контекстов кода, которые пользователь может выбрать, при настройке следующего оператора или показе разборки исходного файла. Несколько контекстов кода могут возникать, например, при наличии нескольких экземпляров шаблона в стиле С.

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)
- [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)
