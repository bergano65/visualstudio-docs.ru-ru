---
title: IDebugDocumentPositionOffset2 | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentPositionOffset2 interface
ms.assetid: f1b05db3-50d8-453f-a72f-e68b239236a4
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c1f30c3a465d4803e5c91f14ee45ad582e76d986
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58978561"
---
# <a name="idebugdocumentpositionoffset2"></a>IDebugDocumentPositionOffset2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Представляет позицию в файле исходного кода как смещение в буфере символов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugDocumentPositionOffset2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Реализуется интегрированной среды разработки и потребляемых отладчиков.  
  
## <a name="methods"></a>Методы  
 В следующей таблице показаны методы `IDebugDocumentPositionOffset2`.  
  
|Метод|Описание|  
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
