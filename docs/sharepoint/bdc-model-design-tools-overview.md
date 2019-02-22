---
title: Обзор средства конструирования модели BDC | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.BDC.Method_Details
- VS.SharePointTools.BDC.Explorer
- VS.SharePointTools.BDC.Diagram
dev_langs:
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: eb2f257feaa8faa6acf58c8e8763d15d08a1079e
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56596572"
---
# <a name="bdc-model-design-tools-overview"></a>Обзор средств проектирования модели BDC
  Для разработки моделей бизнес-данным (BDC) с помощью конструктора BDC, **Подробности метода BDC** окно и **Обозреватель BDC**.

 **Обозреватель BDC** позволяет просматривать модели, поиск модели и определять дескрипторы типов.

## <a name="bdc-designer"></a>Конструктор BDC
 Конструктор BDC позволяет определять сущности в модели и визуально упорядочивать их связи друг с другом. Используйте конструктор BDC можно выполнять следующие задачи:

- Добавьте сущности в модель.

- Удаление сущностей из модели.

- Определение связей между сущностями.

  Чтобы открыть конструктор BDC, дважды щелкните файл модели в проекте или откройте контекстное меню для файла модели и выберите **откройте**. Добавление сущности в модель, перетащив или скопировав **сущности** из **элементов** в конструктор. Чтобы создать ассоциацию между двумя сущностями, выберите **ассоциации** контролировать **элементов**, выберите первую сущность, а затем выберите второй сущности.

## <a name="bdc-method-details-window"></a>Окно Подробности метода BDC
 Используйте **Подробности метода BDC** окно, чтобы определить параметры, экземпляры и дескрипторы типов метода.

 Можно быстро создать методы поиска, специальный метод поиска, создатель, обновления и удаления в **Подробности метода BDC** окна. При создании этих методов, Visual Studio добавляет метаданные, такие как параметры, экземпляры и дескрипторы типов метода. Вы можете изменить эти метаданные в соответствии с конкретным сценарием.

 Чтобы открыть **Подробности метода BDC** окно, в строке меню выберите **представление** > **Other Windows** > **Подробности метода BDC** .

 Чтобы просмотреть методы в **Подробности метода BDC** окно, выберите сущность в конструкторе BDC. Методы выбранной сущности отображаются в **Подробности метода BDC** окна. Если вы не выберете сущность в конструкторе BDC **Подробности метода BDC** окно отображает сведения отсутствуют.

 Развернуть или свернуть узлы в **Подробности метода BDC** окно, чтобы определить параметры, экземпляры и дескрипторы типов. Используйте **Обозреватель BDC** для определения дескрипторов типа.

## <a name="bdc-explorer"></a>Обозреватель BDC
 **Обозреватель BDC** отображает элементы, которые составляют модель. Чтобы открыть **Обозреватель BDC**, в строке меню выберите **представление** > **Other Windows** > **Обозреватель BDC**. Чтобы просмотреть модель, разверните узлы в **Обозреватель BDC**. Каждый узел представляет элемент в XML-файла модели.

 При выборе узлов в **Обозреватель BDC**, отобразятся свойства каждого узла, выбранного в **свойства** окна. Многие из этих свойств соответствуют атрибутам в файле модели. Модели можно найти с помощью поля поиска в верхней части **Обозреватель BDC**.

> [!NOTE]
>  **Обозреватель BDC** не отображает идентификаторы, пользовательские свойства, локализованные строки, группы ассоциаций, действий, дескрипторы фильтров, списки элементов управления действиями и значения параметров по умолчанию.

### <a name="define-type-descriptors"></a>Определение дескрипторов типов
 Используйте **Обозреватель BDC** для определения дескрипторов типа. Обозреватель BDC позволяет определить дескриптор типа один раз, а затем повторно использовать этот дескриптор типа в любом месте модели. Для этого скопируйте дескриптор типа и вставьте его в любой другой параметр или дескриптор типа.

> [!NOTE]
>  Изменение исходного дескриптора типа, не влияет на копии этого дескриптора типа.

 Дополнительные сведения см. в разделе [Как Определение дескриптора типа параметра](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

## <a name="see-also"></a>См. также
- [Практическое руководство. Создать модель BDC](../sharepoint/how-to-create-a-bdc-model.md)
- [Практическое руководство. Добавление сущности в модель](../sharepoint/how-to-add-an-entity-to-a-model.md)
- [Практическое руководство. Добавление метода Finder](../sharepoint/how-to-add-a-finder-method.md)
- [Практическое руководство. Добавление определенного метода Finder](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Практическое руководство. Добавление метода Creator](../sharepoint/how-to-add-a-creator-method.md)
- [Практическое руководство. Добавление метода Deleter](../sharepoint/how-to-add-a-deleter-method.md)
- [Практическое руководство. Добавление метода Updater](../sharepoint/how-to-add-an-updater-method.md)
- [Создание ассоциации между сущностями](../sharepoint/creating-an-association-between-entities.md)
- [Пошаговое руководство: Создание внешнего списка в SharePoint с помощью бизнес-данных](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)
- [Интеграция бизнес-данных в SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
- [Создание модели подключения к бизнес-данным](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md)
