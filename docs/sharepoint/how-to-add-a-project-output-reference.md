---
title: Как добавить выходную ссылку на проект | Документация Майкрософт
description: Узнайте, как добавить выходную ссылку на проект, чтобы развертывать сборки проектов, не относящиеся к SharePoint (или XAP-файлы в проектах Silverlight), в SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 03980eea9d16cde2b6f079e0b33973958fed7a7f
ms.sourcegitcommit: ad2c820b280b523a7f7aef89742cdb719354748f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2020
ms.locfileid: "94849874"
---
# <a name="how-to-add-a-project-output-reference"></a>Как добавить выходную ссылку проекта
  Чтобы развернуть сборки проектов, не относящиеся к SharePoint (или XAP-файлы в проектах Silverlight), в SharePoint, добавьте их в качестве выходной ссылки проекта.

 Этот процесс создает зависимость построения решения между двумя проектами. Проекты, связанные с выходными ссылками проекта, создаются перед построением и развертыванием проекта SharePoint.

### <a name="to-add-a-project-output-reference"></a>Добавление выходной ссылки на проект

1. Загрузите решение, содержащее хотя бы один проект SharePoint и один проект, не относящийся к SharePoint.

2. В **Обозреватель решений** выберите элемент в узле проекта SharePoint.

3. В окне **Свойства** выберите свойство **Выходные ссылки проекта** , а затем нажмите кнопку с многоточием (![ASP.net Mobile Designer (эллипс](../sharepoint/media/mwellipsis.gif "Эллипс конструктора ASP.NET для мобильных устройств"))) рядом с ним.

4. В диалоговом окне **Выходные ссылки проекта** нажмите кнопку **Добавить** .

5. На панели свойств щелкните стрелку рядом со свойством **тип развертывания** , а затем выберите соответствующее значение для элемента, не являющегося элементом SharePoint, на который вы ссылаетесь, например **ElementFile**.

6. Щелкните стрелку рядом с **именем проекта**, выберите имя элемента проекта, не относящегося к SharePoint, а затем нажмите кнопку **ОК** .

## <a name="see-also"></a>См. также статью
- [Предоставление сведений об упаковке и развертывании в элементах проекта](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
- [Как пометить элементы управления как защищенные](../sharepoint/how-to-mark-controls-as-safe-controls.md)
- [Упаковка и развертывание решений SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
