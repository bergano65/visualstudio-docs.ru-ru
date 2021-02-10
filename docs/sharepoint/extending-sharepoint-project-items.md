---
title: Расширение элементов проектов SharePoint | Документация Майкрософт
description: Ознакомьтесь с задачами по расширению элементов проектов SharePoint. Узнайте, как связаны расширения элементов проекта и экземпляры элементов проекта.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: e8486120b0f08077bc30c2a5177a8aba915c37f4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948678"
---
# <a name="extend-sharepoint-project-items"></a>Расширение элементов проектов SharePoint
  Расширение элемента проекта создается, если требуется добавить функциональные возможности в тип элемента проекта SharePoint, уже установленный в Visual Studio. Например, можно создать расширение для встроенных элементов проекта " **приемник событий** " или " **Определение списка** " в Visual Studio или создать расширение для пользовательского типа элемента проекта. Также можно создать расширение для всех типов элементов проектов SharePoint.

## <a name="tasks-for-extending-sharepoint-project-items"></a>Задачи по расширению элементов проектов SharePoint
 Чтобы расширить элемент проекта, создайте сборку расширения Visual Studio, которая реализует <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> интерфейс. Дополнительные сведения см. [в разделе инструкции. Создание расширения элемента проекта SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).

 При расширении элемента проекта можно также добавить в элемент проекта следующие функциональные возможности:

- Добавление пункта контекстного меню в элемент проекта. Пункт меню появляется при открытии контекстного меню элемента проекта в **Обозреватель решений**. Откройте контекстное меню, щелкнув правой кнопкой мыши элемент проекта или выбрав его, а затем нажав клавиши **SHIFT** + **F10** . Дополнительные сведения см. [в разделе инструкции. Добавление пункта контекстного меню в расширение элемента проекта SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md).

- Добавьте пользовательское свойство в элемент проекта. Свойство отображается в окне **Свойства** при выборе элемента проекта в **Обозреватель решений**. Дополнительные сведения см. [в разделе инструкции. Добавление свойства в расширение элемента проекта SharePoint](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md).

  Пошаговое руководство, в котором показано, как создать, развернуть и проверить расширение элемента проекта, см. в разделе [Пошаговое руководство. расширение типа элемента проекта SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md).

## <a name="understand-the-relationship-between-project-item-extensions-and-project-item-instances"></a>Общие сведения о связи между расширениями элементов проекта и экземплярами элементов проектов
 При создании расширения элемента проекта Visual Studio загружает расширение, когда элемент проекта связанного типа добавляется в проект SharePoint. Например, если создать расширение для элементов проекта **приемника событий** , Visual Studio загрузит расширение, когда пользователь добавит в проект элемент проекта **приемника событий** . Visual Studio использует один и тот же экземпляр расширения для всех экземпляров связанного типа элемента проекта. В предыдущем примере, если пользователь добавляет второй элемент проекта **приемника событий** в проект, то для настройки второго элемента проекта используется тот же экземпляр расширения.

 Чтобы получить доступ к определенному экземпляру типа элемента проекта, который вы расширяете, обработайте одно из <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> событий параметра *прожектитемтипе* в реализации <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> метода. Например, чтобы определить, когда элемент проекта расширяемого типа добавляется в проект, обработайте <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> событие. Дополнительные сведения см. [в разделе инструкции. Создание расширения элемента проекта SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).

## <a name="identifiers-for-sharepoint-project-items"></a>Идентификаторы для элементов проектов SharePoint
 Каждый элемент проекта SharePoint имеет соответствующий строковый идентификатор. Если необходимо выполнить следующие задачи, необходимо получить идентификатор для элемента проекта.

- Создайте расширение для элемента проекта. В этом случае необходимо передать идентификатор элемента проекта, который требуется расширить, в конструктор объекта <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> . Чтобы создать расширение для всех типов элементов проекта, передайте **\\** значение * String.

- Программное добавление элемента проекта в проект. В этом случае необходимо передать в метод идентификатор элемента проекта <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemCollection.Add%2A> .

  В следующей таблице перечислены идентификаторы элементов проектов SharePoint, которые входят в состав Visual Studio.

|Имя элемента проекта|Идентификатор строки|
|-----------------------|-----------------------|
|Модель каталога бизнес-данных|Microsoft. VisualStudio. SharePoint. BusinessDataConnectivity|
|Тип содержимого|Microsoft. VisualStudio. SharePoint. ContentType|
|Приемник событий|Microsoft. VisualStudio. SharePoint. EventHandler|
|Пустой элемент|Microsoft. VisualStudio. SharePoint. Женерицелемент|
|Определение списка<br /><br /> Определение списка из типа содержимого|Microsoft. VisualStudio. SharePoint. Листдефинитион|
|Экземпляр списка|Microsoft. VisualStudio. SharePoint. ListInstance|
|Модуль|Microsoft. VisualStudio. SharePoint. Module|
|Последовательный рабочий процесс<br /><br /> Рабочий процесс конечного компьютера|Microsoft. VisualStudio. SharePoint. Workflow|
|Определение сайта|Microsoft. VisualStudio. SharePoint. Ситедефинитион|
|Визуальная веб-часть|Microsoft. VisualStudio. SharePoint. Висуалвебпарт|
|Веб-часть|Microsoft. VisualStudio. SharePoint. WebPart|
|Форма сопоставления рабочего процесса|Microsoft. VisualStudio. SharePoint. ВоркфловассоЦиатион|

## <a name="see-also"></a>См. также раздел
- [Как создать расширение элемента проекта SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)
- [Как добавить пункт контекстного меню в расширение элемента проекта SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)
- [Как добавить свойство в расширение элемента проекта SharePoint](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)
- [Пошаговое руководство. расширение типа элемента проекта SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)
- [Расширение системы проектов SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
