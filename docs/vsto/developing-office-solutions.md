---
title: Разработка решений Office
description: Сведения о проектировании проекта с помощью средств разработчика Office в Visual Studio. Также Узнайте, как приступить к реализации кода и пользовательского пользовательского интерфейса.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, about developing solutions
- solutions [Office development in Visual Studio], developing
- Office solutions [Office development in Visual Studio], developing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 012f08b4a4a8364d278322b7fe057231183fa233
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99897584"
---
# <a name="develop-office-solutions"></a>Разработка решений Office
  После разработки проекта с помощью Office Developer Tools в Visual Studio и настройки файлов проекта можно начать реализовывать код и пользовательский интерфейс.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="office-solutions-programming-model"></a>Модель программирования решений Office
 Объектная модель Office предоставляет широкий набор объектов, которые можно использовать. При программировании решений Office с помощью управляемого кода вы создаете код, который использует типы в основных сборках взаимодействия Office. В решениях, создаваемых с помощью шаблонов проектов Office в Visual Studio, также можно разрабатывать код непосредственно для созданных классов в своем проекте. Дополнительные сведения см. [в статье написание кода в решениях Office](../vsto/writing-code-in-office-solutions.md).

## <a name="program-different-types-of-office-solutions"></a>Программирование различных типов решений Office
 Тип создаваемого решения определяет, какие функции можно использовать в проекте. Например, элементы управления Windows Forms и расширенные элементы управления Office (которые называются *элементы управления ведущего приложения*) можно добавлять в настройки на уровне документа путем перетаскивания элементов из **панели элементов** в Visual Studio во время разработки. Однако при разработке надстройки VSTO можно только добавлять эти элементы управления в документы во время выполнения путем написания кода.

 Дополнительные сведения о функциях, характерных для различных типов решений, см. в следующих статьях:

- [Программирование надстроек VSTO](../vsto/programming-vsto-add-ins.md).

- [Программы настройки на уровне документа](../vsto/programming-document-level-customizations.md).

- [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md).

  Общие сведения о планировании решений и процедур Office, помогающих в создании проектов, см. в статье [Разработка и создание решений Office](../vsto/designing-and-creating-office-solutions.md).

## <a name="related-topics"></a>См. также

|Заголовок|Описание|
|-----------|-----------------|
|[Написание кода в решениях Office](../vsto/writing-code-in-office-solutions.md)|Описание различных аспектов написания кода в решениях Office.|
|[Программирование надстроек VSTO](../vsto/programming-vsto-add-ins.md)|Общие сведения о модели программирования надстроек VSTO и связанных задачах программирования.|
|[Программы настройки на уровне документа](../vsto/programming-document-level-customizations.md)|Общие сведения о модели программирования настроек на уровне документа и связанных задачах программирования.|
|[Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md)|Описание различных способов настройки пользовательского интерфейса приложений Office с помощью надстроек VSTO и настроек на уровне документа.|
|[Данные в решениях Office](../vsto/data-in-office-solutions.md)|Описание различных способов работы с данными в решениях Office, например, привязки данных к элементам управления и кэширования данных в настройках на уровне документа.|
|[Как автосохранение влияет на решения Office](./how-autosave-impacts-office-solutions.md)|Описывает корректировки, которые могут потребоваться в решениях Office при включенном автосохранении.|
|[Устранение неполадок решений Office](../vsto/troubleshooting-office-solutions.md)|Советы по решению типичных проблем, которые могут происходить при создании решений Office.|
|[Поддержка потоков в Office](../vsto/threading-support-in-office.md)|Общие сведения о работе с несколькими потоками в решениях Office.|
|[Специальные возможности в проектах Office](../vsto/accessibility-in-office-projects.md)|Описание специальных возможностей, доступных в решениях Office.|

## <a name="see-also"></a>См. также раздел
- [Как создавать и изменять пользовательские свойства документа](../vsto/how-to-create-and-modify-custom-document-properties.md)
- [Руководство. чтение и запись в свойства документа](../vsto/how-to-read-from-and-write-to-document-properties.md)
- [Как ориентироваться на многоязыковой пользовательский интерфейс Office](../vsto/how-to-target-the-office-multilingual-user-interface.md)
- [Пошаговое руководство. Создание первой надстройки VSTO для Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)
- [Пошаговое руководство. Создание первой настройки уровня документа для Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)
- [Пошаговое руководство. Создание первой надстройки VSTO для Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)
- [Пошаговое руководство. Создание первой надстройки VSTO для PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)
- [Пошаговое руководство. Создание первой надстройки VSTO для Project](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)
- [Пошаговое руководство. Создание первой надстройки VSTO для Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)
- [Пошаговое руководство. Создание первой настройки уровня документа для Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)
