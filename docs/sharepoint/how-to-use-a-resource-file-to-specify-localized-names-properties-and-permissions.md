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
ms.openlocfilehash: 2be88a29d3e9e3da9d1963aa1226ffca0a0a2bbd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62813053"
---
# <a name="how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions"></a>Практическое руководство. Использование файла ресурсов для задания локализованных имен, свойств и разрешений
  С помощью файла ресурсов можно предоставлять локализованные имена, определять свойства и применять разрешения к объектам, определенным в модели подключения к бизнес-данным (BDC). Чтобы задать эти сведения, добавьте **ресурса подключения к бизнес-данным** элемента в проект, содержащий **Business Data Connectivity Model** элемента. Затем задайте имена, свойства и разрешения, редактируя XML-код для файла ресурсов.

### <a name="to-add-a-bdc-resource-file-to-a-sharepoint-project"></a>Чтобы добавить файл ресурсов каталога бизнес-данных в проект SharePoint

1. В **обозревателе решений**, разверните папку проекта SharePoint и затем выберите папку, содержащую модель BDC.

2. В строке меню выберите **Проект** > **Добавить новый элемент**.

3. Разверните **SharePoint** узел, а затем выберите **2010** узла.

4. В **Добавление нового элемента** диалоговом окне выберите **элемент ресурса подключения к бизнес-данным**.

5. В **имя** , укажите имя файла ресурсов и затем выберите **добавить** кнопки.

     Файл ресурсов с расширением .bdcr добавляется в проект и открывается для редактирования.

6. Добавьте XML-код, чтобы определить локализованные имена, свойства и разрешения, которые необходимо применить к модели подключения к бизнес-данным.

     Сведения об определении этих элементов см. в разделе [ресурсов файлов модели и](http://go.microsoft.com/fwlink/?LinkID=169283).

## <a name="see-also"></a>См. также
- [Практическое руководство. Добавление существующего файла модели BDC в проект SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)
- [Создание модели подключения к бизнес-данных](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Практическое руководство. Создать модель BDC](../sharepoint/how-to-create-a-bdc-model.md)
- [Практическое руководство. Добавление пользовательской сборки в возможность BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)
- [Интеграция бизнес-данных в SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
