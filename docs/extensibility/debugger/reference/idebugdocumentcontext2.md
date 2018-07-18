---
title: IDebugDocumentContext2 | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDocumentContext2
helpviewer_keywords:
- IDebugDocumentContext2
ms.assetid: 2a446c71-8100-4c09-a1cc-fd446bd74030
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 06ff06086c0f293f70af7d9570cf72df4be85608
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31107703"
---
# <a name="idebugdocumentcontext2"></a>IDebugDocumentContext2
Этот интерфейс представляет позицию в файл исходного документа.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugDocumentContext2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Модуль отладки (DE) реализует этот интерфейс в рамках поддержки уровня отладку исходного кода. Наряду с позиции в исходном коде этот интерфейс предоставляет методы для сравнения контексты и навигация по документа с исходным кодом.  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 Методы на нескольких интерфейсов, чаще всего [GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) и [GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) интерфейсы, возвращают этот интерфейс.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugDocumentContext2`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetDocument](../../../extensibility/debugger/reference/idebugdocumentcontext2-getdocument.md)|Получает документ, содержащий контекст этого документа.|  
|[GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)|Возвращает отображаемое имя документа, который содержит контекст этого документа.|  
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)|Получает список всех контекстов код, связанный с данным контекстом документа.|  
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugdocumentcontext2-getlanguageinfo.md)|Возвращает язык, связанный с данным контекстом документа.|  
|[GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|Возвращает оператор диапазона файла этого документа контекста.|  
|[GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)|Возвращает диапазон исходного файла этого документа контекста.|  
|[Compare](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)|Сравнивает этот контекст документа документ контекстов в указанный массив.|  
|[Поиск](../../../extensibility/debugger/reference/idebugdocumentcontext2-seek.md)|Перемещает контекст документа, заданное количество операторов или строк.|  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)   
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocumentcontext.md)   
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)   
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)