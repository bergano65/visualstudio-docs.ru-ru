---
title: 'Как: создать модель BDC | Документы Microsoft'
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
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: aae6789d9961fa3cbf63ce073a33251465ee308a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-a-bdc-model"></a>Практическое руководство. Создание модели подключения к бизнес-данным
  Можно создать модель бизнес-данным (BDC), с помощью шаблона для этого типа элемента, а затем добавив модель в любой проект SharePoint. Дополнительные сведения см. в разделе [Создание модели подключения к бизнес-данным](../sharepoint/creating-a-business-data-connectivity-model.md). Дополнительные сведения о способах проектирования модели см. в разделе [проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### <a name="to-create-a-bdc-project"></a>Создание проекта BDC  
  
1.  В строке меню выберите **Файл**, **Создать**, **Проект**.  
  
    > [!NOTE]  
    >  Если интерфейс IDE настроен на использование параметров разработки Visual Basic, выберите **файл**, **новый проект**.  
  
     Откроется диалоговое окно **Новый проект** .  
  
2.  В рамках одного **Visual Basic** или **Visual C#**, выберите **Office/SharePoint**, **решений SharePoint**.  
  
3.  В **шаблоны** области, выберите **SharePoint 2013 — пустой проект** элемента, а затем выберите **ОК** кнопки.  
  
     **Мастер настройки SharePoint** открывается.  
  
4.  На **Укажите сайт и уровень безопасности для отладки** укажите URL-адрес сайта SharePoint на локальном компьютере, выберите **развернуть как решение фермы** переключатель, а затем выберите **Готово** кнопки.  
  
     Выполняется проверка модели на сайте SharePoint, указанном вами.  
  
    > [!IMPORTANT]  
    >  Поскольку модели BDC поддерживают только решения фермы, необходимо развернуть проект как решение фермы.  
  
     Создается пустой проект SharePoint.  
  
5.  В строке меню выберите **проекта**, **Добавление нового элемента**.  
  
6.  В **Добавление нового элемента** диалогового окна выберите **Office/SharePoint** узла.  
  
7.  В списке шаблонов SharePoint выберите **модель подключения к данным предприятия (только для решения фермы)**.  
  
8.  В **имя** , укажите имя для модели BDC и выберите **добавить** кнопки.  
  
     Объект **модель подключения к бизнес-данным** элемент добавляется в проект. По умолчанию модель отображается в конструкторе BDC. Дополнительные сведения см. в разделе [Создание модели подключения к бизнес-данным](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
## <a name="see-also"></a>См. также  
 [Создание модели подключения к бизнес-данным](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Как: Добавление существующего файла модели BDC в проект SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)   
 [Как: определить локализованные имена, свойства и разрешения с помощью файла ресурсов](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)   
 [Как: Добавление пользовательской сборки в функцию BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)   
 [Интеграция бизнес-данных в SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  