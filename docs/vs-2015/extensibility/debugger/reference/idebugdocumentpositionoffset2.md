---
title: IDebugDocumentPositionOffset2 | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugDocumentPositionOffset2 interface
ms.assetid: f1b05db3-50d8-453f-a72f-e68b239236a4
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5bd0a7fb88d1964b0f5fe804527a9890fe69258f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49262305"
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

