---
title: "Как: Добавление и удаление компонентов и элементов в пакете с помощью обозревателя пакетов | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.SharePointTools.RAD.PackagingExplorer
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords: SharePoint development in Visual Studio, packages
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 25a2514f2d25661de2898be8d2ef9ff051cc5559
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer"></a>Практическое руководство. Добавление и удаление компонентов и элементов в пакете с помощью обозревателя пакетов
  Чтобы настроить пакет для развертывания компонентов и элементов SharePoint, можно использовать обозреватель пакетов. Компоненты и элементы проектов SharePoint можно настроить в WSP-файле.  
  
 Кроме того можно использовать конструктор пакетов для просмотра и изменения порядка для изменения порядка активации компонентов. Дополнительные сведения см. в разделе [как: Добавление и удаление компонентов и элементов в пакете с помощью конструктора пакетов](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md).  
  
## <a name="opening-the-packaging-explorer"></a>Запуск обозревателя пакетов  
 Чтобы открыть обозреватель пакетов, можно использовать следующую процедуру, если решение Visual Studio содержит хотя бы один проект SharePoint. Кроме того обозреватель пакетов автоматически открывается при просмотре конструкторы компонентов и пакетов. После закрытия всех конструкторов компонентов и пакетов, обозреватель пакетов также закроется.  
  
#### <a name="to-open-the-packaging-explorer"></a>Чтобы открыть обозреватель пакетов  
  
1.  В строке меню выберите **представление**, **другие окна**, **обозреватель пакетов**.  
  
     **Обозреватель пакетов** отображается в **элементов**.  
  
## <a name="adding-a-feature-to-a-package"></a>Добавление компонента в пакет  
 Новые и существующие компоненты можно добавить в пакет с помощью обозревателя пакетов.  
  
#### <a name="to-add-a-sharepoint-feature"></a>Чтобы добавить в компонент SharePoint  
  
1.  Откройте **обозреватель пакетов**, откройте контекстное меню для проекта и выберите **добавить компонент**.  
  
#### <a name="to-move-an-existing-sharepoint-feature"></a>Для перемещения существующей функции SharePoint  
  
1.  Откройте **обозреватель пакетов**, а затем выполните одно из следующих действий:  
  
    -   Перетащите **функция** из одного проекта в другой проект.  
  
    -   Откройте контекстное меню для компонента, выберите **Вырезать**, откройте контекстное меню для проекта, к которому вы хотите переместить компонент, а затем выберите **вставить**.  
  
    > [!NOTE]  
    >  Эта процедура используется в случае, если в решении имеется несколько проектов SharePoint.  
  
## <a name="validating-a-feature-or-package"></a>Проверка компонента или пакета  
 Проверка файлов можно выявлять потенциальные проблемы в компонентах и пакетах SharePoint. Ошибки и предупреждения отображаются в окне вывода и список ошибок.  
  
#### <a name="to-validate-a-sharepoint-feature-or-package"></a>Чтобы проверить SharePoint компонента или пакета  
  
1.  Откройте **обозреватель пакетов**.  
  
2.  Откройте контекстное меню для компонента или пакета, а затем выберите **проверки**.  
  
## <a name="see-also"></a>См. также  
 [Упаковка и развертывание решений SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  