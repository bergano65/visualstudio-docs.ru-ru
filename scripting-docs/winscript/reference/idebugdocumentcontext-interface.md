---
title: "Интерфейс IDebugDocumentContext | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugDocumentContext interface
ms.assetid: 665ee08a-5c6a-4ab1-ab93-de376acc9a74
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 432fbe9de5b1ab19c64ae1b9eeee36f3b1156d06
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumentcontext-interface"></a>Интерфейс IDebugDocumentContext
Предоставляет абстрактным представлением фрагмент документа, для которого выполняется отладка. Для текстовых документов это представление состоит из диапазона позицию символа.  
  
 Помимо методов, наследуемых от `IUnknown`, `IDebugDocumentContext` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDebugDocumentContext::GetDocument](../../winscript/reference/idebugdocumentcontext-getdocument.md)|Возвращает документ, содержащий этот контекст.|  
|[IDebugDocumentContext::EnumCodeContexts](../../winscript/reference/idebugdocumentcontext-enumcodecontexts.md)|Перечисляет контексты код, связанный с данным контекстом документа.|