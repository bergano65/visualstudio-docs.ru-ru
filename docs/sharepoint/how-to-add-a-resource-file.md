---
title: Как добавить файл ресурсов | Документация Майкрософт
description: Добавьте файл ресурсов в Visual Studio, используя команды в контекстном меню узла решения и узлов компонентов в обозреватель решений.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 22b5638f7251b34c74da348e55e755cd27132aff
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934849"
---
# <a name="how-to-add-a-resource-file"></a>Практическое руководство. Добавление файла ресурсов
  Команды для добавления файлов ресурсов находятся в контекстном меню узла решения и узлов компонентов в обозреватель решений. Дополнительные сведения см. в разделе [локализация решений SharePoint](../sharepoint/localizing-sharepoint-solutions.md).

### <a name="to-add-a-global-resource-file-to-a-sharepoint-solution"></a>Добавление глобального файла ресурсов в решение SharePoint

1. В [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] откройте решение SharePoint.

2. В **Обозреватель решений** выберите узел проекта SharePoint, а затем в строке меню выберите **проект**  >  **Добавить новый элемент**.

3. В диалоговом окне **Добавление нового элемента** выберите шаблон **файл глобальных ресурсов** , а затем нажмите кнопку **добавить** .

   > [!NOTE]
   > Шаблон элемента проекта глобальных ресурсов отображается, только если выбран элемент проекта SharePoint.

4. В диалоговом окне **Добавление ресурса** выберите язык и региональные параметры для файла ресурсов, например английский (США).

    На этом шаге в решение добавляется глобальный файл ресурсов в формате Resource_x_ **.** <em>язык и региональные параметры</em><strong>.</strong> RESX, например *Resource1. en-US. resx*.

5. Когда **Редактор ресурсов** откроется в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , добавьте ресурсы в файл ресурсов.

### <a name="to-add-a-feature-resource-file-to-a-sharepoint-feature"></a>Добавление файла ресурсов компонента в компонент SharePoint

1. Если решение SharePoint еще не открыто в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , откройте решение.

2. В **Обозреватель решений** откройте контекстное меню для имени компонента в узле " **компоненты** ", а затем выберите **Добавить ресурс компонента**.

     На этом шаге в компонент добавляется файл ресурсов в формате _ресаурцефиленаме_**.** _culture_**. resx**, например, *Feature1. en-US. resx*.

3. Когда **Редактор ресурсов** откроется в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , добавьте ресурсы в файл ресурсов.

## <a name="see-also"></a>См. также раздел
- [Разработка решений SharePoint](../sharepoint/developing-sharepoint-solutions.md)
