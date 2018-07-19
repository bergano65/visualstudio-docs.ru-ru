---
title: 'Способ: добавить выходную ссылку проекта | Документация Майкрософт'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: 47b6a3d164bbe1ddcda6d131275427fb1f815198
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/25/2018
ms.locfileid: "36755481"
---
# <a name="how-to-add-a-project-output-reference"></a>Способ: добавить выходную ссылку проекта
  Для развертывания сборки проекта вне SharePoint (или XAP-файлы в проектах Silverlight) в SharePoint, их необходимо добавьте как ссылку на выходные данные проекта.  
  
 Этот процесс создает зависимость сборки решения между двумя проектами. Проекты, связанные с Выходные ссылки проекта построены до построения и развертывания проектов SharePoint.  
  
### <a name="to-add-a-project-output-reference"></a>Чтобы добавить в проект ссылки на выходные данные.
  
1.  Загрузите решение, которое содержит хотя бы один проект SharePoint и один проект не SharePoint.  
  
2.  В **обозревателе решений**, выберите элемент в узле проекта SharePoint.  
  
3.  В **свойства** окно, выберите **Выходные ссылки проекта** свойства, а затем нажмите кнопку с многоточием (![эллипс конструктора ASP.NET Mobile](../sharepoint/media/mwellipsis.gif "ASP. Эллипс конструктора Mobile NET")) кнопку рядом с ним.  
  
4.  В **Выходные ссылки проекта** диалоговое окно, выберите **добавить** кнопки.  
  
5.  На панели «Свойства» нажмите стрелку рядом с полем **типа развертывания** свойство, а затем выберите соответствующее значение для элемента не SharePoint, вы ссылаетесь, такие как **ElementFile**.  
  
6.  Выберите стрелку рядом с пунктом **имя_проекта**, выберите имя элемента проекта вне SharePoint и затем выберите **ОК** кнопки.  
  
## <a name="see-also"></a>См. также
 [Предоставляют сведения о упаковки и развертывания в элементах проекта](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)   
 [Практическое: Пометка элементов управления как безопасных](../sharepoint/how-to-mark-controls-as-safe-controls.md)   
 [Упаковка и развертывание решений SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  
