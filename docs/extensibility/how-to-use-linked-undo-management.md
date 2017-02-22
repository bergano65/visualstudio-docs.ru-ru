---
title: "Практическое руководство: использование управления связанный откат | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "редакторы [Visual Studio SDK] прежних версий - связанный откат управления"
ms.assetid: af5cc22a-c9cf-45b1-a894-1022d563f3ca
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# Практическое руководство: использование управления связанный откат
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Связанный откат дает пользователю одновременно для отмены те же правки в нескольких файлах.  Например, синхронное текст изменяет через несколько программных файлов, таких как файл заголовка и файл Visual C\+\+, связанная rollback transaction.  Связанная возможность отката встроена в реализацию диспетчера отката и среды <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager> позволяет управлять эту возможность.  Связанный откат на родительский единицу отката, которая может связать отдельном стеки отката, которые должны подготавливаться к просмотру в виде единственной единицей отката.  Процедура для использования связанных отката детализирована в следующем разделе.  
  
### Для отката связанному использованием  
  
1.  Вызов `QueryService` на  `SVsLinkedUndoManager` получить указатель на  `IVsLinkedUndoTransactionManager`.  
  
2.  Создание исходного связанная родительским единица отката путем вызова <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.OpenLinkedUndo%2A>.  Это задает начальную точку для наборов стеков отката для группирования в связанные стеки отката.  в `OpenLinkedUndo` метод кроме того, необходимо определить, нужно ли связанный откат быть строги или non\-строги.  Non\-строгая связанной функциональности отката означает, что некоторые из документов со связанными элементами с общим родителем отката и по\-прежнему может закрыть другие связанные элементы с общим родителем, rollback на их стеках.  Строго связанное поведение отмены указывает, что все связанные стеки отмены одного и того же уровня должны отменяться вместе или не отменяться вообще.  Добавьте последующие связанные стеки отката путем вызова [IOleUndoManager:: Добавить](http://msdn.microsoft.com/library/windows/desktop/ms680135) метод.  
  
3.  Вызов <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLinkedUndoTransactionManager.CloseLinkedUndo%2A> откатить все связанные единицы отката как одно.  
  
    > [!NOTE]
    >  К связанному инструментом управления отката в редакторе, добавьте элемент управления отката.  Дополнительные сведения о реализации см. связанный элемент управления отката. [Как Реализуйте элемент управления отката](../extensibility/how-to-implement-undo-management.md).  
  
## См. также  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>   
 [IOleParentUndoUnit](http://msdn.microsoft.com/library/windows/desktop/ms682151)   
 [IOleUndoUnit](http://msdn.microsoft.com/library/windows/desktop/ms678476)   
 [Практическое руководство: реализация управления отмены](../extensibility/how-to-implement-undo-management.md)