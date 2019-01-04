---
title: Настройка функции удаления
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.deletebehavior
helpviewer_keywords:
- Domain-Specific Language, deletion
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: d501e182fa46adef1e0058480baa740ad7703a11
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53940957"
---
# <a name="customizing-deletion-behavior"></a>Настройка функции удаления
Удаление элемента обычно приводит также к удалению связанных элементов. Удаляются все подключенные к нему отношения и дочерние элементы. Это поведение называется *распространение удалений*. Распространение удалений можно настраивать, например, для организации удаления дополнительных связанных элементов. Написав код программы, можно сделать распространение удалений зависимым от состояния модели. Также можно в ответ на удаление вызвать другие изменения.

 Этот раздел включает следующие подразделы:

-   [Поведение удаления по умолчанию](#default)

-   [Настройка параметра распространения удалений для роли](#property)

-   [Переопределение замыкания удаления](#closure) -используйте этот метод, если удаление может привести к удалению соседних элементов.

-   [Использование методов OnDeleting и OnDeleted](#ondeleting) -использовать эти методы, в котором ответ может включать другие действия, например обновление значения внутри или за пределами хранилища.

-   [Правила удаления](#rules) — использовать правила для распространения обновлений любого типа в хранилище, где одно изменение может привести к другому.

-   [События удаления](#rules) -используйте события хранилища для распространения обновлений за пределы хранилища, например в другие документы Visual Studio.

-   [Отменить объединение](#unmerge) -используйте операцию UnMerge для отмены операции слияния, которая присоединила дочерний элемент с родительским.

## <a name="default"></a> Поведение удаления по умолчанию
 По умолчанию распространением удалений управляют следующие правила.

-   Если элемент удаляется, также все внедренные элементы удаляются. Внедренные элементы — это целевые объекты отношений внедрения, для которых этот элемент является источником. Например, если имеется отношение внедрения между **альбома** для **песни**, то при удаления альбома все входящие в него песни также будут удалены.

     При этом удаление песни не ведет к удалению альбома.

-   По умолчанию удаление не распространяется на ссылочные отношения. Если имеется отношение ссылки **ArtistPlaysOnAlbum** из **альбома** для **исполнителя**, удаление альбома не приводит к удалению ним исполнителя, а удаление исполнителя нет удалению альбома.

     При этом удаление распространяется на некоторые встроенные отношения. Например, если удаляется элемент модели, также удаляется его фигура на схеме. Элемент и фигура связаны ссылочным отношением `PresentationViewsSubject`.

-   Удаляется каждое связанное с элементом отношение в исходной или целевой роли. Свойство противоположной роли элемента больше не содержит удаленный элемент.

## <a name="property"></a> Настройка параметра распространения удалений для роли
 Распространение удаления можно вызывать по ссылочному отношению или из встроенного дочернего элемента на родительский.

#### <a name="to-set-delete-propagation"></a>Настройка распространения удаления

1. В схеме определения DSL, выберите *роли* в котором необходимо распространить удаление. Роль представлена линией слева или справа от поля доменной связи.

    Например, если требуется указать, что при удалении альбома следует удалить связанного исполнителя, выберите роль, связанную с классом домена "Исполнитель".

2. В окне «Свойства» задайте **распространение удаления** свойство.

3. Нажмите клавишу F5 и убедитесь в выполнении следующих условий.

   -   Когда удаляется экземпляр этого отношения, удаляется также элемент в выбранной роли.

   -   Когда удаляется элемент в противоположной роли, также удаляются экземпляры этого отношения и связанные элементы в этой роли.

   Также вы увидите **распространение удаления** в диалоговом окне **подробные сведения о DSL** окна. Выберите класс домена и в окне «подробные сведения о DSL» откройте **поведения при удалении** страницы, щелкнув кнопку в боковой части окна. **Propagate** отображается для противоположной роли каждого отношения. **Удалить стиль** столбец указывает ли **Propagate** параметр настройки по умолчанию, но он не имеет отдельного действия.

## <a name="delete-propagation-by-using-program-code"></a>Распространение удаления с помощью кода программы
 Только параметры в файле определения DSL позволяют выбирать, распространять ли удаление на соседние элементы. Для реализации более сложной схемы распространения удаления можно написать код программы.

> [!NOTE]
>  Чтобы добавить код программы в определении DSL, создайте отдельный файл кода в **Dsl** проекта и напишите частичные определения для дополнения классов в папку с созданным кодом. Дополнительные сведения см. в разделе [написание кода для настройки доменного языка](../modeling/writing-code-to-customise-a-domain-specific-language.md).

## <a name="closure"></a> Определение замыкания удаления
 В операции удаления используется класс _YourModel_**DeleteClosure** для определения элементов, которые нужно удалить, учитывая начальный выбор. Проходя диаграмму отношений, он циклично вызывает методы `ShouldVisitRelationship()` и `ShouldVisitRolePlayer()`. Эти методы можно переопределить. ShouldVisitRolePlayer предоставляется с удостоверением связи и элементом в одной из ролей связи. Это позволяет вернуть одно из следующих значений:

-   **VisitorFilterResult.Yes**— элемент удаляется, и обход продолжается, проверяя другие связи элемента.

-   **VisitorFilterResult.DoNotCare** -элемент не должны удаляться, если не получен ответ другого запроса, что он должен быть удален.

-   **VisitorFilterResult.Never** -элемент не должны удаляться, даже если другой запрос отвечает **Да**, а обход не должен проверять другие связи элемента.

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

## <a name="ondeleting"></a> Использование методов OnDeleting и OnDeleted
 В классе или доменной связи методы `OnDeleting()` или `OnDeleted()` переопределить нельзя.

1. <xref:Microsoft.VisualStudio.Modeling.ModelElement.OnDeleting%2A> вызывается, когда элемент сейчас будет удален, но до его отношения будут отключены. Он по-прежнему находится в `store.ElementDirectory` и допускает переход в другие или из других элементов.

    Если несколько элементов удаляются в одно и то же время, то перед выполнением этого действия для них всех вызывается метод OnDeleting.

    `IsDeleting` имеет значение true.

2. <xref:Microsoft.VisualStudio.Modeling.ModelElement.OnDeleted%2A> вызывается, когда элемент был удален. Он остается в куче CLR, чтобы при необходимости можно было выполнить отмену. При это он теряет связи от другими элементами и удаляется из `store.ElementDirectory`. Для связи роли по-прежнему ссылаются на старых исполнителей роли.`IsDeleted` имеет значение true.

3. Методы OnDeleting и OnDeleted вызываются, когда пользователь запускает операцию отмены после создания элемента, а также когда предыдущее удаление повторяется в операции повтора. В таких случаях во избежание обновления элементов хранилища используйте метод `this.Store.InUndoRedoOrRollback`. Дополнительные сведения см. в разделе [Как Использование транзакций для обновления модели](../modeling/how-to-use-transactions-to-update-the-model.md).

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

 Когда к элементу применяется команда <xref:Microsoft.VisualStudio.Modeling.ModelElement.Delete%2A>, вызываются методы OnDeleting и OnDeleted. Эти методы являются всегда выполняются встроенным образом — то есть непосредственно перед и после фактического удаления. Если код удаляет два или несколько элементов, методы OnDeleting и OnDeleted применяются ко всем элементам по очереди.

## <a name="rules"></a> Правила и события удаления
 В качестве альтернативы обработчикам OnDelete можно настроить правила и события удаления.

1.  **Удаление** и **удалить** правила будут активированы только в рамках транзакции, а не в операции отмены или повтора. Можно поместить эти правила в очередь и настроить их выполнение в конце транзакции, включающей удаление. Правила Deleting всегда выполняются перед любыми присутствующими в очереди правилами Deleted.

     Используйте правила для распространения изменений, которые влияют только на элементы в хранилище, включая отношения, элементы схемы и их свойства. Обычно правило Deleting используется для распространения удаления, а правило Deleted — для создания элементов и отношений замены.

     Дополнительные сведения см. в разделе [распространение изменений в модели правил](../modeling/rules-propagate-changes-within-the-model.md).

2.  **Удалить** как событие сохранения вызывается в конце транзакции и вызывается после отката или повтора. Таким образом, его можно использовать для распространения удалений на объекты за пределами хранилища, такие как файлы, записи в базе данных или других объектов в Visual Studio.

     Дополнительные сведения см. в разделе [обработчики распространения изменений за пределами модели событий](../modeling/event-handlers-propagate-changes-outside-the-model.md).

    > [!WARNING]
    >  После удаления элемента можно получить доступ к его значениям свойства домена, но нельзя найти его связи отношений. Если же настроить событие Deleted на отношение, можно также получить доступ к двум элементам, которые были его исполнителями роли. Таким образом Если вы хотите ответить на удаление элемента модели, но требуется доступ к элементу, к которому он был связан, настройте событие удаления на отношение, а не класс домена элемента модели.

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

## <a name="unmerge"></a> Отмена объединения
 Операция, которая вкладывает дочерний элемент с родительским называется *слияния*. Она выполняется, когда новый элемент или группа элементов создаются с панели элементов, перемещаются из другой части модели или копируются из буфера обмена. Как и создание внедренного отношения между родительским и дочерним элементами, операция слияния может формировать дополнительные отношения, создавать вспомогательные элементы и задавать значения свойств в элементах. Операция слияния инкапсулируется в директиву слияния элементов (EMD).

 EMD также инкапсулирует дополнительную *разъединения* или `MergeDisconnect` операции. Для удаления элемента из кластера, сконструированного путем слияния, с сохранением остальных элементов в согласованном состоянии рекомендуется использовать связанное разъединение. Операция разъединения обычно использует технологии, описанные в предыдущих разделах.

 Дополнительные сведения см. в разделе [Настройка создания и перемещения элементов](../modeling/customizing-element-creation-and-movement.md).

## <a name="see-also"></a>См. также

- [Настройка функции копирования](../modeling/customizing-copy-behavior.md)
- [Настройка создания и перемещения элементов](../modeling/customizing-element-creation-and-movement.md)
- [Написание кода для настройки доменного языка](../modeling/writing-code-to-customise-a-domain-specific-language.md)