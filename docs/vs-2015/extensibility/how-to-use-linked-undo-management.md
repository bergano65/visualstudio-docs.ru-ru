---
title: Практическое руководство. Используйте Управление связанный откат | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - linked undo management
ms.assetid: af5cc22a-c9cf-45b1-a894-1022d563f3ca
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 442024b7be335c0aa010ce528142ac7a205097f8
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60062975"
---
# <a name="how-to-use-linked-undo-management"></a>Практическое руководство. Используйте Управление связанный откат
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Связанный откат позволяет пользователю одновременно отменить же изменения в нескольких файлах. Например для одновременного изменения текста в нескольких файлах программы, такие как файл заголовка и файл Visual C++, является связанную транзакцию отмены. Связанный откат возможности встроены в реализацию среды в диспетчер отмены, и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager> позволяет использовать эту возможность. Связанный откат реализуется родительский модуль отмены, которое связывает стеки отмены отдельной вместе, чтобы рассматриваться как один блок отмены. В следующем разделе подробно описана процедура использования связанный откат.  
  
### <a name="to-use-linked-undo"></a>Чтобы использовать связанный откат  
  
1. Вызовите `QueryService` на `SVsLinkedUndoManager` для получения указателя на `IVsLinkedUndoTransactionManager`.  
  
2. Создания начальной родительская единица отмены, связанная с помощью вызова <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.OpenLinkedUndo%2A>. Это задает начальную точку для набора стеки отмены быть сгруппированы в связанные стеки отмены. В `OpenLinkedUndo` метода также необходимо будет указать, следует ли связанный откат strict или не строгая. Не строго связанное поведение отмены означает, что некоторые документы с связанный откат элементов с общим родителем можно закрыть, и по-прежнему не другой связанной отменить одноуровневых элементов в их стеках. Строго связанное поведение отмены указывает, что все связанные того же уровня стеки отмены придется отменять друг с другом или вообще не. Добавление последующие связанные стеки отмены операций путем вызова [IOleUndoManager::Add](/windows/desktop/api/ocidl/nf-ocidl-ioleundomanager-add) метод.  
  
3. Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.CloseLinkedUndo%2A> для наката всех единиц связанный откат как один.  
  
    > [!NOTE]
    >  Чтобы реализовать управление связанный откат в редакторе, добавьте механизмы управления отменой. Дополнительные сведения о реализации управления связанный откат см. в разделе [как: Реализуйте механизмы управления отменой](../extensibility/how-to-implement-undo-management.md).  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>   
 [IOleParentUndoUnit](/windows/desktop/api/ocidl/nn-ocidl-ioleparentundounit)   
 [IOleUndoUnit](/windows/desktop/api/ocidl/nn-ocidl-ioleundounit)   
 [Практическое руководство. Реализуйте механизмы управления отменой](../extensibility/how-to-implement-undo-management.md)
