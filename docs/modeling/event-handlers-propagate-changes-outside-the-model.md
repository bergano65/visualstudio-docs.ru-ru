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
caps.latest.revision: "18"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 29c8594b80c55eb000d70f05d35bbf28becb6e26
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="event-handlers-propagate-changes-outside-the-model"></a>Обработчики событий распространяют изменения за пределы модели
В визуализации и моделирования SDK, можно указать обработчики событий хранилища для распространения изменений к ресурсам за пределами магазина, таких как переменные без хранилища, файлы моделей в других хранилищах или в других [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] расширения. Обработчики событий в хранилище, выполняются после завершения транзакции, в которой произошло событие триггера. Кроме того, они выполняются в операции отмены или повтора. Таким образом в отличие от сохранить правила событий хранилища наиболее полезны для обновления значений, которые находятся за пределами хранилища. В отличие от событий .NET зарегистрированных обработчиков событий в хранилище для прослушивания класс: необходимо зарегистрировать отдельный обработчик для каждого экземпляра. Дополнительные сведения о выборе между различными способами обработки изменений см. в разделе [распространение изменений и реагирование на](../modeling/responding-to-and-propagating-changes.md).  
  
 Поверхность графический и другие элементы управления пользовательского интерфейса являются примерами внешние ресурсы, которые можно обрабатывать события хранилища.  
  
### <a name="to-define-a-store-event"></a>Определение события хранилища  
  
1.  Выберите тип события, которое требуется отслеживать. Полный список, просмотрите свойства <xref:Microsoft.VisualStudio.Modeling.EventManagerDirectory>. Каждое свойство соответствует типу события. Наиболее часто используемые типы событий:  
  
    -   `ElementAdded`-запускается при элемента модели, связи, фигуры или соединителя создается.  
  
    -   ElementPropertyChanged - инициируется при значение `Normal` изменить свойства домена. Событие происходит только в том случае, если старое и новое значения не равны. Это событие не может применяться к вычисляемые и пользовательские свойства хранилища.  
  
         Он не может применяться к свойствам роли, соответствующих связей. Вместо этого используйте `ElementAdded` для мониторинга связи домена.  
  
    -   `ElementDeleted`-активируемые после элемента модели, связи, фигуры или соединителя был удален. Значения свойств элемента по-прежнему можно использовать, но он будет иметь ни одной связи с другими элементами.  
  
2.  Добавьте определение разделяемого класса для *YourDsl***DocData** в отдельном файле кода в **DslPackage** проекта.  
  
3.  Напишите код события как метод, как показано в следующем примере. Это может быть `static`, если не требуется получить доступ к `DocData`.  
  
4.  Переопределить `OnDocumentLoaded()` для регистрации обработчика. Если у вас есть несколько обработчиков, их можно зарегистрировать в одном месте.  
  
 Расположение кода регистрации не является обязательным. `DocView.LoadView()`Представляет альтернативное расположение.  
  
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
  
## <a name="using-events-to-make-undoable-adjustments-in-the-store"></a>С помощью событий для корректировки отменяемой в хранилище  
 События хранилища не используются обычно для распространения изменений в хранилище, так как обработчик событий выполняется после фиксации транзакции. Вместо этого используется правило хранилища. Дополнительные сведения см. в разделе [распространение изменений в модели правил](../modeling/rules-propagate-changes-within-the-model.md).  
  
 Тем не менее можно использовать обработчик событий для выполнения дополнительных обновлений в хранилище, если пользователю необходимо иметь возможность отменить дополнительные обновления отдельно от исходного события. Например предположим, что буквы в нижнем регистре обычных соглашений по альбомам. Можно написать обработчик событий хранилища, которое исправляет заголовок в нижний регистр после пользователь ввел его в верхнем регистре. Однако пользователь может использовать команду отмены для отмены вашей исправления восстановление буквы в верхнем регистре. Второй отмены удаляется, изменение пользователя.  
  
 Напротив, создав правило хранилища, чтобы сделать то же самое изменение пользователя и вашей исправления будут находиться в той же транзакции, чтобы пользователю не удается отменить корректировку без потери исходного изменения.  
  
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
  
 При написании событие, которое обновляет хранилище:  
  
-   Используйте `store.InUndoRedoOrRollback` избежание внесения изменений с элементами модели в отмены. Диспетчер транзакций будет устанавливать все данные в хранилище обратно в исходное состояние.  
  
-   Используйте `store.InSerializationTransaction` избежание внесения изменений во время загрузки модели из файла.  
  
-   Эти изменения приведут дополнительные события, которые будут выполнены. Убедитесь, что позволяет избежать бесконечный цикл.  
  
## <a name="store-event-types"></a>Типы событий в хранилище  
 В коллекцию в Store.EventManagerDirectory соответствует каждого типа события. Можно добавить или удалить обработчики событий в любое время, но обычно создаются путем их добавления при загрузке документа.  
  
|`EventManagerDirectory`Имя свойства|При выполнении|  
|-------------------------------------------|-------------------|  
|ElementAdded|Создается экземпляр класса домена, доменной связи, фигуры, соединителя или схемы.|  
|ElementDeleted|Элемент модели был удален из каталога элемент магазина и больше не является источником или назначением ни одной связи. Элемент фактически не удаляется из памяти, но сохраняется в случае будущих отмены.|  
|ElementEventsBegun|Вызывается в конце внешней транзакции.|  
|ElementEventsEnded|Вызывается, когда все события будут обработаны.|  
|ElementMoved|Элемент модели была перемещена из секции одного хранилища в другое.<br /><br /> Не относится к расположению фигуре на схеме.|  
|ElementPropertyChanged|Изменилось значение свойства домена. Это выполняется только в том случае, если старое и новое значения не равны.|  
|RolePlayerChanged|Один из двух ролей (концов) отношений ссылается на новый элемент.|  
|RolePlayerOrderChanged|В роли с кратностью больше 1 порядковый номер ссылки был изменен.|  
|TransactionBeginning||  
|TransactionCommitted||  
|TransactionRolledBack||  
  
## <a name="see-also"></a>См. также  
 [Реагирование на изменения и их распространение](../modeling/responding-to-and-propagating-changes.md)   
 [Пример кода: схемы канала](http://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)
 
[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
 
