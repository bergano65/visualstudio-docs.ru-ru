---
title: 'Способ: добавить файл ресурсов | Документация Майкрософт'
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
ms.openlocfilehash: 3406e65ad96b93cd21890d61270c0ed989ad496c
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2018
ms.locfileid: "36756575"
---
# <a name="how-to-add-a-resource-file"></a>Способ: добавить файл ресурсов
  Команды для добавления файлов ресурсов — в контекстном меню узла решения и функции узлов в обозревателе решений. Дополнительные сведения см. в разделе [решений SharePoint, локализовать](../sharepoint/localizing-sharepoint-solutions.md).  
  
### <a name="to-add-a-global-resource-file-to-a-sharepoint-solution"></a>Чтобы добавить глобальный файл ресурсов в решение SharePoint  
  
1.  В [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], откройте решение SharePoint.  
  
2.  В **обозревателе решений**, выберите узел проекта SharePoint и затем в строке меню выберите **проекта** > **Добавление нового элемента**.  
  
3.  В **Добавление нового элемента** диалоговое окно, выберите **глобальные файлы ресурсов** шаблона и нажмите кнопку **добавить** кнопки.  
  
    > [!NOTE]  
    >  Глобальные файлы ресурсов шаблона элемента проекта отображается только в том случае, если выбрана элемента проекта SharePoint.  
  
4.  В **добавить ресурс** диалоговое окно, выберите язык и региональные параметры для файла ресурсов, например английский (США).  
  
     Этот шаг добавляет глобальный файл ресурсов в формате, ресурсов решение * x ***.*** язык и региональные параметры ***.** RESX, такие как *Resource1.en-US.resx*.  
  
5.  Когда **редактора ресурсов** открывается в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], добавить ресурсы в файле ресурсов.  
  
### <a name="to-add-a-feature-resource-file-to-a-sharepoint-feature"></a>Чтобы добавить файл ресурсов компонента в компонент SharePoint  
  
1.  Если решение SharePoint еще не открыт в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], откройте решение.  
  
2.  В **обозревателе решений**, откройте контекстное меню для имени функции в разделе **функции** узел, а затем выберите **добавить ресурс компонента**.  
  
     Этот шаг добавляет файл ресурсов в формате, компонент * Имя_файла_ресурсов ***.*** язык и региональные параметры ***.** RESX, такие как *Feature1.en-US.resx*.  
  
3.  Когда **редактора ресурсов** открывается в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], добавить ресурсы в файле ресурсов.  
  
## <a name="see-also"></a>См. также
 [Разработка решений SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
 
