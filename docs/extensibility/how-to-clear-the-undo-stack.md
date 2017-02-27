---
title: "Практическое руководство: Очистка стека отмены | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "редакторы [Visual Studio SDK] прежних версий - очистить стек отмены"
ms.assetid: 2200d2d4-7f58-401c-87fc-ddd32d368193
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# Практическое руководство: Очистка стека отмены
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

В следующей процедуре объясняется, как очищать стек отката ниже.  
  
### Очищать стек отката  
  
1.  Очистить использование стек отката [IOleUndoManager:: DiscardFrom](http://msdn.microsoft.com/library/windows/desktop/ms693799) метод.  Ниже приведен пример этого:  
  
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
  
## См. также  
 [Практическое руководство: реализация управления отмены](../extensibility/how-to-implement-undo-management.md)