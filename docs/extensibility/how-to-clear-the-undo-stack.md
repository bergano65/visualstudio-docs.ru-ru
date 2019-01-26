---
title: Как выполнить Очистить стек отмены | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - clear undo stack
ms.assetid: 2200d2d4-7f58-401c-87fc-ddd32d368193
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 71c8e80fceef685b49af53fb5c369500315bbea9
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55000176"
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