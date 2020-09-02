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
ms.openlocfilehash: b574ae45dafed11ed28047859676524054951512
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65678969"
---
# <a name="idebugdocumenttextevents2"></a>IDebugDocumentTextEvents2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот интерфейс используется для уведомления Visual Studio об изменениях в исходном документе, предоставляемых модулем отладки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugDocumentTextEvents2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Метод DE реализует этот интерфейс для поддержки внесения изменений в исходный код. Этот интерфейс обычно реализуется для того же объекта, который реализует интерфейс [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) .  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Получает этот интерфейс посредством вызова <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> метода. <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint>Интерфейс получается из вызова <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.EnumConnectionPoints%2A> метода. <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer>Интерфейс получается путем вызова метода [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) в интерфейсе [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) .  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugDocumentTextEvents2` .  
  
|Метод|Описание|  
|------------|-----------------|  
|[onDestroy](../../../extensibility/debugger/reference/idebugdocumenttextevents2-ondestroy.md)|Указывает, что весь документ был уничтожен.|  
|[onInsertText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-oninserttext.md)|Уведомляет пакет отладки, что текст вставлен в документ.|  
|[onRemoveText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onremovetext.md)|Уведомляет пакет отладки, что текст был удален из документа.|  
|[onReplaceText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onreplacetext.md)|Уведомляет пакет отладки, что текст был заменен в документе.|  
|[onUpdateTextAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatetextattributes.md)|Уведомляет пакет отладки, что в документе были обновлены текстовые атрибуты.|  
|[onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)|Уведомляет получателя о том, что атрибуты документа были обновлены.|  
  
## <a name="remarks"></a>Remarks  
 Только модули отладки, которые предоставляют собственные документы, используют `IDebugDocumentTextEvent2` интерфейс. Примером этого может быть Подсистема отладки сценариев. В процессе интерпретации скриптов можно создать новый исходный код, который отсутствует в любом файле диска и известен только параметру DE.  
  
## <a name="requirements"></a>Требования  
 Заголовок: мсдбг. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также:  
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)   
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
