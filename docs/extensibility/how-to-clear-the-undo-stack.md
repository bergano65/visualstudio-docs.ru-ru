---
title: Как выполнить Очистить стек отмены | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - clear undo stack
ms.assetid: 2200d2d4-7f58-401c-87fc-ddd32d368193
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 14cf2af71f492dc4a82f6d8d9cf05fadcb0dcda2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53827551"
---
# <a name="how-to-clear-the-undo-stack"></a>Как выполнить Очистить стек отмены
Следующую процедуру ниже объясняется, как очистить стек отмены.  
  
## <a name="to-clear-the-undo-stack"></a>Чтобы очистить стек отмены  
  
1.  Снимите флажок использовать стек отмены [IOleUndoManager::DiscardFrom](/windows/desktop/api/ocidl/nf-ocidl-ioleundomanager-discardfrom) метод. Ниже приведен пример этого:  
  
    ```  
    HRESULT CCmdWindow::ClearUndoStack()  
    {  
      HRESULT hr = S_OK;  
  
      if (m_pUndoMgr == NULL)  
        {  
        IfFailGo(m_pTextLines->GetUndoManager(&m_pUndoMgr));  
        ASSERT(m_pUndoMgr != NULL, "",;);  
        }  
  
      IfFailGo(m_pUndoMgr->DiscardFrom(NULL));  
  
    Error:  
      return hr;  
    }  
    ```  
  
## <a name="see-also"></a>См. также  
 [Практическое руководство. Реализуйте механизмы управления отменой](../extensibility/how-to-implement-undo-management.md)