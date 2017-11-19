---
title: "Интерфейс IDebugDocumentText | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugDocumentText interface
ms.assetid: 242bad79-9c0a-4a30-879a-9f43db4e022b
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9522d1075cd796fb69f6abbc42adc2706a817fed
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenttext-interface"></a>Интерфейс IDebugDocumentText
Предоставляет доступ к версии только текст документа отладки. Этот интерфейс использует следующий формат:  
  
-   Номера строк и позиции знака индексируются с нуля.  
  
-   Позиции знака представляют смещения знаков; они не представляют байтов или word смещения. Для Win32 позиции символа имеет смещение Юникода.  
  
 Помимо методов, наследуемых от `IDebugDocument`, `IDebugDocumentText` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDebugDocumentText::GetDocumentAttributes](../../winscript/reference/idebugdocumenttext-getdocumentattributes.md)|Возвращает атрибуты документа.|  
|[IDebugDocumentText::GetSize](../../winscript/reference/idebugdocumenttext-getsize.md)|Возвращает число строк и число символов в документе.|  
|[IDebugDocumentText::GetPositionOfLine](../../winscript/reference/idebugdocumenttext-getpositionofline.md)|Возвращает позицию символа, соответствующего до первого символа строки.|  
|[IDebugDocumentText::GetLineOfPosition](../../winscript/reference/idebugdocumenttext-getlineofposition.md)|Возвращает номер строки и, возможно, смещение символа в строке, соответствующей в указанную позицию символа.|  
|[IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)|Извлекает символы и символ атрибуты, связанные с диапазоном позиции символа.|  
|[IDebugDocumentText::GetPositionOfContext](../../winscript/reference/idebugdocumenttext-getpositionofcontext.md)|Возвращает позицию символа диапазон, соответствующий контексту документа.|  
|[IDebugDocumentText::GetContextOfPosition](../../winscript/reference/idebugdocumenttext-getcontextofposition.md)|Создает объект контекста документа, соответствующий диапазону позиции указанного символа.|