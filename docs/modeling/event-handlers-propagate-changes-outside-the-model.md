---
title: Обработчики событий распространяют изменения за пределы модели
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
- Domain-Specific Language, events
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: eb9fb268ec98d60dcea46a8802592261493e4b56
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/05/2018
ms.locfileid: "43776175"
---
# <a name="event-handlers-propagate-changes-outside-the-model"></a>Обработчики событий распространяют изменения за пределы модели

Возможности визуализации и моделирования SDK, можно определить обработчики событий хранилища для распространения изменений к ресурсам за пределами хранилища, такие как переменные вне хранилища, файлы, моделей в другие хранилища или других [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] расширения. Обработчики событий Store, выполняются в конце транзакции, в которой произошло событие триггера. Кроме того, они выполняются в операции отмены или повтора. Таким образом в отличие от хранилища, события хранилища удобнее всего использовать для обновления значения, которые находятся за пределами хранилища. В отличие от событий .NET, обработчики событий хранилища зарегистрированного для прослушивания класса: у вас нет регистрируемый отдельный обработчик для каждого экземпляра. Дополнительные сведения о выборе между различных способов обработки изменений см. в разделе [реагирование на события и распространение изменений](../modeling/responding-to-and-propagating-changes.md).

Графическая поверхность и другие элементы управления пользовательского интерфейса являются примерами внешних ресурсов, которые можно обрабатывать события хранилища.

### <a name="to-define-a-store-event"></a>Чтобы определить событие хранения

1.  Выберите тип события, которое вы хотите отслеживать. Полный список, просмотрите свойства <xref:Microsoft.VisualStudio.Modeling.EventManagerDirectory>. Каждое свойство соответствует типу события. Наиболее часто используемые типы событий:

    -   `ElementAdded` -активации, если элемент модели, ссылка отношения, фигуры или соединителя создается.

    -   ElementPropertyChanged - активируется, когда значение `Normal` свойства домена изменяется. Событие срабатывает, только в том случае, если старое и новое значения не равны. Это событие не может использоваться для хранения вычисляемые и пользовательские свойства.

         Он не может применяться к свойствам роли, которые соответствуют связи отношений. Вместо этого используйте `ElementAdded` для наблюдения за доменной связи.

    -   `ElementDeleted` -активировано после элемента модели, отношения, фигуры или соединителя был удален. Значения свойств элемента по-прежнему доступны, но будет иметь ни одной связи с другими элементами.

2.  Добавьте определение разделяемого класса для _YourDsl_**DocData** в отдельном файле кода в **DslPackage** проекта.

3.  Напишите код события, как метод, как показано в следующем примере. Это может быть `static`, только если вы хотите получить доступ к `DocData`.

4.  Переопределить `OnDocumentLoaded()` для регистрации обработчика. Если у вас есть несколько обработчиков, их можно зарегистрировать в одном месте.

Расположение кода регистрации не является обязательным. `DocView.LoadView()` — это альтернативное расположение.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using Microsoft.VisualStudio.Modeling;

namespace Company.MusicLib
{
  partial class MusicLibDocData
  {
    // Register store events here or in DocView.LoadView().
    protected override void OnDocumentLoaded()
    {
      base.OnDocumentLoaded(); // Don't forget this.

      #region Store event handler registration.
      Store store = this.Store;
      EventManagerDirectory emd = store.EventManagerDirectory;
      DomainRelationshipInfo linkInfo = store.DomainDataDirectory
          .FindDomainRelationship(typeof(ArtistAppearsInAlbum));
      emd.ElementAdded.Add(linkInfo,
          new EventHandler<ElementAddedEventArgs>(AddLink));
      emd.ElementDeleted.Add(linkInfo,
          new EventHandler<ElementDeletedEventArgs>(RemoveLink));

      #endregion Store event handlers.
    }

    private void AddLink(object sender, ElementAddedEventArgs e)
    {
      ArtistAppearsInAlbum link = e.ModelElement as ArtistAppearsInAlbum;
      if (link != null)
            ExternalDatabase.Add(link.Artist.Name, link.Album.Title);
    }
    private void RemoveLink(object sender, ElementDeletedEventArgs e)
    {
      ArtistAppearsInAlbum link = e.ModelElement as ArtistAppearsInAlbum;
      if (link != null)
            ExternalDatabase.Delete(link.Artist.Name, link.Album.Title);
    }
  }
}
```

## <a name="use-events-to-make-undoable-adjustments-in-the-store"></a>События используются для корректировки отменяемой в Store

Store события не используются обычно для распространения изменений в хранилище, так как обработчик событий выполняет после фиксации транзакции. Вместо этого используется правило хранилища. Дополнительные сведения см. в разделе [распространение изменений в модели правил](../modeling/rules-propagate-changes-within-the-model.md).

Тем не менее можно использовать обработчик событий для дополнительные обновления в хранилище, если пользователю необходимо иметь возможность отменить дополнительные обновления отдельно от исходного события. Например предположим, что символы в нижнем регистре обычных соглашений по альбомов. Можно написать обработчик событий хранилища, который исправляет заголовок в нижний регистр после введенное пользователем его в верхний регистр. Но пользователь может использовать команду отмены для отмены что изменения внесены, восстановление символы в верхнем регистре. Изменение пользователя удалить второй отмены.

Напротив Если вы создали правило хранилища, чтобы сделать то же самое, изменение пользователя и что изменения внесены будет в той же транзакции, таким образом, чтобы пользователю не удалось отменить корректировки без потери исходного изменения.

```csharp
partial class MusicLibDocView
{
    // Register store events here or in DocData.OnDocumentLoaded().
    protected override void LoadView()
    {
      /* Register store event handler for Album Title property. */
      // Get reflection data for property:
      DomainPropertyInfo propertyInfo =
        this.DocData.Store.DomainDataDirectory
        .FindDomainProperty(Album.TitleDomainPropertyId);
      // Add to property handler list:
      this.DocData.Store.EventManagerDirectory
        .ElementPropertyChanged.Add(propertyInfo,
        new EventHandler<ElementPropertyChangedEventArgs>
             (AlbumTitleAdjuster));

      /*
      // Alternatively, you can set one handler for
      // all properties of a class.
      // Your handler has to determine which property changed.
      DomainClassInfo classInfo = this.Store.DomainDataDirectory
           .FindDomainClass(typeof(Album));
      this.Store.EventManagerDirectory
          .ElementPropertyChanged.Add(classInfo,
        new EventHandler<ElementPropertyChangedEventArgs>
             (AlbumTitleAdjuster));
       */
      return base.LoadView();
    }

// Undoable adjustment after a property is changed.
// Method can be static since no local access.
private static void AlbumTitleAdjuster(object sender,
         ElementPropertyChangedEventArgs e)
{
  Album album = e.ModelElement as Album;
  Store store = album.Store;

  // We mustn't update the store in an Undo:
  if (store.InUndoRedoOrRollback
      || store.InSerializationTransaction)
      return;

  if (e.DomainProperty.Id == Album.TitleDomainPropertyId)
  {
    string newValue = (string)e.NewValue;
    string lowerCase = newValue.ToLowerInvariant();
    if (!newValue.Equals(lowerCase))
    {
      using (Transaction t = store.TransactionManager
            .BeginTransaction("adjust album title"))
      {
        album.Title = lowerCase;
        t.Commit();
      } // Beware! This could trigger the event again.
    }
  }
  // else other properties of this class.
}
```

Если вы создаете событие, которое обновляет хранилище:

-   Используйте `store.InUndoRedoOrRollback` избежание внесения изменений с элементами модели в отмены. Диспетчер транзакций установит все, что в хранилище обратно в исходное состояние.

-   Используйте `store.InSerializationTransaction` избежание внесения изменений в модели во время загрузки из файла.

-   Изменения будут приведут к получению события будут активироваться. Убедитесь, что вам избежать бесконечного цикла.

## <a name="store-event-types"></a>Типы событий Store

В коллекцию в Store.EventManagerDirectory соответствует каждого типа события. Можно добавить или удалить обработчики событий в любое время, но обычно добавляются при загрузке документа.

|`EventManagerDirectory` Имя свойства|Выполняется при|
|-------------------------------------------|-------------------|
|ElementAdded|Создать экземпляр класса домена, доменного отношения, фигуры, соединителя или схемы.|
|ElementDeleted|Элемент модели был удален из каталога элемент магазина и больше не является источником или целевой по связи. Элемент фактически не удаляется из памяти, но сохраняется в случае будущих отмены.|
|ElementEventsBegun|Вызывается в конце внешней транзакции.|
|ElementEventsEnded|Вызывается, когда все остальные события будут обработаны.|
|ElementMoved|Элемент модели был перемещен из одного хранилища секции в другую.<br /><br /> Это не связано с расположение фигур на схеме.|
|ElementPropertyChanged|Значение свойства домена изменилось. Это выполняется только в том случае, если старое и новое значения не равны.|
|RolePlayerChanged|Один из двух ролей (концов) отношения ссылается на новый элемент.|
|RolePlayerOrderChanged|В роли с кратностью больше 1 порядковый номер ссылки был изменен.|
|TransactionBeginning||
|TransactionCommitted||
|TransactionRolledBack||

## <a name="see-also"></a>См. также

- [Реагирование на изменения и их распространение](../modeling/responding-to-and-propagating-changes.md)
- [Пример кода: пример принципиальной схемы](http://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]