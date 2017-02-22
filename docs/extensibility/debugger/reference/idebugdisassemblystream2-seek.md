---
title: "IDebugDisassemblyStream2::Seek | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDisassemblyStream2::Seek"
helpviewer_keywords: 
  - "IDebugDisassemblyStream2::Seek"
ms.assetid: afec3008-b1e0-4803-ad24-195dbfb6497e
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugDisassemblyStream2::Seek
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Перемещает указатель чтения в потоке дизассемблирования заданное число инструкций по отношению к указанной позиции.  
  
## Синтаксис  
  
```cpp#  
HRESULT Seek(   
   SEEK_START          dwSeekStart,  
   IDebugCodeContext2* pCodeContext,  
   UINT64              uCodeLocationId,  
   INT64               iInstructions  
);  
```  
  
```c#  
int Seek(   
   enum_SEEK_START    dwSeekStart,  
   IDebugCodeContext2 pCodeContext,  
   ulong              uCodeLocationId,  
   long               iInstructions  
);  
```  
  
#### Параметры  
 `dwSeekStart`  
 \[in\] значение из [SEEK\_START](../../../extensibility/debugger/reference/seek-start.md) перечисление, указывающее относительное положение начать процесс поиска.  
  
 `pCodeContext`  
 \[in\] IDebugCodeContext2 объект, представляющий контекст кода, что операция поиска по отношению к.  Этот параметр используется, только если `dwSeekStart` \=  `SEEK_START_CODECONTEXT`; в противном случае этот параметр пропускается и может принимать значение NULL.  
  
 `uCodeLocationId`  
 \[in\] идентификатор расположение кода, что операция поиска по отношению к.  Этот параметр используется, если `dwSeekStart` \=  `SEEK_START_CODELOCID`; в противном случае этот параметр пропускается и может иметь значение 0.  См. раздел " примечания ", [GetCodeLocationId](../Topic/IDebugDisassemblyStream2::GetCodeLocationId.md) метод описание идентификатора расположение кода.  
  
 `iInstructions`  
 \[in\] число инструкций переместить относительно позиции, заданной в `dwSeekStart`.  Это значение может быть отрицательным перемещается назад.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`.  Возвращает `S_FALSE` если положение поиска было до точки за списком доступных инструкций.  В противном случае возвращает код ошибки.  
  
## Заметки  
 Если поиск был в позицию, прежде чем начало списка позиция чтения присваивается первой инструкции в списке.  Если элемент был в позицию после конца списка, позиция чтения имеет значение последней инструкции в списке.  
  
## См. также  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [SEEK\_START](../../../extensibility/debugger/reference/seek-start.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [GetCodeLocationId](../Topic/IDebugDisassemblyStream2::GetCodeLocationId.md)