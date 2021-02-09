---
title: Как добавить элементы в проект SharePoint | Документация Майкрософт
description: Добавление новых или существующих элементов в проект SharePoint в Visual Studio после открытия или создания решения SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, adding items
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 4a32d38b20b93cf215cb53c2c2d2b8767418de24
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99923486"
---
# <a name="how-to-add-items-to-a-sharepoint-project"></a>Как добавлять элементы в проект SharePoint
  Решения SharePoint содержат один или несколько проектов, каждый из которых содержит несколько элементов проекта SharePoint. После открытия или создания решения SharePoint можно добавить в эти проекты либо новые, либо существующие элементы. Например, новые проекты рабочих процессов поставляются с формой по умолчанию с именем Default. aspx, но эту форму можно заменить новой или другой формой или добавить другую форму ASPX.

### <a name="to-add-a-new-project-item-to-a-sharepoint-solution"></a>Добавление нового элемента проекта в решение SharePoint

1. В [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] откройте или создайте решение SharePoint.

2. В **Обозреватель решений** выберите узел проекта.

3. В строке меню выберите **проект**  >  **Добавить новый элемент** , чтобы открыть диалоговое окно **Добавление нового элемента** .

4. В списке **Установленные шаблоны** разверните узел **SharePoint** , а затем выберите узел **2010** .

5. В списке шаблонов элементов проекта выберите шаблон.

6. В текстовом поле **имя** введите имя, а затем нажмите кнопку **ОК** .

### <a name="to-add-an-existing-project-item-to-a-sharepoint-solution"></a>Добавление существующего элемента проекта в решение SharePoint

1. В [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] откройте или создайте решение SharePoint.

2. В **Обозреватель решений** выберите узел проекта.

3. В строке меню выберите **проект**  >  **Добавить существующий элемент** , чтобы открыть диалоговое окно **Добавление существующего элемента** .

4. Перейдите к папке, содержащей элемент, который требуется добавить, выберите его и нажмите кнопку **Добавить** .

## <a name="see-also"></a>См. также раздел
- [Шаблоны проектов и элементов проектов SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md)
- [Разработка решений SharePoint](../sharepoint/developing-sharepoint-solutions.md)
