---
title: Обзор средства конструирования модели BDC | Документы Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.BDC.Method_Details
- VS.SharePointTools.BDC.Explorer
- VS.SharePointTools.BDC.Diagram
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], visual tools
- Business Data Connectivity service [SharePoint development in Visual Studio], visual tools
- Business Data Connectivity service [SharePoint development in Visual Studio], BDC Explorer
- BDC [SharePoint development in Visual Studio], method details
- Business Data Connectivity service [SharePoint development in Visual Studio], designer
- Business Data Connectivity service [SharePoint development in Visual Studio], method details
- BDC [SharePoint development in Visual Studio], BDC Explorer
- BDC [SharePoint development in Visual Studio], designer
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 088afa321e5f4026735e88c3068900b0bfc8c07c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="bdc-model-design-tools-overview"></a>Общие сведения о средствах разработки моделей подключения к бизнес-данным
  Для разработки моделей бизнес-данным (BDC) с помощью конструктора BDC **Подробности метода BDC** окна и **Обозреватель BDC**.  
  
 **Обозреватель BDC** дает возможность просматривать модель, осуществлять поиск модели и определять дескрипторы типа.  
  
## <a name="bdc-designer"></a>Конструктор BDC  
 Конструктор BDC позволяет определять сущности в модели и визуально упорядочивать их связи друг с другом. Конструктор BDC позволяет выполнять следующие задачи:  
  
-   Добавьте сущности в модели.  
  
-   Удаление сущностей из модели.  
  
-   Определение отношений между сущностями.  
  
 Чтобы открыть конструктор BDC, дважды щелкните файл модели в проекте или откройте контекстное меню для файла модели и выберите **откройте**. Добавление сущности в модель, перетащив или скопировав **сущности** из **элементов** в конструктор. Чтобы создать ассоциацию между двумя сущностями, выберите **ассоциации** управления в **элементов**, выберите первую сущность, а затем выберите две сущности.  
  
## <a name="bdc-method-details-window"></a>Окно "Подробности метода BDC"  
 Используйте **Подробности метода BDC** окна, чтобы определить параметры, экземпляры и дескрипторы фильтра для метода.  
  
 Можно быстро создать методы поиска, конкретный метод поиска, создатель, обновления и удаления в **Подробности метода BDC** окна. При создании этих методов Visual Studio добавляет метаданные, такие как параметры, экземпляры и дескрипторы типа метода. Вы можете изменить эти метаданные в соответствии с конкретным сценарием.  
  
 Чтобы открыть **Подробности метода BDC** , в строке меню выберите пункты **представление**, **другие окна**, **Подробности метода BDC**.  
  
 Чтобы просмотреть методы в **Подробности метода BDC** окно, выберите сущность в конструкторе BDC. Методы выбранной сущности отображаются в **Подробности метода BDC** окна. Если вы не выберите сущность в конструкторе BDC **Подробности метода BDC** не отобразятся никакие сведения.  
  
 Развернуть или свернуть узлы в **Подробности метода BDC** окна, чтобы определить параметры, экземпляры и дескрипторы фильтра. Используйте **Обозреватель BDC** для определения дескрипторов типа.  
  
## <a name="bdc-explorer"></a>Обозреватель BDC  
 **Обозреватель BDC** отображает элементы, которые составляют модель. Чтобы открыть **Обозреватель BDC**, в строке меню выберите **представление**, **другие окна**, **Обозреватель BDC**. Чтобы просмотреть модель, разверните узлы в **Обозреватель BDC**. Каждый узел представляет элемент в XML-файла модели.  
  
 При выборе узлов в **Обозреватель BDC**, отобразятся свойства каждого узла, выбранного в **свойства** окна. Многие из этих свойств соответствуют атрибутам в файле модели. Модели можно найти с помощью поля поиска в верхней части **Обозреватель BDC**.  
  
> [!NOTE]  
>  **Обозреватель BDC** не отображает идентификаторы, настраиваемые свойства, локализованные строки, группы ассоциаций, действия, дескрипторы фильтров, списки элементов управления действиями и значения параметров по умолчанию.  
  
### <a name="defining-type-descriptors"></a>Определение дескрипторов типов  
 Используйте **Обозреватель BDC** для определения дескрипторов типа. Обозреватель BDC позволяет определить дескриптор типа один раз, а затем повторно использовать этот дескриптор типа в любом месте модели. Для этого скопируйте дескриптор типа и вставьте его в любой другой параметр или дескриптор типа.  
  
> [!NOTE]  
>  Изменения в исходном дескрипторе типа, не влияют на копии этого дескриптора типа.  
  
 Дополнительные сведения см. в разделе [как: определение дескриптора типа параметра](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
## <a name="see-also"></a>См. также  
 [Как: создать модель BDC](../sharepoint/how-to-create-a-bdc-model.md)   
 [Как: Добавление сущности в модель](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [Как: Добавление метода Finder](../sharepoint/how-to-add-a-finder-method.md)   
 [Как: Добавление конкретного метода поиска](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Как: Добавление метода Creator](../sharepoint/how-to-add-a-creator-method.md)   
 [Как: Добавление метода Deleter](../sharepoint/how-to-add-a-deleter-method.md)   
 [Как: Добавление метода Updater](../sharepoint/how-to-add-an-updater-method.md)   
 [Создание ассоциации между сущностями](../sharepoint/creating-an-association-between-entities.md)   
 [Пошаговое руководство: Создание внешнего списка в SharePoint с помощью бизнес-данных](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)   
 [Интеграция бизнес-данным в SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)   
 [Создание модели подключения к бизнес-данным](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  