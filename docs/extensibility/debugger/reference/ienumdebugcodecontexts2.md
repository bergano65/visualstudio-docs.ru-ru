---
title: IEnumDebugCodeContexts2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugCodeContexts2
helpviewer_keywords:
- IEnumDebugCodeContexts2
ms.assetid: 72915146-215f-4c99-a034-131b2b474e0e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dae1261adca25162b5bb81cc3ae8b006ce7ef283
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350877"
---
# <a name="ienumdebugcodecontexts2"></a>IEnumDebugCodeContexts2
Этот интерфейс перечисляет контексты кода, связанного с сеанса отладки, или с определенной программой или документа.

## <a name="syntax"></a>Синтаксис

```
IEnumDebugCodeContexts2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Модуль отладки (DE) реализует этот интерфейс для представления списка контекстов кода в определенном текстовом позиции в программе или список контекстов кода для контекста определенного документа.

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
 Вызовите [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) для получения этого интерфейса, представляющий список контекстов кода определенного текста в позиции программы исходного документа.

 Вызовите [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md) для получения этого интерфейса, представляющий список всех контекстов кода в конкретный документ-источник.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IEnumDebugCodeContexts2`.

|Метод|Описание|
|------------|-----------------|
|[Вперед](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)|Извлекает указанное число контекстов кода в последовательности перечисления.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-skip.md)|Пропускает заданное число контекстов кода в последовательности перечисления.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-reset.md)|Сбрасывает последовательность перечислений в начало.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-clone.md)|Создает перечислитель с тем же состоянием перечисления, что и текущий перечислитель.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-getcount.md)|Получает число контекстов кода в перечислителе.|

## <a name="remarks"></a>Примечания
 Visual Studio вызывает [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) для заполнения списка контекстов кода пользователь может выбрать из когда установка следующего оператора или отображение дизассемблированного кода для исходного файла. Несколько контекстов кода может произойти, например, при наличии нескольких экземпляров шаблона стиля C++.

## <a name="requirements"></a>Требования
 Header: msdbg.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Базовые интерфейсы](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)
- [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)