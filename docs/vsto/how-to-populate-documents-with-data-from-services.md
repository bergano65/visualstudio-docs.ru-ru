---
title: Как заполнить документы данными из служб
description: Узнайте, как можно использовать данные из служб в решении, а также как использовать Windows Forms элементы управления для отображения данных в документе.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], populating with data
- Web services [Office development in Visual Studio], populating documents
- data [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 57fdbcef1aaf9c0903a21a2eeb6436ce1fce25d0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99918550"
---
# <a name="how-to-populate-documents-with-data-from-services"></a>Как заполнить документы данными из служб

Доступ к данным в проектах уровня документа для Microsoft Office работает точно так же, как в проектах Windows Forms. Вы используете те же средства и код для получения данных в ваше решение и даже можете отображать данные с помощью элементов управления Windows Forms. Кроме того, можно воспользоваться преимуществами элементов управления ведущего приложения, которые являются собственными объектами в Microsoft Office Excel и Microsoft Office Word, дополненными событиями и функциями привязки данных. Дополнительные сведения см. в разделе [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md).

[!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

В следующем примере показано, как добавить элементы управления с привязкой к данным в документы во время разработки. Пример добавления элементов управления с привязкой к данным в надстройках VSTO во время выполнения см. в разделе [Пошаговое руководство. привязка к данным из службы в проекте надстройки VSTO](../vsto/walkthrough-binding-to-data-from-a-service-in-a-vsto-add-in-project.md).

## <a name="to-populate-a-document-level-project-with-data-from-a-web-service"></a>Заполнение проекта уровня документа данными из веб-службы

1. Откройте окно **Источники данных** и создайте источник данных для проекта. Дополнительные сведения см. в разделе [Добавление новых источников данных](../data-tools/add-new-data-sources.md).

2. Перетащите нужное поле или таблицу из окна **Источники данных** в ваш документ.

     В документе создается элемент управления, создается объект <xref:System.Windows.Forms.BindingSource> , привязанный к классу объекта в проекте, и создаются классы для службы.

3. В коде создайте экземпляр класса веб-службы, к которому вы подключены на шаге 1.

4. Если имеются свойства, необходимые для связи с веб-службой, создайте экземпляры этих свойств.

5. Создайте и отправьте запрос данных с помощью методов, предоставляемых веб-службой, и экземпляров свойств, созданных на шаге 4.

     Используемые методы зависят от того, что предлагает веб-служба.

6. Назначьте ответ данных от веб-службы <xref:System.Windows.Forms.BindingSource.DataSource%2A> свойству объекта <xref:System.Windows.Forms.BindingSource> .

При запуске проекта элемент управления отображает первую запись в источнике данных. Вы можете включить прокрутку записей посредством обработки текущих событий, используя объекты в <xref:System.Windows.Forms.BindingSource>.

## <a name="see-also"></a>См. также раздел

- [Привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Добавление новых источников данных](../data-tools/add-new-data-sources.md)
- [Привязка элементов управления Windows Forms к данным в Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Как заполнить листы данными из базы данных](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [Как заполнить документы данными из объектов](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Как заполнить документы данными из базы данных](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Руководство. Обновление источника данных с помощью данных из элемента управления ведущего приложения](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)