---
title: 'Практическое: использовать связанный откат управления | Документация Майкрософт'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - linked undo management
ms.assetid: af5cc22a-c9cf-45b1-a894-1022d563f3ca
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d65873ae68fe7446ddd265a3af17e694bd475465
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2018
ms.locfileid: "39500424"
---
# <a name="how-to-use-linked-undo-management"></a>Практическое: использование связанного механизмы управления отменой
Связанный откат позволяет пользователю одновременно отменить же изменения в нескольких файлах. Например для одновременного изменения текста в нескольких файлах программы, такие как файл заголовка и файл Visual C++, является связанную транзакцию отмены. Связанный откат возможности встроены в реализацию среды в диспетчер отмены, и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager> позволяет использовать эту возможность. Связанный откат реализуется родительский модуль отмены, которое связывает стеки отмены отдельной вместе, чтобы рассматриваться как один блок отмены. В следующем разделе подробно описана процедура использования связанный откат.  
  
## <a name="to-use-linked-undo"></a>Чтобы использовать связанный откат  
  
1.  Вызовите `QueryService` на `SVsLinkedUndoManager` для получения указателя на `IVsLinkedUndoTransactionManager`.  
  
2.  Создания начальной родительская единица отмены, связанная с помощью вызова <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.OpenLinkedUndo%2A>. Это задает начальную точку для набора стеки отмены быть сгруппированы в связанные стеки отмены. В `OpenLinkedUndo` метода также необходимо будет указать, следует ли связанный откат strict или не строгая. Не строго связанное поведение отмены означает, что некоторые документы с связанный откат элементов с общим родителем можно закрыть, и по-прежнему не другой связанной отменить одноуровневых элементов в их стеках. Строго связанное поведение отмены указывает, что все связанные того же уровня стеки отмены придется отменять друг с другом или вообще не. Добавление последующие связанные стеки отмены операций путем вызова [IOleUndoManager::Add](http://msdn.microsoft.com/library/windows/desktop/ms680135) метод.  
  
3.  Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.CloseLinkedUndo%2A> для наката всех единиц связанный откат как один.  
  
    > [!NOTE]
    >  Чтобы реализовать управление связанный откат в редакторе, добавьте механизмы управления отменой. Дополнительные сведения о реализации управления связанный откат см. в разделе [как: реализуйте механизмы управления отменой](../extensibility/how-to-implement-undo-management.md).  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>   
 [IOleParentUndoUnit](http://msdn.microsoft.com/library/windows/desktop/ms682151)   
 [IOleUndoUnit](http://msdn.microsoft.com/library/windows/desktop/ms678476)   
 [Практическое: реализуйте механизмы управления отменой](../extensibility/how-to-implement-undo-management.md)