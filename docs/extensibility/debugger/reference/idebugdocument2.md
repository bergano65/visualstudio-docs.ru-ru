---
title: IDebugDocument2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugDocument2
helpviewer_keywords:
- IDebugDocument2 interface
ms.assetid: 1bc58426-dbf5-4471-9aad-9d66cd80eef0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 240efad211f9d5aaee9c9494d545f11dd79e0bce
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53905732"
---
# <a name="idebugdocument2"></a>IDebugDocument2
Этот интерфейс представляет исходный документ.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugDocument2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] обычно реализует этот интерфейс. Отладчик (DE) также можно реализовать этот интерфейс, когда он должен указать исходный код и источник не существует на диске.  В таких случаях также реализовать DE [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) и [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md) интерфейсов, а также некоторые дополнительные методы на [ IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) и [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md) интерфейсов.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 Методы на `IDebugDocumentContext2`, `IDebugDisassemblyStream2`, `IDebugDocumentPosition2`, и `IDebugActivateDocumentEvent2` интерфейсы возвращают этот интерфейс.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugDocument2`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)|Возвращает имя документа в одну из нескольких форм.|  
|[GetDocumentClassID](../../../extensibility/debugger/reference/idebugdocument2-getdocumentclassid.md)|Получает идентификатор класса документа.|  
  
## <a name="remarks"></a>Примечания  
 Этот интерфейс реализуется только в том случае, когда DE предоставляет исходный код. Например, при отладке скрипта в HTML-страницы, DE предоставляет исходный код так, как источник загрузкой и создается динамически и не существует в качестве файла на диске. При отладке традиционных языков, таких как C++, этот интерфейс реализуется не требуется.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugdocumentcontext2-getdocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)