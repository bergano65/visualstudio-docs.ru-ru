---
title: 'Как: Добавление и удаление компонентов и элементов в пакете с помощью конструктора пакетов | Документы Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.RAD.PackageDesignerDesign
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c6f807394497bff99e12546f7a1a913adffbff41
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer"></a>Практическое руководство. Добавление и удаление компонентов и элементов в пакете с помощью конструктора пакетов
  При создании решения SharePoint пакета в решении Visual Studio добавляет возможности SharePoint по умолчанию. Перед окончательным развертыванием можно можно добавлять и удалять элементы проектов SharePoint и для изменения пакета SharePoint.  
  
 Кроме того можно использовать обозреватель пакетов для добавления и удаления элементов проекта SharePoint. Кроме того, можно просматривать и изменять иерархию элементов проектов SharePoint и компоненты, входящие в пакет (WSP-файл). Дополнительные сведения см. в разделе [как: Добавление и удаление компонентов и элементов в пакете с помощью обозревателя пакетов](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md).  
  
## <a name="adding-features-to-a-sharepoint-package"></a>Добавление компонентов в пакет SharePoint  
 Добавление компонентов в пакет SharePoint, можно использовать конструктор пакетов.  
  
#### <a name="to-add-sharepoint-features-with-the-package-designer"></a>Добавление компонентов SharePoint с помощью конструктора пакетов  
  
1.  Откройте **конструктор пакетов**.  
  
     Дополнительные сведения см. в разделе [как: Настройка пакета решения SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).  
  
2.  Добавьте один или несколько компонентов SharePoint, выполнив одно или несколько из следующих действий.  
  
    1.  Дважды щелкните каждый элемент в **элементы в решении** список, который требуется добавить.  
  
    2.  Выберите элемент, который требуется добавить, а затем выберите **добавить** кнопку (>).  
  
    3.  Выберите **добавить все** кнопки (>>) для добавления всех элементов за один раз.  
  
     Например, можно дважды щелкнуть элемент **элементы в решении** список, чтобы добавить его в **элементы в пакете** списка.  
  
     Компоненты и элементы проектов SharePoint отображаются в **элементы в пакете** списка.  
  
## <a name="removing-features-from-a-sharepoint-package"></a>Удаление компонентов из пакета SharePoint  
 Конструктор пакетов можно использовать для удаления компонентов из пакета SharePoint.  
  
#### <a name="to-remove-sharepoint-features-with-the-package-designer"></a>Удаление компонентов SharePoint с помощью конструктора пакетов  
  
1.  В **элементы в пакете** выберите элемент, который требуется удалить, а затем выберите **удалить** (<) кнопку или выберите **удалить все** кнопки (<<) для удаления все элементы.  
  
     Элементы SharePoint отображаются в **элементы в решении** списка.  
  
## <a name="see-also"></a>См. также  
 [Создание пакетов решений SharePoint](../sharepoint/creating-sharepoint-solution-packages.md)   
 [Практическое руководство. Настройка пакета решения SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)  
 [Как: Создание пакета](http://msdn.microsoft.com/en-us/b24be45c-e91d-49bb-afb0-7b265404214b)  
  
  