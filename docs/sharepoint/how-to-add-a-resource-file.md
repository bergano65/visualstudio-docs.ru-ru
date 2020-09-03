---
title: Как добавить файл ресурсов | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 657eb473adcff40a62d2fc9b09518ebe8135eeb4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "86015177"
---
# <a name="how-to-add-a-resource-file"></a>Как добавить файл ресурсов
  Команды для добавления файлов ресурсов находятся в контекстном меню узла решения и узлов компонентов в обозреватель решений. Дополнительные сведения см. в разделе [локализация решений SharePoint](../sharepoint/localizing-sharepoint-solutions.md).

### <a name="to-add-a-global-resource-file-to-a-sharepoint-solution"></a>Добавление глобального файла ресурсов в решение SharePoint

1. В [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] откройте решение SharePoint.

2. В **Обозреватель решений**выберите узел проекта SharePoint, а затем в строке меню выберите **проект**  >  **Добавить новый элемент**.

3. В диалоговом окне **Добавление нового элемента** выберите шаблон **файл глобальных ресурсов** , а затем нажмите кнопку **добавить** .

   > [!NOTE]
   > Шаблон элемента проекта глобальных ресурсов отображается, только если выбран элемент проекта SharePoint.

4. В диалоговом окне **Добавление ресурса** выберите язык и региональные параметры для файла ресурсов, например английский (США).

    На этом шаге в решение добавляется глобальный файл ресурсов в формате Resource_x_**.** <em>язык и региональные параметры</em><strong>.</strong> RESX, например *Resource1. en-US. resx*.

5. Когда **Редактор ресурсов** откроется в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , добавьте ресурсы в файл ресурсов.

### <a name="to-add-a-feature-resource-file-to-a-sharepoint-feature"></a>Добавление файла ресурсов компонента в компонент SharePoint

1. Если решение SharePoint еще не открыто в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , откройте решение.

2. В **Обозреватель решений**откройте контекстное меню для имени компонента в узле " **компоненты** ", а затем выберите **Добавить ресурс компонента**.

     На этом шаге в компонент добавляется файл ресурсов в формате _ресаурцефиленаме_**.** _culture_**. resx**, например, *Feature1. en-US. resx*.

3. Когда **Редактор ресурсов** откроется в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , добавьте ресурсы в файл ресурсов.

## <a name="see-also"></a>См. также раздел
- [Разработка решений SharePoint](../sharepoint/developing-sharepoint-solutions.md)
