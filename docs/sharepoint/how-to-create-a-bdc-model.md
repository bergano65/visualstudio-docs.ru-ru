---
title: Как создать модель BDC | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 139da31ced1d32def450a1dc176ca241b0c4677f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "86014549"
---
# <a name="how-to-create-a-bdc-model"></a>Как создать модель BDC
  Вы можете создать модель подключения к бизнес-данным, используя шаблон для этого типа элементов, а затем добавив модель в любой проект SharePoint. Дополнительные сведения см. [в статье Создание модели подключения к бизнес-данным](../sharepoint/creating-a-business-data-connectivity-model.md). Дополнительные сведения о проектировании модели см. в разделе [проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md).

### <a name="to-create-a-bdc-project"></a>Создание проекта BDC

1. В строке меню выберите **Файл** > **Создать** > **Проект**.

    > [!NOTE]
    > Если в интегрированной среде разработки настроено использование параметров Visual Basic разработки, выберите **файл**  >  **создать проект**.

     Откроется диалоговое окно **Новый проект** .

2. В **Visual Basic** или **Visual C#** выберите **Office/SharePoint**, **решения SharePoint**.

3. В области **шаблоны** выберите **SharePoint 2013 — пустой элемент проекта** , а затем нажмите кнопку **ОК** .

     Откроется **Мастер настройки SharePoint** .

4. На странице **Укажите сайт и уровень безопасности для отладки** укажите URL-адрес сайта SharePoint на локальном компьютере, выберите параметр **Развернуть как решение фермы** , а затем нажмите кнопку **Готово** .

     Вы проверите модель на указанном сайте SharePoint.

    > [!IMPORTANT]
    > Необходимо развернуть проект как решение фермы, так как модели BDC поддерживают только решения фермы.

     Создается пустой проект SharePoint.

5. В строке меню выберите **проект**  >  **Добавить новый элемент**.

6. В диалоговом окне **Добавление нового элемента** выберите узел **Office/SharePoint** .

7. В списке шаблонов SharePoint выберите **модель подключения к бизнес-данным (только для решения фермы)**.

8. В поле **имя** укажите имя модели BDC, а затем нажмите кнопку **Добавить** .

     В проект добавляется элемент **модели подключения к бизнес-данным** . По умолчанию модель отображается в конструкторе BDC. Дополнительные сведения см. [в статье Создание модели подключения к бизнес-данным](../sharepoint/creating-a-business-data-connectivity-model.md).

## <a name="see-also"></a>См. также раздел
- [Создание модели подключения к бизнес-данным](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Как добавить существующий файл модели BDC в проект SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)
- [Как использовать файл ресурсов для указания локализованных имен, свойств и разрешений](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)
- [Как включить пользовательскую сборку в компонент BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)
- [Интеграция бизнес-данных в SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
