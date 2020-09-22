---
title: Как предоставить контекст для редакторов | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - provide context
ms.assetid: 12df4d06-df6b-4eaf-a7bf-c83655a0c683
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 11a98599a9812cd00650d113170ff55c01ac44db
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842684"
---
# <a name="how-to-provide-context-for-editors"></a>Практическое руководство. Предоставление контекста для редакторов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Для редактора контекст активен, только если редактор имеет фокус или фокус находится непосредственно перед перемещением фокуса в окно инструментов. Контекст для редактора можно предоставить, выполнив следующие действия.  
  
1. Создайте контейнер контекста.  
  
2. Опубликуйте контейнер контекста в идентификаторе элемента Selection (Сеид).  
  
3. Сохраните контекст в контейнере.  
  
   Эти задачи описаны в следующих процедурах. Дополнительные сведения о предоставлении контекста см. в разделе **надежное программирование** далее в этой статье.  
  
### <a name="to-create-a-context-bag-for-an-editor-or-a-designer"></a>Создание контейнера контекста для редактора или конструктора  
  
1. Вызовите `QueryService` <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> интерфейс для <xref:Microsoft.VisualStudio.Shell.Interop.SVsMonitorUserContext> службы.  
  
     Возвращается указатель на <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext> интерфейс.  
  
2. Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorUserContext.CreateEmptyContext%2A> метод, чтобы создать новый контекст или контейнер подконтекста.  
  
     Возвращается указатель на <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext> интерфейс.  
  
3. Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A> метод, чтобы добавить атрибуты, ключевые слова поиска или ключевые слова F1 в контекст или контейнер подконтекста.  
  
4. При создании контейнера подконтекстов вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddSubcontext%2A> метод, чтобы связать контейнер подконтекста с родительским контейнером контекста.  
  
5. Вызов <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A> для получения уведомления при обновлении окна **динамической справки** .  
  
     Если окно **динамической справки** вызывает редактор, когда он готов к обновлению, дает возможность отложить изменение контекста до возникновения обновления. Это может повысить производительность, поскольку позволяет отложить выполнение алгоритмов, требующих времени, пока не будет доступно время простоя системы.  
  
### <a name="to-publish-the-context-bag-to-the-seid"></a>Публикация контейнера контекста в Сеид  
  
1. Вызовите `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> службу, чтобы вернуть указатель на <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> интерфейс.  
  
2. Вызовите метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A> , указав значение идентификатора элемента ( `elementid` parameter) SEID_UserContext, чтобы указать, что контекст передается на глобальный уровень.  
  
3. Когда редактор или конструктор становятся активными, значения в его <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> объекте передаются в глобальную область выделения. Этот процесс необходимо выполнить один раз для каждого сеанса, а затем сохранить указатель на глобальный контекст, созданный при вызове <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A> .  
  
### <a name="to-maintain-the-context-bag"></a>Поддержка контейнера контекста  
  
1. Реализуйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext> , чтобы убедиться, что окно **динамической справки** вызывает редактор или конструктор перед обновлением.  
  
     Для каждого контейнера контекста, вызванного <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AdviseUpdate%2A> после создания и реализации контейнера контекста <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate> , вызовы интегрированной среды разработки <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> уведомляют поставщика контекста о том, что контейнер контекста будет обновлен. Этот вызов можно использовать для изменения атрибутов и ключевых слов в контейнере контекста и во всех контейнерах подконтекстов перед обновлением окна **динамической справки** .  
  
2. Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A> в контейнере контекста, чтобы указать, что в редакторе или конструкторе есть новый контекст.  
  
     Когда окно **динамической справки** вызывает метод <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> , чтобы указать, что он обновляется, редактор или конструктор может обновить контекст соответствующим образом как для родительского контейнера контекста, так и для всех контейнеров подконтекстов в это время.  
  
    > [!NOTE]
    > `SetDirty`Флаг автоматически устанавливается в `true` каждый раз, когда контекст добавляется в контейнер контекста или удаляется из него. Окно **динамической справки** вызывает только <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContextUpdate.UpdateUserContext%2A> в контейнере контекста, если `SetDirty` флаг имеет значение `true` . После обновления он сбрасывается `false` .  
  
3. Вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.AddAttribute%2A> , чтобы добавить контекст в коллекцию Active context или <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.RemoveAttribute%2A> удалить контекст.  
  
## <a name="robust-programming"></a>Отказоустойчивость  
 При написании собственного редактора необходимо выполнить все три процедуры, описанные в этом разделе, чтобы предоставить контекст для редактора.  
  
> [!NOTE]
> Чтобы правильно активировать окно редактора или конструктора и убедиться, что маршрутизация команд правильно обновлена, необходимо вызвать <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> для компонента, чтобы сделать его окном фокуса.  
  
 Сеид — это коллекция свойств, которые изменяются в зависимости от выбора. Сведения о Сеид доступны в глобальном выборе. Глобальный выбор разбивается на события, активируемые <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx> интерфейсом, и содержит список всех элементов, которые выбраны (текущий редактор, текущее окно инструментов, текущая иерархия и т. д.).  
  
 Для редакторов и конструкторов, в которых контекст может изменяться всякий раз, когда курсор перемещается внутри слова, непрерывно обновлять набор контекстов неэффективно. Чтобы сделать обновление более эффективным в любое время, когда вы обнаружите перемещение курсора в редакторе или окне конструктора, можно вызвать <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserContext.SetDirty%2A> . Это позволит сохранить контекстные изменения до тех пор, пока не будет открыто время простоя и служба контекста IDE отправит уведомление редактору или конструктору, который обновляется окном **динамической справки** . Этот подход используется в процедуре "сохранение контейнера контекста" в этом разделе.  
  
 После предоставления контекста для действий в редакторе или конструкторе необходимо указать конкретное ключевое слово F1, чтобы разрешить пользователям получать справку для редактора или конструктора.  
  
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
