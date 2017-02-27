---
title: "IEnumDebugCodeContexts2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugCodeContexts2"
helpviewer_keywords: 
  - "IEnumDebugCodeContexts2"
ms.assetid: 72915146-215f-4c99-a034-131b2b474e0e
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IEnumDebugCodeContexts2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот интерфейс перечисляет контексты кода, связанные с сеансом отладки или с указанными приложениями или документом.  
  
## Синтаксис  
  
```  
IEnumDebugCodeContexts2 : IUnknown  
```  
  
## Примечания по реализации  
 Отладчик \(DE\) реализует этот интерфейс, чтобы представлять список контекстов кода для указанной позиции текста в программе или список контекстов кода для контекста заданного документа.  
  
## Замечания для вызывающих объектов  
 Вызов [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) получить этот интерфейс, представляющий список контекстов кода для определенной позиции текста в исходном документе программы.  
  
 Вызов [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md) получить этот интерфейс, представляющий список всех контекстов кода в указанном исходном документе.  
  
## Методы в том порядке Vtable  
 В следующей таблице показаны методы `IEnumDebugCodeContexts2`.  
  
|Метод|Описание|  
|-----------|--------------|  
|[Далее](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)|Получает заданное число контекстов кода в последовательности перечисления.|  
|[Пропустить](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-skip.md)|Пропустить указанное количество контекстов кода в последовательности перечисления.|  
|[Сбросить](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-reset.md)|Сбросить последовательность перечисления в начало.|  
|[Клонировать](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-clone.md)|Создает перечислитель с тем же состоянием перечисления, что и текущий перечислитель.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-getcount.md)|Получает число контекстов кода в перечислителе.|  
  
## Заметки  
 Вызовы Visual Studio [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) заполнить список контекстов кода пользователь может выбрать параметр из следующей выписку или отображения разборку для исходного файла.  Нескольких контекстах кода могут произойти, например, если несколько экземпляров шаблона языка c. \+\+\-style.  
  
## Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)   
 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)