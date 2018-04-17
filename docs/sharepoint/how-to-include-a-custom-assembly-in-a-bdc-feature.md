---
title: 'Как: Добавление пользовательской сборки в функцию BDC | Документы Microsoft'
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
ms.openlocfilehash: ab104ee31246a524e2c34c513a66a5f5143d5f55
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-include-a-custom-assembly-in-a-bdc-feature"></a>Практическое руководство. Добавление пользовательской сборки в возможность BDC
  Проект может ссылаться на сборки из других проектов в одном решении. Тем не менее, необходимо добавить эти сборки в список функций проекта с помощью **Assign связанных сборок бизнес-системам** диалоговое окно.  
  
### <a name="to-include-a-custom-assembly-in-a-business-data-connectivity-bdc-feature"></a>Для включения пользовательской сборки в функцию бизнес-данным (BDC)  
  
1.  В **обозревателе решений**, откройте папку, содержащую модель BDC.  
  
2.  В меню **Вид** выберите пункт **Окно свойств**.  
  
3.  В **свойства** окно, выберите **сборки** свойство и нажмите кнопку с многоточием (![эллипс конструктора ASP.NET Mobile](../sharepoint/media/mwellipsis.gif "ASP.NET для мобильных устройств Эллипс конструктора")).  
  
     **Assign связанных сборок бизнес-системам** откроется диалоговое окно.  
  
4.  В **выбрать сборку** выберите пользовательскую сборку.  
  
    > [!NOTE]  
    >  Сборки отображаются в **Assign связанных сборок бизнес-системам** диалоговое окно «», если вы добавили ссылку на проект, содержащий сборку. Дополнительные сведения см. в разделе [как: Добавление и удаление ссылок с помощью диалоговое окно Добавить ссылку](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
5.  В **свойства ссылки** откройте список, отображаемый для **область бизнес-системы** свойства, выберите бизнес-систему методов, которые используют пользовательскую сборку, а затем выберите **ОК**  кнопки.  
  
    > [!NOTE]  
    >  Для отладки кода в пользовательской сборке необходимо добавить сборку в пакет решения. Дополнительные сведения см. в разделе [как: Добавление и удаление дополнительных сборок](../sharepoint/how-to-add-and-remove-additional-assemblies.md).  
  
## <a name="see-also"></a>См. также  
 [Как: определить локализованные имена, свойства и разрешения с помощью файла ресурсов](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)   
 [Как: Добавление существующего файла модели BDC в проект SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)   
 [Создание модели подключения к бизнес-данным](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Как: создать модель BDC](../sharepoint/how-to-create-a-bdc-model.md)   
 [Интеграция бизнес-данных в SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  