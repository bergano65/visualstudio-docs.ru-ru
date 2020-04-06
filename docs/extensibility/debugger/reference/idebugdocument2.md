---
title: IDebugДокумент2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocument2
helpviewer_keywords:
- IDebugDocument2 interface
ms.assetid: 1bc58426-dbf5-4471-9aad-9d66cd80eef0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4c959c018dd4da0ff088c4fb52c0420de83b4eac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731988"
---
# <a name="idebugdocument2"></a>IDebugDocument2
Этот интерфейс представляет собой исходный документ.

## <a name="syntax"></a>Синтаксис

```
IDebugDocument2 : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]обычно реализует этот интерфейс. Отладка двигателя (DE) также может реализовать этот интерфейс, когда он должен поставить исходный код и источник не существует на диске.  В таких случаях DE будет также реализовывать интерфейсы [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) и [IDebugActivateDocumentEvent2,](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md) а также некоторые дополнительные методы на интерфейсах [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) и [IDebugDocumentPosition2.](../../../extensibility/debugger/reference/idebugdocumentposition2.md)

## <a name="notes-for-callers"></a>Заметки для абонентов
 Методы на `IDebugDocumentContext2` `IDebugDisassemblyStream2`, `IDebugDocumentPosition2`, `IDebugActivateDocumentEvent2` и интерфейсы вернуть этот интерфейс.

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugDocument2`.

|Метод|Описание|
|------------|-----------------|
|[GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)|Получает название документа в одной из нескольких форм.|
|[GetDocumentClassID](../../../extensibility/debugger/reference/idebugdocument2-getdocumentclassid.md)|Получает идентификатор класса документа.|

## <a name="remarks"></a>Примечания
 Этот интерфейс реализуется только тогда, когда DE поставляет исходный код. Например, когда вы отлажаете сценарий на странице HTML, DE поставляет исходный код, потому что источник загружается или генерируется динамически и не существует как дисковый файл. При отладке традиционных языков, таких как СЗ, этот интерфейс не нуждается в реализации.

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)
- [GetDocument](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocument.md)
- [GetDocument](../../../extensibility/debugger/reference/idebugdocumentcontext2-getdocument.md)
- [GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)
- [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)
