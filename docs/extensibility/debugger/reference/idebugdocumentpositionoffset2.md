---
title: IDebugDocumentPositionOffset2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugDocumentPositionOffset2 interface
ms.assetid: f1b05db3-50d8-453f-a72f-e68b239236a4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: eeedd1038b577be8a0e0cac46359cf0b05f0dc70
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53948291"
---
# <a name="idebugdocumentpositionoffset2"></a>IDebugDocumentPositionOffset2
Представляет позицию в файле исходного кода как смещение в буфере символов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugDocumentPositionOffset2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Реализуется интегрированной среды разработки и потребляемых отладчиков.  
  
## <a name="methods"></a>Методы  
 В следующей таблице показаны методы `IDebugDocumentPositionOffset2`.  
  
|Метод|Описание:|  
|------------|-----------------|  
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2-getrange.md)|Извлекает диапазон для текущей позиции документа.|  
  
## <a name="remarks"></a>Примечания  
 Возвращает те же сведения, что [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md) в `char` смещений от начала документа. Это представляет документ, как он будет существовать на диске, то есть в одномерный массив символов, а не сведения строки и столбца, который обычно возвращается.  
  
## <a name="requirements"></a>Требования  
 Заголовок: Msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)