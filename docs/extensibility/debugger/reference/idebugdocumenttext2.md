---
title: "IDebugDocumentText2 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugDocumentText2
helpviewer_keywords: IDebugDocumentText2 interface
ms.assetid: e85f50a3-211c-4220-a9f4-789950ba2782
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ebcb90f570ad29f38eabe8712928b484fd6961c0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idebugdocumenttext2"></a>IDebugDocumentText2
Этот интерфейс представляет текстовый документ.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugDocumentText2 : IDebugDocument2  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Отладчик (DE) реализует этот интерфейс, когда исходного кода, его необходимо указать в виде текста. Так как это наиболее типичный случай, если реализует DE [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) интерфейс, он также должен реализовать `IDebugDocumentText2` интерфейса.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Используйте `QueryInterface` метод, чтобы получить этот интерфейс из `IDebugDocument2` интерфейса.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В дополнение к методам на `IDebugDocument2` интерфейс, этот интерфейс реализует следующие методы:  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetSize](../../../extensibility/debugger/reference/idebugdocumenttext2-getsize.md)|Получает размер текста в этой позиции в документе.|  
|[GetText](../../../extensibility/debugger/reference/idebugdocumenttext2-gettext.md)|Получение текста из указанной позиции в документе.|  
  
## <a name="remarks"></a>Примечания  
 Объект, реализующий этот интерфейс также должен реализовывать <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> интерфейс предоставляет <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> интерфейс для [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md) объекта.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)   
 [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)