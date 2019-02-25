---
title: Практическое руководство. Создать модель BDC | Документация Майкрософт
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
ms.openlocfilehash: d82678df0da5932dd33c08a6e3066462df204f6e
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56596507"
---
# <a name="how-to-create-a-bdc-model"></a>Практическое руководство. Создать модель BDC
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
- [Создание модели подключения к бизнес-данных](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Практическое руководство. Добавление существующего файла модели BDC в проект SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)
- [Практическое руководство. Использование файла ресурсов для задания локализованных имен, свойств и разрешений](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)
- [Практическое руководство. Добавление пользовательской сборки в возможность BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)
- [Интеграция бизнес-данных в SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
