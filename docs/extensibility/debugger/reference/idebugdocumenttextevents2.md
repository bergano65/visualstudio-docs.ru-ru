---
title: "IDebugDocumentTextEvents2 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugDocumentTextEvents2
helpviewer_keywords:
- IDebugDocumentTextEvents2 interface
ms.assetid: a10cbb6b-11a8-4056-b42a-2ecebf0e690d
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 242c15cc456c3a27ba7b7da45a11031b026c02d3
ms.lasthandoff: 04/05/2017

---
# <a name="idebugdocumenttextevents2"></a>IDebugDocumentTextEvents2
Этот интерфейс используется для уведомления об изменениях в исходном документе, поставляемые модуль отладки Visual Studio.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugDocumentTextEvents2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 DE реализует этот интерфейс для поддержки внесения изменений в исходный код. Обычно этот интерфейс реализуется на тот же объект, реализующий [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) интерфейса.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]Получает этого интерфейса через вызов <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A>метод.</xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint>Интерфейс получается из вызова <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.EnumConnectionPoints%2A>метод.</xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.EnumConnectionPoints%2A> </xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer>Интерфейс получается путем вызова метода [QueryInterface](/cpp/atl/queryinterface) метод [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) интерфейса.</xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer>  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugDocumentTextEvents2`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[onDestroy](../../../extensibility/debugger/reference/idebugdocumenttextevents2-ondestroy.md)|Указывает, что весь документ был удален.|  
|[onInsertText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-oninserttext.md)|Уведомляет отладочный пакет вставки текста в документ.|  
|[onRemoveText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onremovetext.md)|Уведомляет отладочный пакет о том, что текст был удален из документа.|  
|[onReplaceText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onreplacetext.md)|Уведомляет отладочный пакет замены, текст в документе.|  
|[onUpdateTextAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatetextattributes.md)|Уведомляет отладочный пакет об обновлении атрибуты текста в документе.|  
|[onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)|Уведомляет приемника события, что атрибуты были обновлены.|  
  
## <a name="remarks"></a>Примечания  
 Только модули отладки, которые поставляют своих собственных документов может воспользоваться преимуществами `IDebugDocumentTextEvent2` интерфейса. Примером будет модуля отладки скрипта. В процессе интерпретации скриптов, новый исходный код может быть создан, не присутствует в любом файле диска и известен только DE.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)   
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
