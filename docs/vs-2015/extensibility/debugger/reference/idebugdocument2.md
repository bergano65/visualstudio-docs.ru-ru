---
title: IDebugDocument2 | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugDocument2
helpviewer_keywords:
- IDebugDocument2 interface
ms.assetid: 1bc58426-dbf5-4471-9aad-9d66cd80eef0
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d840039f6ec9c4dce16e8efe9d6dbb2d91cad5d8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47571699"
---
# <a name="idebugdocument2"></a>IDebugDocument2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugDocument2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugdocument2).  
  
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
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugdocumentcontext2-getdocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)

