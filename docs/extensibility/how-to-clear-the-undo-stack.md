---
title: Практическое руководство. Очистить стек отмены | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - clear undo stack
ms.assetid: 2200d2d4-7f58-401c-87fc-ddd32d368193
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 442c362a3d9c65cd75a4f3f5446228630f9cb5b1
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66344621"
---
# <a name="how-to-clear-the-undo-stack"></a>Практическое руководство. Очистить стек отмены
Следующую процедуру ниже объясняется, как очистить стек отмены.

## <a name="to-clear-the-undo-stack"></a>Чтобы очистить стек отмены

1. Снимите флажок использовать стек отмены [IOleUndoManager::DiscardFrom](/windows/desktop/api/ocidl/nf-ocidl-ioleundomanager-discardfrom) метод. Ниже приведен пример этого:

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
- [Практическое руководство. Реализуйте механизмы управления отменой](../extensibility/how-to-implement-undo-management.md)