---
title: "Как: Добавление ссылки на выходные данные проекта | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- project output references [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, project output references
- SharePoint development in Visual Studio, advanced packaging tools
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 0114971baa164858add68f2f1d6f571407ba5320
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-add-a-project-output-reference"></a>Практическое руководство. Добавление ссылки на выходные данные проекта
  Чтобы развернуть сборки проекта вне SharePoint (или файлы .xap в проектах Silverlight) для SharePoint, добавьте их в виде ссылки на выходные данные проекта.  
  
 Этот процесс создает зависимость сборки решения в двух проектах. Проекты, связанные с Выходные ссылки проекта построены до построения и развертывания проекта SharePoint.  
  
### <a name="to-add-a-project-output-reference"></a>Добавление ссылки на выходные данные проекта  
  
1.  Загрузите решение, содержащее хотя бы один проект SharePoint и один проект, не являющегося элементом SharePoint.  
  
2.  В **обозревателе решений**, выберите элемент в узле проекта SharePoint.  
  
3.  В **свойства** окна, выберите **Выходные ссылки проекта** свойства, а затем нажмите кнопку с многоточием (![эллипс конструктора ASP.NET Mobile](../sharepoint/media/mwellipsis.gif "ASP. Эллипс конструктора Mobile NET")) рядом с ним.  
  
4.  В **Выходные ссылки проекта** диалогового окна выберите **добавить** кнопки.  
  
5.  В панели «Свойства» щелкните стрелку рядом с **тип развертывания** свойства, а затем выберите соответствующее значение для элемента не SharePoint, вы ссылаетесь, таких как **ElementFile**.  
  
6.  Щелкните стрелку рядом с **имя проекта**, выберите имя элемента проекта, не являющегося элементом SharePoint и нажмите кнопку **ОК** кнопки.  
  
## <a name="see-also"></a>См. также  
 [Предоставление упаковке и сведения о развертывании в элементах проекта](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)   
 [Как: Пометка элементов управления как безопасных элементов управления](../sharepoint/how-to-mark-controls-as-safe-controls.md)   
 [Упаковка и развертывание решений SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  