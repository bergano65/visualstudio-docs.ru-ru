---
title: "Как: использовать связанный откат управления | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - linked undo management
ms.assetid: af5cc22a-c9cf-45b1-a894-1022d563f3ca
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 7a025cdfc14eb39dad7ea2bc72a69f1f260fb583
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-linked-undo-management"></a>Как: использовать связанный откат управления
Связанный откат позволяет пользователю одновременно отменить же изменения в нескольких файлах. Например для одновременного изменения текста в нескольких файлах программы, таких как файл заголовка и файл кода Visual C++ является связанный откат транзакции. Связанный откат возможностей встроена в реализации среды в диспетчер отмены и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager> позволяет реализовать эту возможность. Связанный откат реализуется блок отмены родительской, который можно связать стеки отдельные отмены вместе, чтобы рассматриваться как один блок отмены. В следующем разделе подробно описана процедура использования связанный откат.  
  
### <a name="to-use-linked-undo"></a>Чтобы использовать связанный откат  
  
1.  Вызовите `QueryService` на `SVsLinkedUndoManager` для получения указателя на `IVsLinkedUndoTransactionManager`.  
  
2.  Создать связанный откат начальной родительское подразделение, вызвав <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.OpenLinkedUndo%2A>. Это задает начальную точку для набора стеки отмены, чтобы разделить на связанные стеки отмены. В `OpenLinkedUndo` метод, необходимо также указать, следует ли связанный откат strict или нестрогом. Не строго связанное поведение отмены означает, что некоторые документы с связанный откат элементов с общим родителем можно закрыть, а по-прежнему оставьте связан другой отменить одноуровневых элементов в их стеках. Строго связанное поведение отмены указывает, что все связанные того же уровня стеки отмены иметь отменяться вместе или не полностью. Добавить последующие связанные стеки отменить, вызвав [IOleUndoManager::Add](http://msdn.microsoft.com/library/windows/desktop/ms680135) метод.  
  
3.  Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.CloseLinkedUndo%2A> для наката все единицы связанный откат как один.  
  
    > [!NOTE]
    >  Для реализации управления связанный откат в редакторе, добавьте управления отмены. Дополнительные сведения о реализации управления связанный откат см. в разделе [как: реализуйте отменить управления](../extensibility/how-to-implement-undo-management.md).  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>   
 [IOleParentUndoUnit](http://msdn.microsoft.com/library/windows/desktop/ms682151)   
 [IOleUndoUnit](http://msdn.microsoft.com/library/windows/desktop/ms678476)   
 [Как: реализации управления отмены](../extensibility/how-to-implement-undo-management.md)