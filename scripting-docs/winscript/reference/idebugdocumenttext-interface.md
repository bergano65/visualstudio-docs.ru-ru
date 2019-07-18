---
title: Интерфейс IDebugDocumentText | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentText interface
ms.assetid: 242bad79-9c0a-4a30-879a-9f43db4e022b
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8878e1ce6e9ad05fc94b134a2e71847b67d578d2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63008619"
---
# <a name="idebugdocumenttext-interface"></a>Интерфейс IDebugDocumentText
Предоставляет доступ к исключительно текстовой версии документа отладки. Этот интерфейс использует следующие правила:  
  
- Положениями символов и номера строк, отсчитываемый от нуля.  
  
- Позиций знаков представляют смещения знаков; они не представляют байтов или слов смещения. Для Win32 позиция символа находится смещение Юникода.  
  
  Помимо методов, наследуемых от `IDebugDocument`, `IDebugDocumentText` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDebugDocumentText::GetDocumentAttributes](../../winscript/reference/idebugdocumenttext-getdocumentattributes.md)|Возвращает атрибуты документа.|  
|[IDebugDocumentText::GetSize](../../winscript/reference/idebugdocumenttext-getsize.md)|Возвращает число строк и число символов в документе.|  
|[IDebugDocumentText::GetPositionOfLine](../../winscript/reference/idebugdocumenttext-getpositionofline.md)|Возвращает позицию символа, соответствующего до первого символа строки.|  
|[IDebugDocumentText::GetLineOfPosition](../../winscript/reference/idebugdocumenttext-getlineofposition.md)|Возвращает номер строки и, возможно, смещение знака в строке, соответствующей в данную позицию символа.|  
|[IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)|Извлекает символы и символ атрибуты, связанные с диапазоном позицию символа.|  
|[IDebugDocumentText::GetPositionOfContext](../../winscript/reference/idebugdocumenttext-getpositionofcontext.md)|Возвращает позицию символа диапазон, соответствующий контексту документа.|  
|[IDebugDocumentText::GetContextOfPosition](../../winscript/reference/idebugdocumenttext-getcontextofposition.md)|Создает объект контекста документа, соответствующий диапазону позиции указанного символа.|