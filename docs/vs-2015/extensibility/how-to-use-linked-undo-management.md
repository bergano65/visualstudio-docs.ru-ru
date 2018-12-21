---
title: 'Практическое: использовать связанный откат управления | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - linked undo management
ms.assetid: af5cc22a-c9cf-45b1-a894-1022d563f3ca
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2a5da4b7c25ab97356798fe8c2db184982fc885d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51739302"
---
# <a name="how-to-use-linked-undo-management"></a>Практическое: использовать связанный откат управления
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Связанный откат позволяет пользователю одновременно отменить же изменения в нескольких файлах. Например для одновременного изменения текста в нескольких файлах программы, такие как файл заголовка и файл Visual C++, является связанную транзакцию отмены. Связанный откат возможности встроены в реализацию среды в диспетчер отмены, и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager> позволяет использовать эту возможность. Связанный откат реализуется родительский модуль отмены, которое связывает стеки отмены отдельной вместе, чтобы рассматриваться как один блок отмены. В следующем разделе подробно описана процедура использования связанный откат.  
  
### <a name="to-use-linked-undo"></a>Чтобы использовать связанный откат  
  
1.  Вызовите `QueryService` на `SVsLinkedUndoManager` для получения указателя на `IVsLinkedUndoTransactionManager`.  
  
2.  Создания начальной родительская единица отмены, связанная с помощью вызова <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.OpenLinkedUndo%2A>. Это задает начальную точку для набора стеки отмены быть сгруппированы в связанные стеки отмены. В `OpenLinkedUndo` метода также необходимо будет указать, следует ли связанный откат strict или не строгая. Не строго связанное поведение отмены означает, что некоторые документы с связанный откат элементов с общим родителем можно закрыть, и по-прежнему не другой связанной отменить одноуровневых элементов в их стеках. Строго связанное поведение отмены указывает, что все связанные того же уровня стеки отмены придется отменять друг с другом или вообще не. Добавление последующие связанные стеки отмены операций путем вызова [IOleUndoManager::Add](http://msdn.microsoft.com/library/windows/desktop/ms680135) метод.  
  
3.  Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.CloseLinkedUndo%2A> для наката всех единиц связанный откат как один.  
  
    > [!NOTE]
    >  Чтобы реализовать управление связанный откат в редакторе, добавьте механизмы управления отменой. Дополнительные сведения о реализации управления связанный откат см. в разделе [как: реализуйте отменить управления](../extensibility/how-to-implement-undo-management.md).  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>   
 [IOleParentUndoUnit](http://msdn.microsoft.com/library/windows/desktop/ms682151)   
 [IOleUndoUnit](http://msdn.microsoft.com/library/windows/desktop/ms678476)   
 [Практическое руководство. Реализация управления отменой](../extensibility/how-to-implement-undo-management.md)

