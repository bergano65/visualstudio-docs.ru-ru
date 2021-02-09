---
title: Как заполнить документы данными из объектов
description: Узнайте, как можно использовать данные из объекта в решении, а также можно использовать Windows Forms элементы управления для отображения данных в документе.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], populating with data
- data [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 5bebc21fb02f6b5441c597fcfd25364991829e71
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99918580"
---
# <a name="how-to-populate-documents-with-data-from-objects"></a>Как заполнить документы данными из объектов

Доступ к данным в объекте данных в проектах уровня документа Microsoft Office Word осуществляется точно так же, как в проектах Windows Forms. Для получения данных из объекта в решении можно использовать те же средства и компоненты кода. Также можно использовать элементы управления Windows Forms для отображения данных. Кроме того, данные можно показать с помощью элементов управления ведущего приложения. Элементы управления ведущего приложения представляют собой управляемые объекты Microsoft Office Word, дополненные событиями и функциями привязки данных. Дополнительные сведения см. в разделе [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md).

[!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

Чтобы заполнить документ данными из объекта, необходимо выполнить три основных действия:

- добавить в документ элемент управления, который можно привязать к данным;

- добавить данные из объекта в документ;

- подключить объект данных к BindingSource.

## <a name="to-add-a-data-object"></a>Добавление объекта данных

Чтобы добавить объект данных, откройте окно **Источники данных** и создайте источник данных из объекта. Дополнительные сведения см. в разделе [Добавление новых источников данных](../data-tools/add-new-data-sources.md).

## <a name="connect-the-data-object-to-the-bindingsource"></a>Подключение объекта данных к BindingSource

В проектах уровня документа вы добавляете элементы управления в документ и привязываете их к данным во время разработки.

В проектах надстроек VSTO вы создаете элементы управления и привязываете их во время выполнения.

### <a name="document-level-projects"></a>Проекты уровня документа

Чтобы подключить объект данных к BindingSource:

1. Перетащите нужное поле данных из окна **Источники данных** в документ. При этом автоматически создается элемент управления.

2. Создайте в коде экземпляр типа объекта, выбранного в качестве источника данных.

3. Присвойте этот экземпляр свойству <xref:System.Windows.Forms.BindingSource.DataSource%2A> объекта <xref:System.Windows.Forms.BindingSource>.

### <a name="application-level-projects"></a>Проекты уровня приложения

Чтобы подключить объект данных к BindingSource:

1. Создайте в коде экземпляр типа объекта, связанного с источником данных.

2. Создайте экземпляр <xref:System.Windows.Forms.BindingSource>.

3. Присвойте экземпляр источника данных свойству <xref:System.Windows.Forms.BindingSource.DataSource%2A> объекта <xref:System.Windows.Forms.BindingSource>.

4. Добавьте источник данных как привязку данных к элементу управления.

## <a name="see-also"></a>См. также раздел

- [Добавление новых источников данных](../data-tools/add-new-data-sources.md)
- [Привязка элементов управления Windows Forms к данным в Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Как заполнить документы данными из базы данных](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Руководство. Обновление источника данных с помощью данных из элемента управления ведущего приложения](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Общие сведения о компоненте BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview)