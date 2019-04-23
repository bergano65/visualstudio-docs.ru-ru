---
title: Практическое руководство. Добавить выходную ссылку проекта | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project output references [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, project output references
- SharePoint development in Visual Studio, advanced packaging tools
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2ae3965647416d7a8e11cf0ea5e24cef1e54a09b
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60079789"
---
# <a name="how-to-add-a-project-output-reference"></a>Практическое руководство. Добавить ссылку на выходные данные проекта
  Для развертывания сборки проекта вне SharePoint (или XAP-файлы в проектах Silverlight) в SharePoint, их необходимо добавьте как ссылку на выходные данные проекта.

 Этот процесс создает зависимость сборки решения между двумя проектами. Проекты, связанные с Выходные ссылки проекта построены до построения и развертывания проектов SharePoint.

### <a name="to-add-a-project-output-reference"></a>Чтобы добавить в проект ссылки на выходные данные.

1. Загрузите решение, которое содержит хотя бы один проект SharePoint и один проект не SharePoint.

2. В **обозревателе решений**, выберите элемент в узле проекта SharePoint.

3. В **свойства** окно, выберите **Выходные ссылки проекта** свойства, а затем нажмите кнопку с многоточием (![эллипс конструктора ASP.NET Mobile](../sharepoint/media/mwellipsis.gif "ASP. Эллипс конструктора Mobile NET")) кнопку рядом с ним.

4. В **Выходные ссылки проекта** диалоговое окно, выберите **добавить** кнопки.

5. На панели «Свойства» нажмите стрелку рядом с полем **типа развертывания** свойство, а затем выберите соответствующее значение для элемента не SharePoint, вы ссылаетесь, такие как **ElementFile**.

6. Выберите стрелку рядом с пунктом **имя_проекта**, выберите имя элемента проекта вне SharePoint и затем выберите **ОК** кнопки.

## <a name="see-also"></a>См. также
- [Предоставляют сведения о упаковки и развертывания в элементах проекта](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
- [Практическое руководство. Пометка элементов управления как безопасных](../sharepoint/how-to-mark-controls-as-safe-controls.md)
- [Упаковка и развертывание решений SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
