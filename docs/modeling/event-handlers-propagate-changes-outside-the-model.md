---
title: "Обработчики событий распространяют изменения за пределы модели | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, programming domain models
- Domain-Specific Language, events
ms.assetid: 0ac8d1e4-239f-4370-ba1d-3769bb38b8a5
caps.latest.revision: 18
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 3d07f82ea737449fee6dfa04a61e195654ba35fa
ms.openlocfilehash: af5fbd8973082e92f9609e335314a30eb22595fa
ms.lasthandoff: 02/22/2017

---
# <a name="event-handlers-propagate-changes-outside-the-model"></a>Обработчики событий распространяют изменения за пределы модели
В визуализации и моделирования SDK, можно определить обработчики событий хранилища для распространения изменений к ресурсам за пределами хранилища, такие как переменные вне хранилища, файлы моделей в другие хранилища или других [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] расширения. После завершения транзакции, в которой произошло событие, запускающее обработчики событий хранилища. Они также выполняются в операции отмены или повтора. Таким образом в отличие от сохранить правила событий хранилища наиболее полезны для обновления значения, которые находятся за пределами хранилища. В отличие от событий .NET зарегистрированных обработчиков событий в хранилище для прослушивания класс: необходимо зарегистрировать отдельный обработчик для каждого экземпляра. Дополнительные сведения о том, как выбрать различные способы обработки изменений см. в разделе [распространение изменений и реагирование на](../modeling/responding-to-and-propagating-changes.md).  
  
 Область графического и другие элементы управления пользовательского интерфейса являются примерами внешних ресурсов, которые могут быть обработаны событий хранилища.  
  
### <a name="to-define-a-store-event"></a>Чтобы определить событие хранения  
  
1.  Выберите тип события, которое требуется отслеживать. Полный список просмотрите свойства <xref:Microsoft.VisualStudio.Modeling.EventManagerDirectory>.</xref:Microsoft.VisualStudio.Modeling.EventManagerDirectory> Каждое свойство соответствует типу события. Наиболее часто используемые типы событий:  
  
    -   `ElementAdded`— запускается при элемента модели, связи, фигуру или соединитель создается.  
  
    -   ElementPropertyChanged — инициируется при значение `Normal` изменить свойства домена. Событие происходит только в том случае, если старое и новое значения не равны. Это событие не может применяться к вычисляемые и пользовательские свойства хранилища.  
  
         Он не может применяться к свойствам роли, которые соответствуют связи отношений. Вместо этого используйте `ElementAdded` отслеживать отношения между доменом.  
  
    -   `ElementDeleted`— создается после элемента модели, отношения, фигуры или соединителя был удален. Значения свойств элемента можно получить доступ, но у него будет ни одной связи с другими элементами.  
  
2.  Добавьте определение разделяемого класса для *YourDsl***DocData** в отдельном файле кода в **DslPackage** проекта.  
  
3.  Напишите код события как метод, как показано в следующем примере. Он может быть `static`, если не требуется доступ к `DocData`.  
  
4.  Переопределение `OnDocumentLoaded()` для регистрации обработчика. Если у вас есть несколько обработчиков, их можно зарегистрировать в одном месте.  
  
 Расположение кода регистрации не является обязательным. `DocView.LoadView()`является альтернативное расположение.  
  
```  
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
      base.OnDocumentLoaded(); // Don’t forget this.  
  
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
  
## <a name="using-events-to-make-undoable-adjustments-in-the-store"></a>С помощью событий отменяемой корректировки в хранилище  
 События хранилища не используются обычно для распространения изменений внутри хранилища, так как обработчик событий выполняется после фиксации транзакции. Вместо этого используется правило хранилища. Дополнительные сведения см. в разделе [распространение изменений в модели правил](../modeling/rules-propagate-changes-within-the-model.md).  
  
 Однако можно использовать обработчик событий вносить дополнительные обновления в хранилище, если требуется, чтобы пользователь имел возможность отменить дополнительные обновления отдельно от исходного события. Например предположим, что буквы в нижнем регистре обычных соглашений по альбомов. Можно написать обработчик событий хранилища, который исправляет заголовок, нижний регистр после пользователь ввел его в верхний регистр. Однако пользователь может использовать команду отмены для отмены вашей исправления восстановление символы верхнего регистра. Изменение пользователя удалить второй отмены.  
  
 Напротив Если написал правило хранилища, чтобы сделать то же самое, изменение пользователя и что исправления внесены будет в той же транзакции, таким образом, чтобы пользователю не удается отменить корректировку без потери исходного изменения.  
  
```  
  
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
  
 Если вы пишете событие, которое обновляет хранилище:  
  
-   Используйте `store.InUndoRedoOrRollback` во избежание внесения изменений с элементами модели в отмены. Диспетчер транзакций настроит все в хранилище обратно в исходное состояние.  
  
-   Используйте `store.InSerializationTransaction` во избежание внесения изменений во время загрузки модели из файла.  
  
-   Эти изменения приведут дальнейшей событий срабатывания триггера. Убедитесь, что позволяет избежать бесконечного цикла.  
  
## <a name="store-event-types"></a>Типы событий хранилища  
 Каждый тип событий соответствует коллекции в Store.EventManagerDirectory. Можно добавить или удалить обработчики событий в любое время, но обычно создаются путем их добавления при загрузке документа.  
  
|`EventManagerDirectory`Имя свойства|При выполнении|  
|-------------------------------------------|-------------------|  
|ElementAdded|Создать экземпляр класса домена, отношения между доменом, фигуры, соединителя или схемы.|  
|ElementDeleted|Элемент модели был удален из каталога элемент магазина и больше не является источником или целевой связи. Элемент фактически не удаляется из памяти, но сохраняется в случае будущих отмены.|  
|ElementEventsBegun|Вызывается в конце внешней транзакции.|  
|ElementEventsEnded|Вызывается, когда все события будут обработаны.|  
|ElementMoved|Элемент модели был перемещен из одного хранилища секции в другую.<br /><br /> Это не связано с расположением фигуры на схеме.|  
|ElementPropertyChanged|Изменилось значение свойства домена. Это выполняется только в том случае, если старое и новое значения не равны.|  
|RolePlayerChanged|Один из двух ролей (заканчивается) связи ссылается на новый элемент.|  
|RolePlayerOrderChanged|В роли с кратностью больше 1 порядковый номер ссылки был изменен.|  
|TransactionBeginning||  
|TransactionCommitted||  
|TransactionRolledBack||  
  
## <a name="see-also"></a>См. также  
 [Реагирование на изменения и их распространение](../modeling/responding-to-and-propagating-changes.md)   
 [Пример кода: принципиальной схемы](http://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)
 
[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
 

