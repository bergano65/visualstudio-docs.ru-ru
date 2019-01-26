---
title: Как выполнить Создать модель BDC | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4d0d261b0227e024b5b4eda89b237df0c70dbd32
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2019
ms.locfileid: "54870052"
---
# <a name="how-to-create-a-bdc-model"></a>Как выполнить Создать модель BDC
  Можно создать модель бизнес-данным (BDC) с помощью шаблона для данного типа элементов и последующим добавлением модели в любой проект SharePoint. Дополнительные сведения см. в разделе [Создание модели подключения к бизнес-данным](../sharepoint/creating-a-business-data-connectivity-model.md). Дополнительные сведения о способах проектирования модели см. в разделе [проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
### <a name="to-create-a-bdc-project"></a>Создание проекта BDC  
  
1.  В строке меню выберите **Файл** > **Создать** > **Проект**.  
  
    > [!NOTE]  
    >  Если интерфейс IDE настроен на использование параметров разработки Visual Basic, выберите **файл** > **новый проект**.  
  
     Откроется диалоговое окно **Новый проект** .  
  
2.  В области **Visual Basic** или **Visual C#**, выберите **Office/SharePoint**, **решений SharePoint**.  
  
3.  В **шаблоны** панели выберите **SharePoint 2013 — пустой проект** элемента, а затем выберите **ОК** кнопки.  
  
     **Мастер настройки SharePoint** открывает.  
  
4.  На **Укажите сайт и уровень безопасности для отладки** странице укажите URL-адрес сайта SharePoint на локальном компьютере, выберите **развернуть как решение фермы** переключатель, а затем выберите **Готово** кнопки.  
  
     Вы протестируете модель на сайте SharePoint, который вы указали.  
  
    > [!IMPORTANT]  
    >  Необходимо развернуть проект как решение фермы, поскольку модели BDC поддерживают только решения фермы.  
  
     Создается пустой проект SharePoint.  
  
5.  В строке меню выберите **Проект** > **Добавить новый элемент**.  
  
6.  В **Добавление нового элемента** диалоговое окно, выберите **Office/SharePoint** узла.  
  
7.  В списке шаблонов SharePoint выберите **Business Data Connectivity Model (только для решения фермы)**.  
  
8.  В **имя** , укажите имя для модели BDC и затем выберите **добавить** кнопки.  
  
     Объект **Business Data Connectivity Model** элемент добавляется в проект. По умолчанию модель отображается в конструкторе BDC. Дополнительные сведения см. в разделе [Создание модели подключения к бизнес-данным](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
## <a name="see-also"></a>См. также
 [Создание модели подключения к бизнес-данных](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Практическое руководство. Добавление существующего файла модели BDC в проект SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)   
 [Практическое руководство. Использование файла ресурсов для задания локализованных имен, свойств и разрешений](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)   
 [Практическое руководство. Добавление пользовательской сборки в возможность BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)   
 [Интеграция бизнес-данных в SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
