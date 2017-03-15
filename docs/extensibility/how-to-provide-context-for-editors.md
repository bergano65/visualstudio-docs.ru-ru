---
title: "Практическое руководство: предоставляют контекст для редакторов | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - provide context
ms.assetid: 12df4d06-df6b-4eaf-a7bf-c83655a0c683
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 362cd554e0723b1137d033440c9844d6cf3e59dd
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-provide-context-for-editors"></a>Практическое руководство: предоставляют контекст для редакторов
Контекст редактора, активна только в том случае, если редактор находится в фокусе или находится в фокусе непосредственно перед фокус был перемещен в окне инструментов. Можно предоставить контекст для редактора следующим образом:  
  
1.  Создайте контейнер контекста.  
  
2.  Публикация контейнера контекста идентификатор элемента выбора (SEID).  
  
3.  Сохранить контекст в контейнере.  
  
 Эти задачи описаны в следующих процедурах. Дополнительные сведения о предоставлении контекста см. в разделе **надежные программирования** далее в этом разделе.  
  
### <a name="to-create-a-context-bag-for-an-editor-or-a-designer"></a>Чтобы создать контейнер контекста для редактор или конструктор  
  
1.  Вызов `QueryService` на вашей <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>интерфейс для <xref:Microsoft.VisualStudio.Shell.Interop.SVsMonitorUserContext>службы.</xref:Microsoft.VisualStudio.Shell.Interop.SVsMonitorUserContext> </xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>  
  
     Указатель на <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext>возвращается интерфейс.</xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext>  
  
2.  Вызов <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext.CreateEmptyContext%2A>метод для создания нового контекста или подконтекст контейнера.</xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext.CreateEmptyContext%2A>  
  
     Указатель на <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext>возвращается интерфейс.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext>  
  
3.  Вызов <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>метод для добавления атрибутов, ключевые слова для поиска или ключевые слова справки F1 контейнера контекста или подконтекст.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>  
  
4.  При создании контейнера подконтекст вызова <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddSubcontext%2A>метод связывание контейнера контекст родительского контейнера подконтекст.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddSubcontext%2A>  
  
5.  Вызов <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A>для получения уведомления при **динамической справки** окна является обновление.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A>  
  
     Наличие **динамической справки** вызвать окно редактора готовности обновление дает возможность отложить изменять контекст, пока не произойдет обновление. Это может повысить производительность, поскольку он позволяет отложить выполнение длительных алгоритмы до времени простоя системы.  
  
### <a name="to-publish-the-context-bag-to-the-seid"></a>Чтобы опубликовать контейнера контекста SEID  
  
1.  Вызов `QueryService` на <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>службы для возврата указателя на <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>интерфейса.</xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> </xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>  
  
2.  Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>, указав идентификатор элемента (`elementid` параметр) значение SEID_UserContext для указания, что контекст передает глобальном уровне.</xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>  
  
3.  Когда редактор или конструктор становится активным, значения в его <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>объекта передаются глобального выделения.</xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> Требуется только для завершения этого процесса один раз за сеанс и затем сохраните указатель глобальный контекст, созданные при вызове <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>  
  
### <a name="to-maintain-the-context-bag"></a>Для поддержания контекста контейнера  
  
1.  Реализуйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext>Чтобы убедиться, что **динамической справки** окно вызывает редактор или конструктор, перед обновлением.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext>  
  
     Для каждого контекста контейнера, который вызвал <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A>После создания контейнера контекста и реализовал <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate>, вызовы IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>сообщит поставщику контекста будет обновляться контейнера контекста.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate> </xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A> Этот вызов можно использовать для изменения атрибутов и ключевые слова в контексте контейнера и все сумок подконтекст перед **динамической справки** происходит обновление окна.  
  
2.  Вызов <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>на контейнере контекста для указания, что редактор или конструктор имеет новый контекст.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>  
  
     При **динамической справки** окно вызовы <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>, чтобы указать, что он обновляется, редактора или конструктора в это время можно обновить контекста, необходимые для контекста родительский контейнер и все сумок подконтекст.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>  
  
    > [!NOTE]
    >  `SetDirty` Флаг автоматически устанавливается значение `true` каждый раз, когда добавляется или удаляется из контекста контейнера контекста. **Динамической справки** окна вызывает только <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>на контейнере контекста при `SetDirty` флаг имеет значение `true`.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> Сбрасывается на `false` после обновления.  
  
3.  Вызов <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>Добавление контекста к коллекции активный контекст или <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A>для удаления контекста.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>  
  
## <a name="robust-programming"></a>Отказоустойчивость  
 При написании собственного редактора, необходимо выполнить все три процедуры в этом разделе, для предоставления контекста для редактора.  
  
> [!NOTE]
>  Чтобы правильно перейти в окно редактора или конструктора и убедитесь, что маршрутизация команд обновляется должным образом, необходимо вызвать метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>компонента, чтобы сделать его окном фокуса.</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>  
  
 SEID — это совокупность свойств, изменяемых на основе выделения. SEID информация доступна через глобальный выбор. Глобальный выбор подключен на события, вызванные <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>интерфейс, и список всех, выбрал (текущий редактор, текущего окна инструментов, текущей иерархии и т. д).</xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>  
  
 Редакторы и конструкторы в контексте которого можно изменить каждый раз, когда курсор перемещается в word, неэффективно постоянного обновления контейнера контекста. Чтобы более эффективно все время обновляется определение курсора, перемещение в окне редактора или конструктора, можно вызвать <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A> Это позволяет проводить изменения контекста до времени простоя и IDE контекста служба отправляет уведомление в редактор или конструктор, **динамической справки** обновление окна. Этот подход используется в процедуре «Ведение контейнера контекста» в этом разделе.  
  
 После предоставления контекста для действий в редактор или конструктор, необходимо предоставить определенные ключевое слово F1, чтобы пользователи могли получить справку для редактора или конструктора сам.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate></xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx></xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx>
