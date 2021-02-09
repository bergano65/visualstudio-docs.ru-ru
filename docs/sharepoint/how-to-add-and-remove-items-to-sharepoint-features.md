---
title: Как добавлять и удалять элементы в компонентах SharePoint | Документация Майкрософт
description: Вручную добавлять и удалять элементы проектов SharePoint в компонентах SharePoint с помощью конструктора компонентов в Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.RAD.FeatureDesigner
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, features
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f18c46bb7bab2acd1d97e3154b53ab8ca52520e3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99923467"
---
# <a name="how-to-add-and-remove-items-to-sharepoint-features"></a>Как добавлять и удалять элементы в функциях SharePoint
  При создании решения SharePoint Visual Studio добавляет элементы проекта SharePoint по умолчанию в компонент. Перед развертыванием можно добавлять и удалять элементы проектов SharePoint для изменения компонента SharePoint.

## <a name="add-sharepoint-project-items-to-a-feature"></a>Добавление элементов проектов SharePoint в компонент

#### <a name="to-add-sharepoint-project-items-with-the-feature-designer"></a>Добавление элементов проекта SharePoint с помощью конструктора компонентов

1. Откройте конструктор компонентов.

    Дополнительные сведения см. в разделе [Практическое руководство. Настройка компонента SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md).

2. Добавьте один или несколько элементов из списка **элементов в список решений** в **элементы в списке компонентов** , выполнив одно или несколько действий, описанных ниже.

   - Дважды щелкните каждый элемент, который требуется добавить.

   - Выберите элемент, который требуется добавить, а затем нажмите кнопку **Добавить** (>).

   - Нажмите кнопку **Добавить все** (>>).

     Элементы проектов SharePoint отображаются в **элементах в списке компонентов** .

## <a name="remove-sharepoint-project-items-from-a-feature"></a>Удаление элементов проекта SharePoint из компонента

#### <a name="to-remove-sharepoint-items-with-the-feature-designer"></a>Удаление элементов SharePoint с помощью конструктора компонентов

1. Выберите один или несколько элементов в **элементах в списке компонентов** .

2. Нажмите кнопку **Удалить** (<), чтобы удалить один элемент за раз, или нажмите кнопку **удалить все** (<<), чтобы удалить все элементы.

     Элементы проекта SharePoint отображаются в **элементах списка решение** .

## <a name="see-also"></a>См. также раздел
- [Создание компонентов SharePoint](../sharepoint/creating-sharepoint-features.md)
- [Упаковка и развертывание решений SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
