---
title: 'Способ: добавьте файл ресурсов | Документы Microsoft'
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
- resource files [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, resource files
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 132a5b5933b1bc96244238570091e522f8af91d2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-a-resource-file"></a>Практическое руководство. Добавление файла ресурсов
  Команды для добавления файлов ресурсов — в контекстном меню узла решения и узлов компонентов в обозревателе решений. Дополнительные сведения см. в разделе [локализация решений SharePoint](../sharepoint/localizing-sharepoint-solutions.md).  
  
### <a name="to-add-a-global-resource-file-to-a-sharepoint-solution"></a>Чтобы добавить глобальный файл ресурсов в решение SharePoint  
  
1.  В [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], откройте решение SharePoint.  
  
2.  В **обозревателе решений**, выберите узел проекта SharePoint и затем в строке меню выберите **проекта**, **Добавление нового элемента**.  
  
3.  В **Добавление нового элемента** диалогового окна выберите **глобальный файл ресурсов** шаблона и выберите **добавить** кнопки.  
  
    > [!NOTE]  
    >  Шаблон элемента проекта глобальный файл ресурсов отображается только в том случае, если выбрана элемента проекта SharePoint.  
  
4.  В **добавить ресурс** диалогового окна выберите культуру файла ресурсов, таких как английский (США).  
  
     Этот шаг добавляет глобальный файл ресурсов в формате ресурса решение * x***.*** язык и региональные параметры ***.** RESX, например Resource1.en US.resx.  
  
5.  Когда **редактор ресурсов** открывается в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], добавьте ресурсы в файл ресурсов.  
  
### <a name="to-add-a-feature-resource-file-to-a-sharepoint-feature"></a>Чтобы добавить файл ресурсов компонента в компонент SharePoint  
  
1.  Если решение SharePoint еще не открыт в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], откройте решение.  
  
2.  В **обозревателе решений**, откройте контекстное меню для имени функции в **функции** узел и выберите **добавить ресурс компонента**.  
  
     Этот шаг добавляет файл ресурсов в формате, компонент * Имя_файла_ресурсов***.*** язык и региональные параметры ***.** RESX, например Feature1.en US.resx.  
  
3.  Когда **редактор ресурсов** открывается в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], добавьте ресурсы в файл ресурсов.  
  
## <a name="see-also"></a>См. также  
 [Разработка решений SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
  