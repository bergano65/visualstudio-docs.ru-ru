---
title: Практическое руководство. Используйте Управление связанный откат | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - linked undo management
ms.assetid: af5cc22a-c9cf-45b1-a894-1022d563f3ca
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ce6d86d84d6f51b995649d5cbfda652262dcfc66
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60045725"
---
# <a name="how-to-use-linked-undo-management"></a>Практическое руководство. Используйте Управление связанный откат
Связанный откат позволяет пользователю одновременно отменить же изменения в нескольких файлах. Например для одновременного изменения текста в нескольких файлах программы, такие как файл заголовка и файл Visual C++, является связанную транзакцию отмены. Связанный откат возможности встроены в реализацию среды в диспетчер отмены, и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager> позволяет использовать эту возможность. Связанный откат реализуется родительский модуль отмены, которое связывает стеки отмены отдельной вместе, чтобы рассматриваться как один блок отмены. В следующем разделе подробно описана процедура использования связанный откат.

## <a name="to-use-linked-undo"></a>Чтобы использовать связанный откат

1. Вызовите `QueryService` на `SVsLinkedUndoManager` для получения указателя на `IVsLinkedUndoTransactionManager`.

2. Создания начальной родительская единица отмены, связанная с помощью вызова <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.OpenLinkedUndo%2A>. Это задает начальную точку для набора стеки отмены быть сгруппированы в связанные стеки отмены. В `OpenLinkedUndo` метода также необходимо будет указать, следует ли связанный откат strict или не строгая. Не строго связанное поведение отмены означает, что некоторые документы с связанный откат элементов с общим родителем можно закрыть, и по-прежнему не другой связанной отменить одноуровневых элементов в их стеках. Строго связанное поведение отмены указывает, что все связанные того же уровня стеки отмены придется отменять друг с другом или вообще не. Добавление последующие связанные стеки отмены операций путем вызова [IOleUndoManager::Add](/windows/desktop/api/ocidl/nf-ocidl-ioleundomanager-add) метод.

3. Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.CloseLinkedUndo%2A> для наката всех единиц связанный откат как один.

    > [!NOTE]
    >  Чтобы реализовать управление связанный откат в редакторе, добавьте механизмы управления отменой. Дополнительные сведения о реализации управления связанный откат см. в разделе [как: Реализуйте механизмы управления отменой](../extensibility/how-to-implement-undo-management.md).

## <a name="see-also"></a>См. также
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>
- [IOleParentUndoUnit](/windows/desktop/api/ocidl/nn-ocidl-ioleparentundounit)
- [IOleUndoUnit](/windows/desktop/api/ocidl/nn-ocidl-ioleundounit)
- [Практическое руководство. Реализуйте механизмы управления отменой](../extensibility/how-to-implement-undo-management.md)