---
title: Как использовать связанное управление отменой | Документация Майкрософт
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
ms.openlocfilehash: 67d0d173909b8cdfe2eaf0d56aa5c99c437d5ad8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842592"
---
# <a name="how-to-use-linked-undo-management"></a>Практическое руководство. Использование управления связанной отменой
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Связанная Отмена позволяет пользователю одновременно отменять одни и те же изменения в нескольких файлах. Например, одновременные изменения текста в нескольких программах, таких как заголовочный файл и файл Visual C++, — это связанная транзакция отмены. Связанная возможность отмены встроена в реализацию диспетчера отмены в среде и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager> позволяет управлять этой возможностью. Связанная отмена реализуется родительской единицей отката, которая может связывать отдельные стеки отмены и обрабатывать их как одну единицу отмены. Процедура использования связанной отмены подробно описана в следующем разделе.  
  
### <a name="to-use-linked-undo"></a>Использование связанной отмены  
  
1. Вызовите `QueryService` On `SVsLinkedUndoManager` , чтобы получить указатель на `IVsLinkedUndoTransactionManager` .  
  
2. Создайте начальную родительскую связанную единицу отмены, вызвав <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.OpenLinkedUndo%2A> . Это задает начальную точку для набора стеков отмены, которые будут сгруппированы в связанные стеки отмены. В `OpenLinkedUndo` методе также необходимо указать, должна ли связанная отмена быть в ограниченном или не ограничена. Недолгосрочное связанное поведение отмены означает, что некоторые документы со связанными одноуровневыми элементами отмены могут закрыться, и все остальные связанные элементы отменять на их стеках будут оставаться неизменными. Режим с четким связыванием указывает, что все связанные стеки отмены одного уровня должны быть отменены вместе или вообще не иметь. Добавьте последующие связанные стеки отмены, вызвав метод [иолеундоманажер:: Add](/windows/desktop/api/ocidl/nf-ocidl-ioleundomanager-add) .  
  
3. Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.CloseLinkedUndo%2A> , чтобы выполнить откат всех связанных блоков отмены в качестве одного.  
  
    > [!NOTE]
    > Чтобы реализовать связанное управление отменой в редакторе, добавьте управление отменой. Дополнительные сведения о реализации связанного управления отменой см. [в разделе руководство. Реализация отмены управления](../extensibility/how-to-implement-undo-management.md).  
  
## <a name="see-also"></a>См. также:  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>   
 [иолепарентундаунит](/windows/desktop/api/ocidl/nn-ocidl-ioleparentundounit)   
 [иолеундаунит](/windows/desktop/api/ocidl/nn-ocidl-ioleundounit)   
 [Практическое руководство. Реализация управления отменой](../extensibility/how-to-implement-undo-management.md)
