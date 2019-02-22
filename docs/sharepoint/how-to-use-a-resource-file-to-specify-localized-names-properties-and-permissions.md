---
title: Практическое руководство. Использование файла ресурсов для задания локализованных имен, свойств и разрешений | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], localize strings
- BDC [SharePoint development in Visual Studio], localize strings
- BDC [SharePoint development in Visual Studio], resource file
- Business Data Connectivity service [SharePoint development in Visual Studio], resource strings
- BDC [SharePoint development in Visual Studio], properties
- Business Data Connectivity service [SharePoint development in Visual Studio], properties
- Business Data Connectivity service [SharePoint development in Visual Studio], resource file
- BDC [SharePoint development in Visual Studio], resource strings
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9014b344e030f3763037395f5fb96d446c0132f0
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56621556"
---
# <a name="how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions"></a>Практическое руководство. Использование файла ресурсов для задания локализованных имен, свойств и разрешений
  С помощью файла ресурсов можно предоставлять локализованные имена, определять свойства и применять разрешения к объектам, определенным в модели подключения к бизнес-данным (BDC). Чтобы задать эти сведения, добавьте **ресурса подключения к бизнес-данным** элемента в проект, содержащий **Business Data Connectivity Model** элемента. Затем задайте имена, свойства и разрешения, редактируя XML-код для файла ресурсов.

### <a name="to-add-a-bdc-resource-file-to-a-sharepoint-project"></a>Чтобы добавить файл ресурсов каталога бизнес-данных в проект SharePoint

1.  В **обозревателе решений**, разверните папку проекта SharePoint и затем выберите папку, содержащую модель BDC.

2.  В строке меню выберите **Проект** > **Добавить новый элемент**.

3.  Разверните **SharePoint** узел, а затем выберите **2010** узла.

4.  В **Добавление нового элемента** диалоговом окне выберите **элемент ресурса подключения к бизнес-данным**.

5.  В **имя** , укажите имя файла ресурсов и затем выберите **добавить** кнопки.

     Файл ресурсов с расширением .bdcr добавляется в проект и открывается для редактирования.

6.  Добавьте XML-код, чтобы определить локализованные имена, свойства и разрешения, которые необходимо применить к модели подключения к бизнес-данным.

     Сведения об определении этих элементов см. в разделе [ресурсов файлов модели и](http://go.microsoft.com/fwlink/?LinkID=169283).

## <a name="see-also"></a>См. также
- [Практическое руководство. Добавление существующего файла модели BDC в проект SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)
- [Создание модели подключения к бизнес-данных](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Практическое руководство. Создать модель BDC](../sharepoint/how-to-create-a-bdc-model.md)
- [Практическое руководство. Добавление пользовательской сборки в возможность BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)
- [Интеграция бизнес-данных в SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
