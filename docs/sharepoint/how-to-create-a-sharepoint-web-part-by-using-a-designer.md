---
title: Инструкции. Создание веб-части SharePoint с помощью конструктора | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], designer
- Web Parts [SharePoint development in Visual Studio], adding
- Web Parts [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0830cec748d68f010397c42334a5ed83365ee6b7
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: ru-RU
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016476"
---
# <a name="how-to-create-a-sharepoint-web-part-by-using-a-designer"></a>Инструкции. Создание веб-части SharePoint с помощью конструктора
  Веб-часть можно создать путем добавления **визуального элемента веб-части** в любой проект SharePoint. Откроется конструктор Visual Web Developer в Visual Studio, в котором можно добавить элементы управления и код в веб-часть. Визуальные веб-части работают так же, как и веб-части. Единственное отличие заключается в проектировании визуальных веб-частей в конструкторе Visual Web Developer.

### <a name="to-create-a-project-for-visual-web-parts"></a>Создание проекта для визуальных веб-частей

1. В строке меню выберите **Файл** >**Создать** > **Проект**.

     Откроется диалоговое окно **Новый проект** .

2. В диалоговом окне **Новый проект** в разделе **Visual C#** или **Visual Basic**разверните узел **Office/SharePoint** , а затем выберите категорию **решения SharePoint** .

3. В списке шаблонов проектов выберите **SharePoint 2013 — Визуальная веб-часть**, а затем нажмите кнопку **ОК** .

     Откроется **Мастер настройки SharePoint** .

4. На странице **Укажите сайт и уровень безопасности для отладки** укажите URL-адрес сайта SharePoint, который находится на локальном компьютере, а затем нажмите кнопку **Готово** .

     В **Обозреватель решений**отображается веб-часть. После разработки веб-части в конструкторе Visual Web Developer вы протестируете его на указанном сайте.

### <a name="to-add-a-visual-web-part-to-an-existing-sharepoint-project"></a>Добавление визуальной веб-части в существующий проект SharePoint

1. В строке меню выберите **проект**  >  **Добавить новый элемент**.

2. В диалоговом окне **Добавление нового элемента** выберите узел **Office/SharePoint** .

3. В списке шаблонов проектов выберите **Визуальная веб-часть**, присвойте ей имя, а затем нажмите кнопку **Добавить** .

     В **Обозреватель решений**откроется веб-часть. После разработки веб-части в конструкторе Visual Web Developer вы протестируете его на указанном сайте.

## <a name="see-also"></a>См. также раздел
- [Создание веб-частей для SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
- [Как создать веб-часть SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md)
- [Пошаговое руководство. Создание веб-части для SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)
- [Пошаговое руководство. Создание веб-части для SharePoint с помощью конструктора](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)
