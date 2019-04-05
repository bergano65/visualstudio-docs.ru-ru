---
title: IDebugDocumentTextEvents2 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDocumentTextEvents2
helpviewer_keywords:
- IDebugDocumentTextEvents2 interface
ms.assetid: a10cbb6b-11a8-4056-b42a-2ecebf0e690d
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: dca9d3c8de956faf2dab5c9090c9963a7c9fbea0
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58991133"
---
# <a name="idebugdocumenttextevents2"></a>IDebugDocumentTextEvents2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот интерфейс используется для уведомления об изменениях в исходном документе, предоставляемые ядром отладки Visual Studio.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugDocumentTextEvents2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 DE реализует этот интерфейс для поддержки внесение изменений в исходный код. Этот интерфейс обычно реализуется на тот же объект, реализующий [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) интерфейс.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Получает этот интерфейс, посредством вызова <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> метод. <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> Интерфейс получается из вызова <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.EnumConnectionPoints%2A> метод. <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> Интерфейс получается путем вызова [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) метод [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) интерфейс.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugDocumentTextEvents2`.  
  
|Метод|Описание|  
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
