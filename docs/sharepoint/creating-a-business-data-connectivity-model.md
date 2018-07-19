---
title: Создание Business Data Connectivity Model | Документация Майкрософт
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], model
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
- SharePoint development in Visual Studio, Business Data Connectivity service
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b8d76c6f7d28b990d133780c25577cab4e8c3cad
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/22/2018
ms.locfileid: "36326038"
---
# <a name="create-a-business-data-connectivity-model"></a>Создание модели подключения к бизнес-данных
  Можно создать модель бизнес-данным (BDC) или настроить существующую модель BDC с помощью Visual Studio. Каждый проект SharePoint может содержать только одну модель. Дополнительные сведения см. в разделе [интегрировать бизнес-данные в SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md).  
  
## <a name="create-a-new-model"></a>Создание новой модели
 Чтобы создать новую модель, создайте **Business Data Connectivity Model** проекта или добавить **Business Data Connectivity Model** элемент **Empty SharePoint Project**.  
  
> [!NOTE]  
>  Необходимо иметь [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] установлен на компьютере.  
  
 Visual Studio добавляет папку в проект. Эта папка имеет имя, указанное для **Business Data Connectivity Model** элемент **Добавление нового элемента** диалоговое окно. Если вы создаете новый **Business Data Connectivity Model** проекта, Visual Studio присваивает папке **BdcModel1**.  
  
 Visual Studio добавляет следующие файлы в новую папку.  
  
|Файл|Описание:|  
|----------|-----------------|  
|Файл определения модели|Содержит XML-код, который определяет сущности, методы, объекты строки из БИЗНЕС-системы и другие метаданные, описывающие модель.<br /><br /> Изменения метаданных в этот файл в конструкторе BDC **Обозреватель BDC**, **Подробности метода BDC** окно, и **свойства** окна.|  
|Файл кода службы сущности|Содержит методы, получение, обновление и удаление экземпляров сущности по умолчанию.|  
  
 Чтобы определить свойства сущности, измените файл кода сущности. Дополнительные сведения см. в разделе [как: Добавление сущности в модель](../sharepoint/how-to-add-an-entity-to-a-model.md).  
  
 Для получения, обновления и удаления экземпляров сущности, добавьте код в файл кода службы сущности. Дополнительные сведения см. в разделе [проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
 При компиляции проекта Visual Studio создает сборку. Убедитесь, что другие элементы не добавлены в проект, добавьте код в сборку проекта (например: **последовательный рабочий процесс** элемента или **веб-часть** элемента). Код для этого элемента не будет выполняться при развертывании решения, поскольку пакет решения не копирует сборку в глобальный кэш сборок.  Пакет решения выполняет развертывание сборки BDC только к базе данных в SharePoint.  
  
> [!NOTE]  
>  Visual Studio копирует сборку в оба расположения на локальном компьютере, при отладке проекта.  
  
## <a name="add-an-existing-model"></a>Добавить существующую модель
 Вы можете импортировать модель, которая была создана с помощью других средств, таких как SharePoint Designer. Можно выбрать для импорта существующей модели в проект, в следующих ситуациях:  
  
-   Чтобы настроить модель, которая уже развернута на ферме серверов SharePoint.  
  
-   Для упаковки и развертывания существующей модели на нескольких фермах серверов SharePoint.  
  
 В любом случае бизнес-системам, определенные в модели, импортируемые не затрагиваются и будут продолжать работать должным образом. Чтобы добавить существующую модель в проект SharePoint, используйте Visual Studio **добавить существующий элемент** диалоговое окно. Дополнительные сведения см. в разделе [как: Добавление существующего файла модели BDC в проект SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md).  
  
 Можно добавить бизнес-систему типа сборки .NET Framework для импортированной модели, выбрав один из вариантов в **бизнес-системы сборки .NET, добавьте**. Это позволяет создавать пользовательский код и использовать конструктор для определения метаданных для импортированной модели.  
  
## <a name="related-topics"></a>См. также
  
|Заголовок|Описание:|  
|-----------|-----------------|  
|[Практическое: создать модель BDC](../sharepoint/how-to-create-a-bdc-model.md)|Показано, как создать новую модель BDC.|  
|[Практическое: Добавление существующего файла модели BDC в проект SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)|Показано, как для импорта существующей модели в проект SharePoint.|  
|[Практическое: использование файла ресурсов для задания локализованных имен, свойств и разрешений](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)|Содержит сведения о предоставлении строки, которые объединяются с метаданными модели, при использовании модели веб-части или веб-страницы.|  
|[Практическое: Добавление пользовательской сборки в возможность BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)|Показано, как добавление пользовательской сборки в функцию.|  
  
 
