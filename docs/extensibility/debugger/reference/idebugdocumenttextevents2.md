---
title: IDebugDocumentTextEvents2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugDocumentTextEvents2
helpviewer_keywords:
- IDebugDocumentTextEvents2 interface
ms.assetid: a10cbb6b-11a8-4056-b42a-2ecebf0e690d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 816bd32d8583bd235ddff13d00b63e77e1ae2d4f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54942952"
---
# <a name="idebugdocumenttextevents2"></a>IDebugDocumentTextEvents2
Этот интерфейс используется для уведомления об изменениях в исходном документе, предоставляемые ядром отладки Visual Studio.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugDocumentTextEvents2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 DE реализует этот интерфейс для поддержки внесение изменений в исходный код. Этот интерфейс обычно реализуется на тот же объект, реализующий [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) интерфейс.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Получает этот интерфейс, посредством вызова <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> метод. <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> Интерфейс получается из вызова <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.EnumConnectionPoints%2A> метод. <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> Интерфейс получается путем вызова [QueryInterface](/cpp/atl/queryinterface) метод [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) интерфейс.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugDocumentTextEvents2`.  
  
|Метод|Описание:|  
|------------|-----------------|  
|[onDestroy](../../../extensibility/debugger/reference/idebugdocumenttextevents2-ondestroy.md)|Указывает, что весь документ был удален.|  
|[onInsertText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-oninserttext.md)|Уведомляет отладочный пакет о том, что текст была введена в документ.|  
|[onRemoveText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onremovetext.md)|Уведомляет отладочный пакет о том, что текст был удален из документа.|  
|[onReplaceText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onreplacetext.md)|Уведомляет отладочный пакет о том, что текст был заменен в документе.|  
|[onUpdateTextAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatetextattributes.md)|Уведомляет отладочный пакет об обновлении атрибуты текста в документе.|  
|[onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)|Уведомляет получатель события о том, что атрибуты документа были обновлены.|  
  
## <a name="remarks"></a>Примечания  
 Только для обработчиков отладки, которые предоставляют свои собственные документы могли бы воспользоваться преимуществами `IDebugDocumentTextEvent2` интерфейс. Примером этого бы обработчик сценариев отладки. В процессе интерпретации скриптов, новый исходный код можно создать, не присутствует в любом файле диска и известен только DE.  
  
## <a name="requirements"></a>Требования  
 Header: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)   
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)