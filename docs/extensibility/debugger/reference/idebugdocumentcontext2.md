---
title: IDebugДокументальныйконтекст2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2
helpviewer_keywords:
- IDebugDocumentContext2
ms.assetid: 2a446c71-8100-4c09-a1cc-fd446bd74030
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2d31a78412a1a6b20518b6f38ba76b7964cbdbe3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731733"
---
# <a name="idebugdocumentcontext2"></a>IDebugDocumentContext2
Этот интерфейс представляет собой позицию в исходном файле документа.

## <a name="syntax"></a>Синтаксис

```
IDebugDocumentContext2 : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 Движок отладки (DE) реализует этот интерфейс как часть своей поддержки отладки уровня исходного кода. В дополнение к позиции в исходном коде, этот интерфейс поставляет методы для сравнения контекстов и навигации по исходному коду документа.

## <a name="notes-for-callers"></a>Заметки для абонентов
 Методы на нескольких интерфейсах, чаще всего [интерфейсы GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) и [GetDocumentContext,](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) возвращают этот интерфейс.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugDocumentContext2`.

|Метод|Описание|
|------------|-----------------|
|[GetDocument](../../../extensibility/debugger/reference/idebugdocumentcontext2-getdocument.md)|Получает документ, содержащий контекст этого документа.|
|[GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)|Получает отображаемое имя документа, содержащего контекст этого документа.|
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)|Извлекает список всех контекстов кода, связанных с этим контекстом документа.|
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugdocumentcontext2-getlanguageinfo.md)|Получает язык, связанный с контекстом этого документа.|
|[GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|Получает диапазон файлового заявления в контексте этого документа.|
|[GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)|Получает диапазон исходного кода файла в контексте этого документа.|
|[Сравнить](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)|Сравнивает контекст этого документа с данным массивом контекстов документов.|
|[Seek](../../../extensibility/debugger/reference/idebugdocumentcontext2-seek.md)|Перемещает контекст документа по определенному числу заявлений или строк.|

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocumentcontext.md)
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)
- [GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)
