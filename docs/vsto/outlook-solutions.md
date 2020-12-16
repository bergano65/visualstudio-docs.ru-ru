---
title: решения Outlook
description: Узнайте, как можно использовать надстройки VSTO для автоматизации Outlook, расширения функций Outlook или настройки пользовательского интерфейса Outlook.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], Outlook
- Office projects [Office development in Visual Studio], Outlook
- Office solutions [Office development in Visual Studio], Outlook
- templates [Office development in Visual Studio], Outlook
- projects [Office development in Visual Studio], Outlook
- Outlook [Office development in Visual Studio]
- e-mail [Office development in Visual Studio], Outlook solutions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ded4652704a47252f0839aed151f0557ae5e6766
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/15/2020
ms.locfileid: "97527543"
---
# <a name="outlook-solutions"></a>решения Outlook
  Visual Studio предоставляет шаблоны проектов, которые можно использовать для создания надстроек VSTO для Microsoft Office Outlook. Надстройки VSTO можно использовать для автоматизации Outlook, расширения его функциональных возможностей и настройки пользовательского интерфейса Outlook. Дополнительные сведения о надстройках VSTO см. в разделе [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md).

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="create-an-outlook-vsto-add-in-project"></a>Создание проекта надстройки VSTO для Outlook
 Проекты Outlook создаются с помощью шаблона проекта **Надстройки Outlook** в диалоговом окне **Создание проекта** . Этот шаблон включает в себя необходимые ссылки на сборки и файлы проекта.

 Дополнительные сведения о создании проекта надстройки VSTO см. в разделе [как создавать проекты Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Дополнительные сведения о шаблонах проектов см. в разделе [Общие сведения о шаблонах проектов Office](../vsto/office-project-templates-overview.md).

## <a name="outlook-vsto-add-in-programming-model"></a>Модель программирования надстроек VSTO для Outlook
 При создании проекта надстройки VSTO для Outlook Visual Studio создает класс с именем `ThisAddIn`, который служит базой для вашего решения. Этот класс служит отправной точкой для написания собственного кода, а также предоставляет объектную модель Outlook для надстройки.

 Дополнительные сведения о `ThisAddIn` классе и других функциях, которые можно использовать в надстройке VSTO, см. в разделе [программирование VSTO-надстроек](../vsto/programming-vsto-add-ins.md).

## <a name="automate-outlook-by-using-the-outlook-object-model"></a>Автоматизация Outlook с помощью объектной модели Outlook
 Объектная модель Outlook предоставляет различные типы, которые можно использовать для автоматизации Outlook. С их помощью можно написать код для выполнения распространенных задач:

- программное создание и отправка электронных сообщений;

- отправка новых приглашений на собрание;

- поиск элементов в папках Outlook.

  Дополнительные сведения см. в разделе [Общие сведения об объектной модели Outlook](../vsto/outlook-object-model-overview.md).

## <a name="customize-the-user-interface-of-an-outlook-application"></a>Настройка пользовательского интерфейса приложения Outlook

|Задача|Дополнительные сведения|
|----------|--------------------------|
|Добавление пользовательских вкладок на ленту инспектора Outlook.|[Общие сведения о ленте](../vsto/ribbon-overview.md)|
|Добавление настраиваемых групп на встроенную вкладку инспектора Outlook.|[Как настроить встроенную вкладку](../vsto/how-to-customize-a-built-in-tab.md)|
|Добавление настраиваемой области задач, которая отображается в окне инспектора Outlook.|[Настраиваемые области задач](../vsto/custom-task-panes.md).|
|Добавление области формы, расширяющей или заменяющей существующие формы Outlook.|[Создание областей формы Outlook](../vsto/creating-outlook-form-regions.md)|

 Дополнительные сведения о настройке пользовательского интерфейса Outlook и других Microsoft Office приложений см. в разделе [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md).

## <a name="related-topics"></a>См. также

|Заголовок|Описание|
|-----------|-----------------|
|[Общие сведения об объектной модели Outlook](../vsto/outlook-object-model-overview.md)|Обзор объектов, предоставляемых объектной моделью Outlook.|
|[Создание областей формы Outlook](../vsto/creating-outlook-form-regions.md)|Описание средств Visual Studio, которые упрощают процесс проектирования, разработки и отладки областей формы.|
|[Пошаговое руководство. Создание первого Add-In VSTO для Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)|Здесь показано, как создать надстройку VSTO для Microsoft Office Outlook.|
|[Outlook 2010 в разработке решений для Office](/previous-versions/office/developer/office-2010/ff458122(v=office.14))|Раздел библиотеки MSDN, содержащий статьи и справочную документацию по разработке решений для Outlook (не только с помощью Visual Studio).|
