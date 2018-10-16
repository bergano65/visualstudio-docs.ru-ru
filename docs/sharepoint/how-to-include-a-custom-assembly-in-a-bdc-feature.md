---
title: 'Практическое: Добавление пользовательской сборки в возможность BDC | Документация Майкрософт'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.BDC.Add_Assemblies_Dialog
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], add reference
- Business Data Connectivity service [SharePoint development in Visual Studio], custom assembly
- BDC [SharePoint development in Visual Studio], custom assembly
- BDC [SharePoint development in Visual Studio], add reference
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: aa210047a65870806877e1d22e08fc1f2b9bc010
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/29/2018
ms.locfileid: "37119412"
---
# <a name="how-to-include-a-custom-assembly-in-a-bdc-feature"></a>Практическое: Добавление пользовательской сборки в возможность BDC
  Проект может ссылаться на сборки из других проектов в одном решении. Тем не менее, необходимо добавить эти сборки в файл компонента проекта с помощью **назначение связанных сборок бизнес-системам** диалоговое окно.  
  
### <a name="to-include-a-custom-assembly-in-a-business-data-connectivity-bdc-feature"></a>Для включения пользовательской сборки в функцию бизнеса данных подключения (BDC)
  
1.  В **обозревателе решений**, выберите папку, содержащую модель BDC.  
  
2.  В меню **Вид** выберите пункт **Окно свойств**.  
  
3.  В **свойства** окно, выберите **сборки** свойства, а затем кнопку с многоточием (![эллипс конструктора ASP.NET Mobile](../sharepoint/media/mwellipsis.gif "ASP.NET для мобильных устройств Эллипс конструктора")).  
  
     **Назначение связанных сборок бизнес-системам** откроется диалоговое окно.  
  
4.  В **выбрать сборку** выберите пользовательскую сборку.  
  
    > [!NOTE]  
    >  Сборки отображаются в **назначение связанных сборок бизнес-системам** диалоговое окно, если вы добавили ссылку на проект, содержащий сборку. Дополнительные сведения см. в разделе [как: Добавление и удаление ссылок с помощью Add Reference Dialog Box](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
5.  В **свойства ссылки на** группе, откройте список, отображаемый для **область бизнес-системы** свойства, выберите бизнес-систему методов, которые используют пользовательскую сборку, а затем выберите **ОК**  кнопки.  
  
    > [!NOTE]  
    >  Для отладки кода в пользовательскую сборку, необходимо добавить сборку в пакет решения. Дополнительные сведения см. в разделе [как: Добавление и удаление дополнительных сборок](../sharepoint/how-to-add-and-remove-additional-assemblies.md).  
  
## <a name="see-also"></a>См. также
 [Практическое: использование файла ресурсов для задания локализованных имен, свойств и разрешений](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)   
 [Практическое: Добавление существующего файла модели BDC в проект SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)   
 [Создание модели подключения к бизнес-данных](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Практическое: создать модель BDC](../sharepoint/how-to-create-a-bdc-model.md)   
 [Integragte бизнес-данных в SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
