---
title: "Как: предоставляют контекст для редакторов | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: editors [Visual Studio SDK], legacy - provide context
ms.assetid: 12df4d06-df6b-4eaf-a7bf-c83655a0c683
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: d9b89c4e45f8268df55386d321816325fb50174c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-provide-context-for-editors"></a>Как: предоставляют контекст для редакторов
Контекст для редактора активна только в том случае, если редактор имеет фокус или находится в фокусе непосредственно перед фокус переместился в окно инструментов. Может предоставить контекст для редактора следующим образом:  
  
1.  Создайте контейнер контекста.  
  
2.  Публикация контейнера контекста идентификатора элемента выбора (SEID).  
  
3.  Ведение контекст, в контейнере.  
  
 Эти задачи описаны в следующих процедурах. Дополнительные сведения о предоставлении контекста см. в разделе **надежные программирования** далее в этом разделе.  
  
### <a name="to-create-a-context-bag-for-an-editor-or-a-designer"></a>Чтобы создать контейнер контекст для редактор или конструктор  
  
1.  Вызовите `QueryService` на ваш <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> интерфейс для <xref:Microsoft.VisualStudio.Shell.Interop.SVsMonitorUserContext> службы.  
  
     Указатель на <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext> возвращается.  
  
2.  Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext.CreateEmptyContext%2A> метод для создания нового контекста или подконтекст контейнера.  
  
     Указатель на <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext> возвращается.  
  
3.  Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A> метод, чтобы добавить атрибуты, ключевые слова для поиска или ключевые слова справки F1 для контекста или подконтекст контейнере.  
  
4.  При создании контейнера подконтекст вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddSubcontext%2A> метод, чтобы связать контейнер подконтекст контекст родительского контейнера.  
  
5.  Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A> получать уведомления при **динамической справки** окно является обновление.  
  
     Наличие **динамической справки** окна вызова редактора готовности обновление дает возможность отложить изменять контекст, пока происходит обновление. Это может повысить производительность, поскольку он позволяет отложить выполнение длительных алгоритмы пока не станет доступен время простоя системы.  
  
### <a name="to-publish-the-context-bag-to-the-seid"></a>Для публикации в контейнере контекста SEID  
  
1.  Вызовите `QueryService` на <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> службы для возврата указателя на <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> интерфейса.  
  
2.  Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>, указав идентификатор элемента (`elementid` параметра) значение SEID_UserContext для указания, что контекст передает глобальном уровне.  
  
3.  Когда редактор или конструктор становится активным, значения в его <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> объекта распространяются на глобального выделения. Требуется только для завершения этого процесса, один раз за сеанс и затем сохраните указатель на глобальном контексте, созданные при вызове <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>.  
  
### <a name="to-maintain-the-context-bag"></a>Для поддержания контейнера контекста  
  
1.  Реализуйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext> чтобы убедиться, что **динамической справки** окно вызывает редактор или конструктор, перед обновлением.  
  
     Для каждого контейнера контекста, вызванным <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A> после создания контейнера контекста и внедрила <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate>, вызовы IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> известить поставщик контекста будет обновляться в контейнере контекста. Этот вызов можно использовать для изменения атрибутов и ключевые слова в контейнере контекста и в любой пакеты подконтекст перед **динамической справки** происходит обновление окна.  
  
2.  Вызов <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A> на наборе контекста для указания, что редактор или конструктор имеет новый контекст.  
  
     Когда **динамической справки** вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> , чтобы указать, что он обновляется, редактора или конструктора можно обновить контекста, необходимые для контекста родительского контейнера и все контейнеры подконтекст в это время.  
  
    > [!NOTE]
    >  `SetDirty` Флаг автоматически присваивается `true` каждый раз, когда добавляется или удаляется из контейнера контекста контекста. **Динамической справки** окна вызывает только <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> на наборе контекст Если `SetDirty` флаг имеет значение `true`. Задается равным `false` после обновления.  
  
3.  Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A> Чтобы добавить контекст к коллекции активный контекст или <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A> для удаления контекста.  
  
## <a name="robust-programming"></a>Отказоустойчивость  
 При написании собственного редактора необходимо выполнить все три процедуры, описанные в этом разделе, чтобы обеспечить контекст для редактора.  
  
> [!NOTE]
>  Чтобы правильно активировать окно редактора или конструктора и убедитесь, что маршрутизация команд обновлена должным образом, необходимо вызвать метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> вносить активному окну в компоненте.  
  
 SEID — это коллекция свойств, изменение на основе выделения. SEID информация доступна через глобального выделения. Глобального выделения, встроены в события, вызванные <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> интерфейс, и список всех, выбрал (текущий редактор, текущее окно инструментов, текущей иерархии и т. д.).  
  
 Редакторы и конструкторы в контексте которого можно изменить каждый раз, когда курсор перемещается в word, неэффективно постоянного обновления контейнера контекста. Чтобы сделать обновление более эффективно любое время, определение курсора, перемещение в редакторе и окно «конструктор», можно вызвать <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>. Это позволит дождитесь изменения контекста времени простоя и служба контекста IDE отправляет уведомление в редактор или конструктор, **динамической справки** окна обновляется. Этот подход используется в процедуре «Ведение контейнера контекста» в этом разделе.  
  
 После предоставления контекста для действий в редактор или конструктор, должен предоставить конкретных ключевое слово F1, чтобы пользователи могли получить справку для самого конструктора или редактора.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>