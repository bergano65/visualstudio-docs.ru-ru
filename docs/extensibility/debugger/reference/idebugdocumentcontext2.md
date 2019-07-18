---
title: IDebugDocumentContext2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2
helpviewer_keywords:
- IDebugDocumentContext2
ms.assetid: 2a446c71-8100-4c09-a1cc-fd446bd74030
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fe54a6d3e97fc40f915c42c4aa5397165416b073
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66326643"
---
# <a name="idebugdocumentcontext2"></a>IDebugDocumentContext2
Этот интерфейс представляет позицию в документе исходного файла.

## <a name="syntax"></a>Синтаксис

```
IDebugDocumentContext2 : IUnknown
```

## <a name="notes-for-implementers"></a>Примечания для разработчиков
 Модуль отладки (DE) реализует этот интерфейс как часть его поддержка уровня отладку исходного кода. В дополнение к позиции в исходном коде этот интерфейс предоставляет методы для сравнения контекстов и навигация по документа с исходным кодом.

## <a name="notes-for-callers"></a>Заметки о вызывающих объектов
 Методы на нескольких интерфейсов, чаще всего [GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) и [GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) интерфейсы, возвращают этот интерфейс.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugDocumentContext2`.

|Метод|Описание|
|------------|-----------------|
|[GetDocument](../../../extensibility/debugger/reference/idebugdocumentcontext2-getdocument.md)|Возвращает документ, который содержит контекст этого документа.|
|[GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)|Возвращает отображаемое имя документа, который содержит контекст этого документа.|
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)|Возвращает список всех контекстов кода, связанный с данным контекстом документа.|
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugdocumentcontext2-getlanguageinfo.md)|Возвращает язык, связанный с данным контекстом документа.|
|[GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|Получает диапазон инструкции файл этого контекста документа.|
|[GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)|Получает диапазон исходного файла этого контекста документа.|
|[Compare](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)|Сравнивает этот контекст документа, в указанный массив контекстов документа.|
|[Seek](../../../extensibility/debugger/reference/idebugdocumentcontext2-seek.md)|Перемещает контекст документа, заданное число операторов или строк.|

## <a name="requirements"></a>Требования
 Header: msdbg.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocumentcontext.md)
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)