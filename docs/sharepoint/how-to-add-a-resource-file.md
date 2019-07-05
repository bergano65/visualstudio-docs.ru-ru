---
title: Практическое руководство. Добавьте файл ресурсов | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- resource files [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, resource files
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e7b8394d0c21ed5a45639e4dad5fe3695aaccc27
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63440009"
---
# <a name="how-to-add-a-resource-file"></a>Практическое руководство. Добавьте файл ресурсов
  Команды для добавления файлов ресурсов — в контекстном меню узла решения и функции узлов в обозревателе решений. Дополнительные сведения см. в разделе [решений SharePoint, локализовать](../sharepoint/localizing-sharepoint-solutions.md).

### <a name="to-add-a-global-resource-file-to-a-sharepoint-solution"></a>Чтобы добавить глобальный файл ресурсов в решение SharePoint

1. В [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], откройте решение SharePoint.

2. В **обозревателе решений**, выберите узел проекта SharePoint и затем в строке меню выберите **проекта** > **Добавление нового элемента**.

3. В **Добавление нового элемента** диалоговое окно, выберите **глобальные файлы ресурсов** шаблона и нажмите кнопку **добавить** кнопки.

   > [!NOTE]
   > Глобальные файлы ресурсов шаблона элемента проекта отображается только в том случае, если выбрана элемента проекта SharePoint.

4. В **добавить ресурс** диалоговое окно, выберите язык и региональные параметры для файла ресурсов, например английский (США).

    Этот шаг добавляет глобальный файл ресурсов в решение в формате, Resource_x_**.** <em>языка и региональных параметров</em><strong>.</strong> RESX, такие как *Resource1.en-US.resx*.

5. Когда **редактора ресурсов** открывается в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], добавить ресурсы в файле ресурсов.

### <a name="to-add-a-feature-resource-file-to-a-sharepoint-feature"></a>Чтобы добавить файл ресурсов компонента в компонент SharePoint

1. Если решение SharePoint еще не открыт в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], откройте решение.

2. В **обозревателе решений**, откройте контекстное меню для имени функции в разделе **функции** узел, а затем выберите **добавить ресурс компонента**.

     Этот шаг добавляет файл ресурсов в формате, компонент _Имя_файла_ресурсов_**.** _языка и региональных параметров_**.resx**, такие как *Feature1.en-US.resx*.

3. Когда **редактора ресурсов** открывается в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], добавить ресурсы в файле ресурсов.

## <a name="see-also"></a>См. также
- [Разработка решений SharePoint](../sharepoint/developing-sharepoint-solutions.md)
