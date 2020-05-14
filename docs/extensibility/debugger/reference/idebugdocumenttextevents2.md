---
title: IDebugДокументТекстСобытия2 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentTextEvents2
helpviewer_keywords:
- IDebugDocumentTextEvents2 interface
ms.assetid: a10cbb6b-11a8-4056-b42a-2ecebf0e690d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 44a1736890ac78e7aaf20b4a639b1794fc63b5ac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731362"
---
# <a name="idebugdocumenttextevents2"></a>IDebugDocumentTextEvents2
Этот интерфейс используется для уведомления Visual Studio об изменениях в исходном документе, поставляемом движком отладки.

## <a name="syntax"></a>Синтаксис

```
IDebugDocumentTextEvents2 : IUnknown
```

## <a name="notes-for-implementers"></a>Заметки для исполнителей
 DE реализует этот интерфейс для поддержки внесения изменений в исходный код. Этот интерфейс обычно реализуется на том же объекте, который реализует интерфейс [IDebugDocument2.](../../../extensibility/debugger/reference/idebugdocument2.md)

## <a name="notes-for-callers"></a>Заметки для абонентов
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]получает этот интерфейс через вызов <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> к методу. Интерфейс <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> получен от вызова к <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.EnumConnectionPoints%2A> методу. Интерфейс <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> получен путем вызова метода [queryInterface](/cpp/atl/queryinterface) на интерфейсе [IDebugDocument2.](../../../extensibility/debugger/reference/idebugdocument2.md)

## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable
 В следующей таблице показаны методы `IDebugDocumentTextEvents2`.

|Метод|Описание|
|------------|-----------------|
|[onDestroy](../../../extensibility/debugger/reference/idebugdocumenttextevents2-ondestroy.md)|Означает, что весь документ был уничтожен.|
|[onInsertText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-oninserttext.md)|Уведомляет пакет отладки, который был вставлен в документ.|
|[onRemoveText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onremovetext.md)|Уведомляет пакет отладки, что текст был удален из документа.|
|[onReplaceText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onreplacetext.md)|Уведомляет пакет отладки, который был заменен в документе.|
|[onUpdateTextAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatetextattributes.md)|Уведомляет пакет отладки, что атрибуты текста были обновлены в документе.|
|[onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)|Уведомляет получателя события об обновлении атрибутов документа.|

## <a name="remarks"></a>Примечания
 Только отладить двигатели, которые поставляют `IDebugDocumentTextEvent2` свои собственные документы будут воспользоваться интерфейсом. Примером этого может быть движок отладки сценариев. В процессе интерпретации скриптов может быть сгенерирован новый исходный код, который не присутствует ни в одном дисковом файле и известен только DE.

## <a name="requirements"></a>Требования
 Заголовок: msdbg.h

 Название: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
