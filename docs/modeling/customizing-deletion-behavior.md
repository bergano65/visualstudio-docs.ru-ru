---
title: "Настройка функции удаления | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.dsltools.dsldesigner.deletebehavior
helpviewer_keywords: Domain-Specific Language, deletion
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: c51c44d47f24994e75ca91b4f4d8d7f2c9a805a6
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/13/2018
---
# <a name="customizing-deletion-behavior"></a>Настройка функции удаления
Удаление элемента обычно приводит также к удалению связанных элементов. Удаляются все подключенные к нему отношения и дочерние элементы. Это поведение называется *удаление распространений*. Распространение удалений можно настраивать, например, для организации удаления дополнительных связанных элементов. Написав код программы, можно сделать распространение удалений зависимым от состояния модели. Также можно в ответ на удаление вызвать другие изменения.  
  
 Этот раздел включает следующие подразделы:  
  
-   [Удаление по умолчанию](#default)  
  
-   [Установка параметра распространить удаление роли](#property)  
  
-   [Переопределение закрытия удалить](#closure) -используйте этот способ, где удаление может привести к удалению соседних элементов.  
  
-   [С помощью OnDeleting и OnDeleted](#ondeleting) -использовать эти методы, в которых ответ может содержать другие действия, такие как обновление значение внутри или за пределами хранилища.  
  
-   [Правила удаления](#rules) — использовать правила распространения обновлений любого типа в хранилище, где одно изменение может привести к другим пользователям.  
  
-   [События удаления](#rules) -использование хранилища событий для распространения обновлений за пределы хранилища, например для других [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] документов.  
  
-   [Отменить объединение](#unmerge) -использовать операцию отменить объединение, чтобы отменить операцию слияния, присоединена к родительской дочерний элемент.  
  
##  <a name="default"></a>Удаление по умолчанию  
 По умолчанию распространением удалений управляют следующие правила.  
  
-   Если элемент удаляется, также все внедренные элементы удаляются. Внедренные элементы — это целевые объекты отношений внедрения, для которых этот элемент является источником. Например, если определено отношение внедрения из **альбом** для **песню**, то при удалении конкретного альбома, также будут удалены все песни.  
  
     При этом удаление песни не ведет к удалению альбома.  
  
-   По умолчанию удаление не распространяется на ссылочные отношения. Если ссылочная связь **ArtistPlaysOnAlbum** из **альбом** для **исполнителя**альбом при удалении не удаляются все связанные исполнителя и не поддерживает удаление художник Удалите все альбома.  
  
     При этом удаление распространяется на некоторые встроенные отношения. Например, если удаляется элемент модели, также удаляется его фигура на схеме. Элемент и фигура связаны ссылочным отношением `PresentationViewsSubject`.  
  
-   Удаляется каждое связанное с элементом отношение в исходной или целевой роли. Свойство противоположной роли элемента больше не содержит удаленный элемент.  
  
##  <a name="property"></a>Установка параметра распространить удаление роли  
 Распространение удаления можно вызывать по ссылочному отношению или из встроенного дочернего элемента на родительский.  
  
#### <a name="to-set-delete-propagation"></a>Настройка распространения удаления  
  
1.  Схема определения DSL, выберите *роли* в котором необходимо удалить во время распространения. Роль представлена линией слева или справа от поля доменной связи.  
  
     Например, если требуется указать, что при удалении альбома следует удалить связанного исполнителя, выберите роль, связанную с классом домена "Исполнитель".  
  
2.  В окне свойств задайте **распространяет удалить** свойство.  
  
3.  Нажмите клавишу F5 и убедитесь в выполнении следующих условий.  
  
    -   Когда удаляется экземпляр этого отношения, удаляется также элемент в выбранной роли.  
  
    -   Когда удаляется элемент в противоположной роли, также удаляются экземпляры этого отношения и связанные элементы в этой роли.  
  
 Можно также просмотреть **распространяет удаление** в диалоговом окне **сведений DSL** окна. Выберите класс домена и откройте окно сведений DSL **поведения при удалении** страницы с помощью кнопки в части окна. **Propagate** вариант отображается для каждой связи противоположной роли. **Удалить стиль** столбец показывает, является ли **Propagate** параметр — параметры по умолчанию, но он не повлияют отдельные.  
  
## <a name="delete-propagation-by-using-program-code"></a>Распространение удаления с помощью кода программы  
 Только параметры в файле определения DSL позволяют выбирать, распространять ли удаление на соседние элементы. Для реализации более сложной схемы распространения удаления можно написать код программы.  
  
> [!NOTE]
>  Чтобы добавить программный код в определение DSL, создайте отдельный файл кода в **Dsl** проекта и записи определения разделяемых классов для расширения классов в папке созданного кода. Дополнительные сведения см. в разделе [написание кода для настройки доменного языка](../modeling/writing-code-to-customise-a-domain-specific-language.md).  
  
##  <a name="closure"></a>Определение закрытия Delete  
 Операции удаления с помощью класса *YourModel *** DeleteClosure** чтобы определить, какие элементы, чтобы удалить данный первоначального выбора. Проходя диаграмму отношений, он циклично вызывает методы `ShouldVisitRelationship()` и `ShouldVisitRolePlayer()`. Эти методы можно переопределить. ShouldVisitRolePlayer входит в состав идентификации ссылки и элемент в одной из ролей по ссылке. Это позволяет вернуть одно из следующих значений:  
  
-   **VisitorFilterResult.Yes**— должен быть удален элемент и walker следует продолжить попробовать элемента с другими элементами.  
  
-   **VisitorFilterResult.DoNotCare** -элемент не должны удаляться, если пользователь ответит другой запрос, он должен быть удален.  
  
-   **VisitorFilterResult.Never** -элемент не должны удаляться, даже если другой запрос отвечает **Да**, и не пытайтесь выполнить обход элемента с другими элементами.  
  
```  
// When a musician is deleted, delete their albums with a low rating.  
// Override methods in <YourDsl>DeleteClosure in DomainModel.cs  
partial class MusicLibDeleteClosure  
{  
  public override VisitorFilterResult ShouldVisitRolePlayer  
    (ElementWalker walker, ModelElement sourceElement, ElementLink elementLink,   
    DomainRoleInfo targetDomainRole, ModelElement targetRolePlayer)  
  {  
    ArtistAppearsInAlbum link = elementLink as ArtistAppearsInAlbum;  
    if (link != null   
       && targetDomainRole.RolePlayer.Id == Album.DomainClassId)  
    {  
      // Count other unvisited links to the Album of this link.  
      if (ArtistAppearsInAlbum.GetLinksToArtists(link.Album)  
              .Where(linkAlbumArtist =>   
                     linkAlbumArtist != link &&  
                     !walker.Visited(linkAlbumArtist))  
              .Count() == 0)  
      {  
        // Should delete this role player:  
        return VisitorFilterResult.Yes;   
      }  
      else  
        // Don't delete unless another relationship deletes it:  
        return VisitorFilterResult.DoNotCare;   
    }  
    else   
    {  
      // Test for and respond to other relationships and roles here.  
  
      // Not the relationship or role we're interested in.  
      return base.ShouldVisitRolePlayer(walker, sourceElement,   
             elementLink, targetDomainRole, targetRolePlayer);  
    }  
  }  
}  
  
```  
  
 Технология замыкания гарантирует определение удаляемого набора элементов и связей перед началом удаления. Обход также объединяет результаты замыкания с результатами из других частей модели.  
  
 В то же время данная технология предполагает, что удаление влияет только на соседние элементы в диаграмме отношений. Нельзя использовать этот метод для удаления элемента в другой части модели, а также для добавления элементов или внесения других изменений в ответ на удаление.  
  
##  <a name="ondeleting"></a>С помощью OnDeleting и OnDeleted  
 В классе или доменной связи методы `OnDeleting()` или `OnDeleted()` переопределить нельзя.  
  
1.  <xref:Microsoft.VisualStudio.Modeling.ModelElement.OnDeleting%2A>вызывается, когда элемент которой нужно удалить, но до его связей, был отключен. Он по-прежнему находится в `store.ElementDirectory` и допускает переход в другие или из других элементов.  
  
     Если несколько элементов удаляются в одно и то же время, то перед выполнением этого действия для них всех вызывается метод OnDeleting.  
  
     `IsDeleting`имеет значение true.  
  
2.  <xref:Microsoft.VisualStudio.Modeling.ModelElement.OnDeleted%2A>вызывается, когда элемент был удален. Он остается в куче CLR, чтобы при необходимости можно было выполнить отмену. При это он теряет связи от другими элементами и удаляется из `store.ElementDirectory`. Для связей роли по-прежнему ссылаться на старый исполнители роли.`IsDeleted` имеет значение true.  
  
3.  Методы OnDeleting и OnDeleted вызываются, когда пользователь запускает операцию отмены после создания элемента, а также когда предыдущее удаление повторяется в операции повтора. В таких случаях во избежание обновления элементов хранилища используйте метод `this.Store.InUndoRedoOrRollback`. Дополнительные сведения см. в разделе [как: использование транзакций для обновления модели](../modeling/how-to-use-transactions-to-update-the-model.md).  
  
 Например, следующий код удаляет альбом, когда удаляется его последняя дочерняя песня:  
  
```  
  
// Delete the parent Album when the last Song is deleted.  
// Override methods in the embedding relationship between Album and Song:  
partial class AlbumHasSongs  
{  
  protected override void OnDeleted()  
  {  
    base.OnDeleted();  
    // Don't perform in-store actions in undo:  
    if (this.Store.InUndoRedoOrRollback) return;  
    // Relationship source and target still work:  
    // Don't bother if source is already on its way out:  
    if (!this.Album.IsDeleting && !this.Album.IsDeleted)  
    {  
      if (this.Album.Songs.Count == 0)  
      {   
        this.Album.Delete();  
} } } }  
  
```  
  
 Часто полезнее активировать триггер из удаления отношения, чем из элемента роли, так как он работает и при удалении элемента, и при удалении самого отношения. Для ссылочного отношения может распространение удаления может потребоваться при удалении связанного элемента, а не самого отношения. В этом примере альбом удаляется, когда удаляется последний указанный в нем исполнитель, но не отвечает, если удаляются отношения:  
  
```  
using System.Linq; ...  
// Assumes a many-many reference relationship   
// between Artist and Album.    
partial class Artist  
{  
  protected override void OnDeleting()  
  {  
    base.OnDeleting();  
    if (this.Store.InUndoRedoOrRollback) return;  
    List<Album> toDelete = new List<Album>();  
    foreach (Album album in this.Albums)  
    {  
      if (album.Artists.Where(artist => !artist.IsDeleting)  
                        .Count() == 0)  
      {  
        toDelete.Add(album);  
      }  
    }  
    foreach (Album album in toDelete)  
    {  
      album.Delete();  
} } }  
  
```  
  
 Когда к элементу применяется команда <xref:Microsoft.VisualStudio.Modeling.ModelElement.Delete%2A>, вызываются методы OnDeleting и OnDeleted. Эти методы являются всегда выполнено встроенного - т. е непосредственно до и после фактического удаления. Если код удаляет два или несколько элементов, методы OnDeleting и OnDeleted применяются ко всем элементам по очереди.  
  
##  <a name="rules"></a>Правила удаления и события  
 В качестве альтернативы обработчикам OnDelete можно настроить правила и события удаления.  
  
1.  **Удаление** и **удалить** правила активируются, только в рамках транзакции, а не в отмены или повтора. Можно поместить эти правила в очередь и настроить их выполнение в конце транзакции, включающей удаление. Правила Deleting всегда выполняются перед любыми присутствующими в очереди правилами Deleted.  
  
     Используйте правила для распространения изменений, которые влияют только на элементы в хранилище, включая отношения, элементы схемы и их свойства. Обычно правило Deleting используется для распространения удаления, а правило Deleted — для создания элементов и отношений замены.  
  
     Дополнительные сведения см. в разделе [распространение изменений в модели правил](../modeling/rules-propagate-changes-within-the-model.md).  
  
2.  **Удалить** событий хранилища, вызывается в конце транзакции и вызывается после отмены или повтора. Таким образом, его можно использовать для распространения удалений на объекты за пределами хранилища, например файлы, записи баз данных или другие объекты в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
     Дополнительные сведения см. в разделе [обработчики распространение изменений за пределами модели событий](../modeling/event-handlers-propagate-changes-outside-the-model.md).  
  
    > [!WARNING]
    >  После удаления элемента можно получить доступ к его значениям свойства домена, но нельзя найти его связи отношений. Если же настроить событие Deleted на отношение, можно также получить доступ к двум элементам, которые были его исполнителями роли. Таким образом Если вы хотите ответить при удалении элемента модели, но требуется доступ к элементу, с которым он связан, задайте событие удаления в отношении вместо класса элемента модели домена.  
  
### <a name="example-deletion-rules"></a>Пример правил Deletion  
  
```  
[RuleOn(typeof(Album), FireTime = TimeToFire.TopLevelCommit)]  
internal class AlbumDeletingRule : DeletingRule  
{  
  public override void ElementDeleting(ElementDeletingEventArgs e)  
  {  
    base.ElementDeleting(e);  
    // ...perform tasks to propagate imminent deletion  
  }  
}  
[RuleOn(typeof(Album), FireTime = TimeToFire.TopLevelCommit)]  
internal class AlbumDeletedRule : DeleteRule  
{  
  public override void ElementDeleted(ElementDeletedEventArgs e)  
  {  
    base.ElementDeleted(e);  
    // ...perform tasks such as creating new elements  
  }  
}  
  
// The rule must be registered:  
public partial class MusicLibDomainModel  
{  
  protected override Type[] GetCustomDomainModelTypes()  
  {  
    List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());  
    types.Add(typeof(AlbumDeletingRule));  
    types.Add(typeof(AlbumDeletedRule));  
    // If you add more rules, list them here.   
    return types.ToArray();  
  }  
}  
  
```  
  
### <a name="example-deleted-event"></a>Пример события Deleted  
  
```  
partial class NestedShapesSampleDocData  
{  
  protected override void OnDocumentLoaded(EventArgs e)  
  {  
    base.OnDocumentLoaded(e);  
    DomainRelationshipInfo commentRelationship =   
          this.Store.DomainDataDirectory  
          .FindDomainRelationship(typeof(CommentsReferenceComponents));  
  
    this.Store.EventManagerDirectory.ElementDeleted.Add(commentRelationship,  
      new EventHandler<ElementDeletedEventArgs>(CommentLinkDeleted));  
  }  
  
  private void CommentLinkDeleted (object sender, ElementDeletedEventArgs e)  
  {  
    CommentsReferenceComponents link = e.ModelElement as CommentsReferenceComponents;  
    Comment comment = link.Comment;  
    Component component = link.Subject;  
    if (comment.IsDeleted)  
    {  
      // The link was deleted because the comment was deleted.  
      System.Windows.Forms.MessageBox.Show("Removed comment on " + component.Name);  
    }  
    else  
    {  
      // It was just the link that was deleted - the comment itself remains.  
      System.Windows.Forms.MessageBox.Show("Removed comment link to "   
           + component.Name);  
    }  
  }  
}  
  
```  
  
##  <a name="unmerge"></a>Отмена объединения  
 Операция, присоединяет дочернего элемента с родительским называется *слияния*. Она выполняется, когда новый элемент или группа элементов создаются с панели элементов, перемещаются из другой части модели или копируются из буфера обмена. Как и создание внедренного отношения между родительским и дочерним элементами, операция слияния может формировать дополнительные отношения, создавать вспомогательные элементы и задавать значения свойств в элементах. Операция слияния инкапсулируется в директиву слияния элементов (EMD).  
  
 EMD инкапсулирует дополнительный *разделите* или `MergeDisconnect` операции. Для удаления элемента из кластера, сконструированного путем слияния, с сохранением остальных элементов в согласованном состоянии рекомендуется использовать связанное разъединение. Операция разъединения обычно использует технологии, описанные в предыдущих разделах.  
  
 Дополнительные сведения см. в разделе [Настройка создания и перемещения элементов](../modeling/customizing-element-creation-and-movement.md).  
  
## <a name="see-also"></a>См. также  
 [Настройка функции копирования](../modeling/customizing-copy-behavior.md)   
 [Настройка создания и перемещения элементов](../modeling/customizing-element-creation-and-movement.md)   
 [Написание кода для настройки доменного языка](../modeling/writing-code-to-customise-a-domain-specific-language.md)