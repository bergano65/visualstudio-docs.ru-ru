---
title: 'Практическое: Добавление и удаление компонентов и элементов в пакете с помощью конструктора пакетов | Документация Майкрософт'
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
ms.openlocfilehash: a2307a870487a3cc62a60b4162245db57653d452
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2018
ms.locfileid: "36756097"
---
# <a name="how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer"></a>Практическое: Добавление и удаление компонентов и элементов в пакете с помощью конструктора пакетов
  При создании решения SharePoint, Visual Studio добавляет функции SharePoint по умолчанию для пакета в решении. Перед окончательным развертыванием можно добавить и удаление элементов проекта SharePoint и компонентов для изменения пакета SharePoint.  
  
 Кроме того можно использовать обозреватель пакетов для добавления и удаления элементов проекта SharePoint. Кроме того, можно также просматривать и изменять иерархию элементов проекта SharePoint и функции, которые помещаются в пакет (.wsp). Дополнительные сведения см. в разделе [как: Добавление и удаление компонентов и элементов в пакете с помощью обозревателя пакетов](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md).  
  
## <a name="add-features-to-a-sharepoint-package"></a>Добавление компонентов в пакет SharePoint  
 Чтобы добавить компоненты в пакет SharePoint можно использовать конструктор пакетов.  
  
#### <a name="to-add-sharepoint-features-with-the-package-designer"></a>Добавление компонентов SharePoint с помощью конструктора пакетов
  
1.  Откройте **конструктор пакетов**.  
  
     Дополнительные сведения см. в разделе [как: Настройка пакета решения SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).  
  
2.  Добавьте один или несколько компонентов SharePoint, выполнив одно или несколько из следующих действий:  
  
    1.  Дважды щелкните каждый элемент в **элементы в решении** список, который вы хотите добавить.  
  
    2.  Выберите элемент, который вы хотите добавить, а затем выберите **добавить** кнопки (>).  
  
    3.  Выберите **добавить все** кнопки (>>) чтобы добавить все элементы за один раз.  
  
     Например, можно дважды щелкнуть элемент в **элементы в решении** списка, чтобы добавить его в **элементы в пакете** списка.  
  
     Компоненты и элементы проектов SharePoint отображаются в **элементы в пакете** списка.  
  
## <a name="remove-features-from-a-sharepoint-package"></a>Удаление компонентов из пакета SharePoint  
 Конструктор пакетов можно использовать для удаления компонентов из пакета SharePoint.  
  
#### <a name="to-remove-sharepoint-features-with-the-package-designer"></a>Для удаления компонентов SharePoint с помощью конструктора пакетов
  
1.  В **элементы в пакете** выберите элемент, который требуется удалить, а затем выберите **удалить** (<) кнопку или выбрать **удалить все** кнопки (<<) для удаления все элементы.  
  
     Элементы SharePoint отображаются в **элементы в решении** списка.  
  
## <a name="see-also"></a>См. также
 [Создание пакетов решений SharePoint](../sharepoint/creating-sharepoint-solution-packages.md)   
 [Практическое: Настройка пакета решения SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)  
 [Практическое: Создание пакета](http://msdn.microsoft.com/en-us/b24be45c-e91d-49bb-afb0-7b265404214b)  
  
