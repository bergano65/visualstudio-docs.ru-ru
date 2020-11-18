---
title: Обзор средств проектирования моделей BDC | Документация Майкрософт
description: Ознакомьтесь с обзором средств проектирования для использования с моделью подключения к бизнес-данным (BDC). Сведения о конструкторе BDC, окне "сведения о методе BDC" и в обозревателе BDC.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: b6e78b6809d3136c0db1f558d175706dc0ecd75b
ms.sourcegitcommit: ad2c820b280b523a7f7aef89742cdb719354748f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2020
ms.locfileid: "94850317"
---
# <a name="bdc-model-design-tools-overview"></a>Обзор средств проектирования моделей BDC
  Модель подключения к бизнес-данным можно спроектировать с помощью конструктора BDC, окна " **сведения о методе BDC** " и **обозревателя BDC**.

 **Обозреватель BDC** позволяет просматривать модель, выполнять поиск по модели и определять дескрипторы типов.

## <a name="bdc-designer"></a>Конструктор BDC
 Конструктор BDC позволяет определять сущности в модели и визуально упорядочивать их связи друг с другом. Используйте конструктор BDC для выполнения следующих задач:

- Добавление сущностей в модель.

- Удалите сущности из модели.

- Определение связей между сущностями.

  Чтобы открыть конструктор BDC, дважды щелкните файл модели в проекте или откройте контекстное меню для файла модели и выберите **Открыть**. Добавьте сущность в модель, перетащив или скопировав **сущность** из **панели элементов** в конструктор. Чтобы создать ассоциацию между двумя сущностями, выберите элемент управления **взаимосвязь** на **панели элементов**, выберите первую сущность, а затем выберите вторую сущность.

## <a name="bdc-method-details-window"></a>Окно сведений о методе BDC
 Используйте окно **сведения о методе BDC** , чтобы определить параметры, экземпляры и дескрипторы фильтра метода.

 В окне **сведения о методе BDC** можно быстро создать методы поиска, средства поиска, создателя, обновления и удаления. При создании этих методов Visual Studio добавляет в метод метаданные, такие как параметры, экземпляры и дескрипторы типа. Эти метаданные можно изменить в соответствии с конкретным сценарием.

 Чтобы открыть окно **сведения о методе BDC** , в строке меню выберите **Просмотреть**  >  **другие**  >  **сведения о методе BDC** Windows.

 Чтобы просмотреть методы в окне **сведения о методе BDC** , выберите сущность в конструкторе BDC. Методы выбранной сущности отображаются в окне **сведения о методе BDC** . Если вы не выбираете сущность в конструкторе BDC, в окне **сведения о методе BDC** не отображаются сведения.

 Разверните или сверните узлы в окне **сведения о методе BDC** , чтобы определить параметры, экземпляры и дескрипторы фильтра. Используйте **Обозреватель BDC** для определения дескрипторов типов.

## <a name="bdc-explorer"></a>Обозреватель BDC
 В **обозревателе BDC** отображаются элементы, составляющие модель. Чтобы открыть **Обозреватель BDC**, в строке меню выберите пункт **Просмотреть**  >  **другой**  >  **проводник Windows BDC**. Для просмотра модели разверните узел узлы в **обозревателе BDC**. Каждый узел представляет элемент в XML-файле модели.

 При выборе узлов в **обозревателе BDC** свойства каждого выбранного узла отображаются в окне **свойства** . Многие из этих свойств соответствуют атрибутам в файле модели. Для поиска в модели можно использовать поле поиска в верхней части **обозревателя BDC**.

> [!NOTE]
> В **обозревателе BDC** не отображаются идентификаторы, пользовательские свойства, локализованные строки, группы взаимосвязей, действия, дескрипторы фильтров, списки управления действиями и значения параметров по умолчанию.

### <a name="define-type-descriptors"></a>Определение дескрипторов типов
 Используйте **Обозреватель BDC** для определения дескрипторов типов. Обозреватель BDC позволяет определить дескриптор типа один раз, а затем повторно использовать этот дескриптор типа в любом расположении в модели. Чтобы сделать это, скопируйте дескриптор типа и вставьте его в любой другой параметр или дескриптор типа.

> [!NOTE]
> Изменения в исходном дескрипторе типа не влияют на копии этого дескриптора типа.

 Дополнительные сведения см. [в разделе инструкции. определение дескриптора типа параметра](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

## <a name="see-also"></a>См. также статью
- [Практическое руководство. Создание модели подключения к бизнес-данным](../sharepoint/how-to-create-a-bdc-model.md)
- [Как добавить сущность в модель](../sharepoint/how-to-add-an-entity-to-a-model.md)
- [Как добавить метод Finder](../sharepoint/how-to-add-a-finder-method.md)
- [Как добавить конкретный метод поиска](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Как добавить метод Creator](../sharepoint/how-to-add-a-creator-method.md)
- [Как добавить метод удаления](../sharepoint/how-to-add-a-deleter-method.md)
- [Как добавить метод обновления](../sharepoint/how-to-add-an-updater-method.md)
- [Создание связи между сущностями](../sharepoint/creating-an-association-between-entities.md)
- [Пошаговое руководство. Создание внешнего списка в SharePoint с помощью бизнес-данных](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)
- [Интеграция бизнес-данных в SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
- [Создание модели подключения к бизнес-данным](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md)
