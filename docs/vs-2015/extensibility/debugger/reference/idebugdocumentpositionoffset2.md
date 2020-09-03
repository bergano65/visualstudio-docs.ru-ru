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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200217"
---
# <a name="idebugdocumentpositionoffset2"></a>IDebugDocumentPositionOffset2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Представляет расположение в исходном файле как смещение символа.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugDocumentPositionOffset2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Реализуется интегрированной средой разработки и используется механизмами отладки.  
  
## <a name="methods"></a>Методы  
 В следующей таблице показаны методы `IDebugDocumentPositionOffset2` .  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2-getrange.md)|Извлекает диапазон для текущего расположения документа.|  
  
## <a name="remarks"></a>Remarks  
 При этом возвращаются те же сведения [, что](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md) и в методе «та», но в `char` смещении от начала документа. Таким образом, документ будет выглядеть так, как если бы он существовал на диске, то есть в одномерном массиве символов вместо сведений о строках и столбцах, которые обычно возвращаются.  
  
## <a name="requirements"></a>Требования  
 Заголовок: Мсдбг. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также:  
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
