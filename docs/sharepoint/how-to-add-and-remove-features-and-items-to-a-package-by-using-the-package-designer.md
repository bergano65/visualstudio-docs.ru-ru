---
title: 'Конструктор пакетов: Добавление & удаление компонентов и элементов в пакет'
titleSuffix: ''
description: Узнайте, как добавлять и удалять компоненты и элементы в пакете SharePoint с помощью конструктора пакетов в Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.RAD.PackageDesignerDesign
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 92503d8e29bac4f44df5376f3cecb24247b585d6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99923594"
---
# <a name="how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer"></a>Пошаговое руководство. Добавление и удаление компонентов и элементов в пакет с помощью конструктора пакетов
  При создании решения SharePoint Visual Studio добавляет компоненты SharePoint по умолчанию в пакет в решении. Перед окончательным развертыванием можно добавлять и удалять элементы и компоненты проекта SharePoint для изменения пакета SharePoint.

 Кроме того, можно использовать обозреватель пакетов для добавления и удаления элементов проектов SharePoint. Можно также просмотреть и изменить иерархию элементов и компонентов проекта SharePoint, помещаемых в пакет (WSP-файлы). Дополнительные сведения см. в разделе [инструкции. Добавление и удаление компонентов и элементов в пакете с помощью обозревателя пакетов](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md).

## <a name="add-features-to-a-sharepoint-package"></a>Добавление компонентов в пакет SharePoint
 Для добавления компонентов в пакет SharePoint можно использовать конструктор пакетов.

#### <a name="to-add-sharepoint-features-with-the-package-designer"></a>Добавление функций SharePoint с помощью конструктора пакетов

1. Откройте **конструктор пакетов**.

    Дополнительные сведения см. [в разделе руководство. Настройка пакета решения SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).

2. Добавьте одну или несколько функций SharePoint, выполнив одно или несколько из следующих действий.

   1. Дважды щелкните каждый элемент в списке **элементов списка решений** , который требуется добавить.

   2. Выберите элемент, который требуется добавить, а затем нажмите кнопку **Добавить** (>).

   3. Нажмите кнопку " **Добавить все** " (>>), чтобы добавить все элементы одновременно.

      Например, можно дважды щелкнуть элемент в списке **элементов списка решений** , чтобы добавить его в **элементы списка пакет** .

      Элементы и компоненты проекта SharePoint отображаются в **элементах списка пакетов** .

## <a name="remove-features-from-a-sharepoint-package"></a>Удаление компонентов из пакета SharePoint
 Для удаления компонентов в пакет SharePoint можно использовать конструктор пакетов.

#### <a name="to-remove-sharepoint-features-with-the-package-designer"></a>Удаление компонентов SharePoint с помощью конструктора пакетов

1. В списке **элементы списка пакет** выберите элемент, который требуется удалить, а затем нажмите кнопку **Удалить** (<) или нажмите кнопку **Удалить << все** , чтобы удалить все элементы.

     Элементы SharePoint отображаются в **элементах списка решение** .

## <a name="see-also"></a>См. также раздел
- [Создание пакетов решений SharePoint](../sharepoint/creating-sharepoint-solution-packages.md)
- [Как настроить пакет решения SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)
- [Как создать пакет](/previous-versions/ee231585(v=vs.110))