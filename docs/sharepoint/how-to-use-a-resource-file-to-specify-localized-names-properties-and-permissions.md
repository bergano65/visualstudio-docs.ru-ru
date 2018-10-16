---
title: 'Практическое: использование файла ресурсов для задания локализованных имен, свойств и разрешений | Документация Майкрософт'
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
- Business Data Connectivity service [SharePoint development in Visual Studio], localize strings
- BDC [SharePoint development in Visual Studio], localize strings
- BDC [SharePoint development in Visual Studio], resource file
- Business Data Connectivity service [SharePoint development in Visual Studio], resource strings
- BDC [SharePoint development in Visual Studio], properties
- Business Data Connectivity service [SharePoint development in Visual Studio], properties
- Business Data Connectivity service [SharePoint development in Visual Studio], resource file
- BDC [SharePoint development in Visual Studio], resource strings
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c54aa87f09d4821f9fde5cceb95e6ec3a8e089fa
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/29/2018
ms.locfileid: "37119444"
---
# <a name="how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions"></a>Практическое: использование файла ресурсов для задания локализованных имен, свойств и разрешений
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
 [Практическое: Добавление существующего файла модели BDC в проект SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)   
 [Создание модели подключения к бизнес-данных](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Практическое: создать модель BDC](../sharepoint/how-to-create-a-bdc-model.md)   
 [Практическое: Добавление пользовательской сборки в возможность BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)   
 [Интеграция бизнес-данных в SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
