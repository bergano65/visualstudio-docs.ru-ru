---
title: "IDebugDisassemblyStream2::Seek | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugDisassemblyStream2::Seek
helpviewer_keywords: IDebugDisassemblyStream2::Seek
ms.assetid: afec3008-b1e0-4803-ad24-195dbfb6497e
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 61ef1e649a80fcda5ec3ce4be6c74b154c17f9a4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idebugdisassemblystream2seek"></a>IDebugDisassemblyStream2::Seek
Перемещает указатель чтения в потоке Дизассемблирование заданное количество инструкции относительно указанной позиции.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT Seek(   
   SEEK_START          dwSeekStart,  
   IDebugCodeContext2* pCodeContext,  
   UINT64              uCodeLocationId,  
   INT64               iInstructions  
);  
```  
  
```csharp  
int Seek(   
   enum_SEEK_START    dwSeekStart,  
   IDebugCodeContext2 pCodeContext,  
   ulong              uCodeLocationId,  
   long               iInstructions  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dwSeekStart`  
 [in] Значение из [SEEK_START](../../../extensibility/debugger/reference/seek-start.md) перечисление, указывающее относительное положение, чтобы начать процесс поиска.  
  
 `pCodeContext`  
 [in] [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) объект, представляющий контекст кода, относительно операции поиска. Этот параметр используется только в том случае, если `dwSeekStart`  =  `SEEK_START_CODECONTEXT`; в противном случае этот параметр игнорируется и может иметь значение null.  
  
 `uCodeLocationId`  
 [in] Идентификатор расположение кода, относительно операции поиска. Этот параметр используется в том случае, если `dwSeekStart`  =  `SEEK_START_CODELOCID`; в противном случае этот параметр игнорируется и может быть равным 0. В разделе «Примечания» [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md) метод описание идентификатора расположение в коде.  
  
 `iInstructions`  
 [in] Количество инструкций для перемещения относительно позиции, указанной в `dwSeekStart`. Это значение может быть отрицательным для перемещения в обратном направлении.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` в точку за пределами списка доступных инструкций если позиции поиска. В противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Если поиска было позиция в начале списка, положение чтения присваивается первой инструкции в списке. Если см. в позицию после окончания списка, положение чтения имеет значение последней инструкции в списке.  
  
## <a name="see-also"></a>См. также  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [SEEK_START](../../../extensibility/debugger/reference/seek-start.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)