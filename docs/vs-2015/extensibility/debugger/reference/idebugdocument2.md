---
title: IDebugDocument2 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDocument2
helpviewer_keywords:
- IDebugDocument2 interface
ms.assetid: 1bc58426-dbf5-4471-9aad-9d66cd80eef0
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2cd6afb417de4d8a362916f91593d0d0e67d307c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58981054"
---
# <a name="idebugdocument2"></a>IDebugDocument2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот интерфейс представляет исходный документ.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugDocument2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] обычно реализует этот интерфейс. Отладчик (DE) также можно реализовать этот интерфейс, когда он должен указать исходный код и источник не существует на диске.  В таких случаях также реализовать DE [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) и [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md) интерфейсов, а также некоторые дополнительные методы на [ IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) и [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md) интерфейсов.  
  
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
 Header: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugdocumentcontext2-getdocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)
