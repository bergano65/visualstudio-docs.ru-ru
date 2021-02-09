---
title: Решения PowerPoint
description: Узнайте, что Visual Studio предоставляет шаблоны проектов, которые можно использовать для создания надстроек VSTO для Microsoft PowerPoint.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office solutions [Office development in Visual Studio], PowerPoint
- templates [Office development in Visual Studio], PowerPoint
- solutions [Office development in Visual Studio], PowerPoint
- projects [Office development in Visual Studio], PowerPoint
- PowerPoint [Office development in Visual Studio]
- Office projects [Office development in Visual Studio], PowerPoint
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 4033c3fbae9aaefdc094d94d3a4ba70b67d40bf5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99891908"
---
# <a name="powerpoint-solutions"></a>Решения PowerPoint
  Visual Studio предоставляет шаблоны проектов, которые можно использовать для создания надстроек VSTO для Microsoft Office PowerPoint. Вы можете использовать надстройки VSTO для автоматизации PowerPoint, расширения и настройки пользовательского интерфейса PowerPoint.

 Дополнительные сведения о надстройках VSTO см. в статье Приступая к [программированию надстроек VSTO](getting-started-programming-vsto-add-ins.md) и [Архитектура надстроек VSTO](architecture-of-vsto-add-ins.md). Если вы не знакомы с программированием с Microsoft Office, см. статью Приступая к [работе &#40;разработке решений Office в Visual Studio&#41;](getting-started-office-development-in-visual-studio.md).

 [!INCLUDE[appliesto_pptallapp](includes/appliesto-pptallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="automate-powerpoint-by-using-the-powerpoint-object-model"></a>Автоматизация PowerPoint с помощью объектной модели PowerPoint
 Объектная модель Word предоставляет различные типы, которые можно использовать для автоматизации Word. С их помощью можно написать код для выполнения распространенных задач:

- программное создание и форматирование презентаций;

- добавление и удаление слайдов из презентаций;

- добавление и изменение фигур на слайде.

  Чтобы получить доступ к объектной модели PowerPoint из надстройки VSTO, используйте `Application` поле `ThisAddIn` класса в проекте. `Application`Поле возвращает объект [приложения](/previous-versions/office/developer/office-2010/ff764034(v=office.14)) , представляющий текущий экземпляр PowerPoint. Дополнительные сведения см. в разделе [программирование VSTO Add-ins](programming-vsto-add-ins.md).

  При вызове объектной модели PowerPoint используются типы, предоставляемые в основной сборке взаимодействия для PowerPoint. Основная сборка взаимодействия представляет собой мост между управляемым кодом в надстройке VSTO и объектной моделью COM в PowerPoint. Все типы в основной сборке взаимодействия PowerPoint определяются в пространстве имен [Microsoft. Office. Interop. PowerPoint](/previous-versions/office/developer/office-2010/ff763170(v=office.14)) . Дополнительные сведения о первичных сборках взаимодействия см. в статье [Общие сведения о разработке решений Office &#40;VSTO&#41;](office-solutions-development-overview-vsto.md) и [основные сборки взаимодействия Office](office-primary-interop-assemblies.md).

## <a name="use-the-powerpoint-object-model-documentation"></a><a name="WordOMDocumentation"></a> Использование документации по объектной модели PowerPoint
 Полные сведения об объектной модели PowerPoint см. в справочнике по основной сборке взаимодействия PowerPoint и в справочнике по объектной модели VBA.

### <a name="primary-interop-assembly-reference"></a>Ссылка на основную сборку взаимодействия
 В справочной документации по основной сборке взаимодействия PowerPoint описываются типы основной сборки взаимодействия для PowerPoint. Эта документация доступна по следующему адресу: [Справочник по основной сборке взаимодействия PowerPoint 2010](office-primary-interop-assemblies.md).

 Дополнительные сведения о проектировании основных сборок взаимодействия PowerPoint, таких как различия между классами и интерфейсами в основной сборке взаимодействия и способ реализации событий в PIA, см. [в разделе Общие сведения о классах и интерфейсах в основных сборках взаимодействий Office](/previous-versions/office/developer/office-2010/ff759900(v=office.14)).

### <a name="vba-object-model-reference"></a>Справочник по объектной модели VBA
 В справочных документах по объектной модели VBA объектная модель PowerPoint описана в том виде, в котором она предоставляется коду Visual Basic для приложений. Дополнительные сведения см. в [справочнике по объектной модели PowerPoint 2010](/office/vba/api/overview/PowerPoint/object-model).

 Все объекты и элементы в справочнике объектной модели VBA соответствуют типам и членам основной сборки взаимодействия PowerPoint. Например, объект представления в справочнике по объектной модели VBA соответствует типу [представления](/previous-versions/office/developer/office-2010/ff761925(v=office.14)) в основной сборке взаимодействия PowerPoint. Несмотря на то что в справочнике по объектной модели VBA содержатся примеры кода для большинства свойств, методов и событий, необходимо преобразовать код VBA в этом справочнике в код Visual Basic или Visual C#, если требуется использовать его в проекте надстройки VSTO для PowerPoint, создаваемом с помощью Visual Studio.

## <a name="customize-the-user-interface-of-powerpoint"></a>Настройка пользовательского интерфейса PowerPoint
 Пользовательский интерфейс PowerPoint можно изменить следующими способами.

|Задача|Дополнительные сведения|
|----------|--------------------------|
|Создание настраиваемой области задач.|[Настраиваемые области задач](custom-task-panes.md)|
|Добавление настраиваемых вкладок на ленту.|[Общие сведения о ленте](ribbon-overview.md)|
|Добавление настраиваемых групп на встроенную вкладку на ленте.|[Как настроить встроенную вкладку](how-to-customize-a-built-in-tab.md)|

 Дополнительные сведения о настройке пользовательского интерфейса PowerPoint и других Microsoft Office приложений см. в разделе [Настройка пользовательского интерфейса Office](office-ui-customization.md).

## <a name="see-also"></a>См. также раздел
- [Пошаговое руководство. Создание первой надстройки VSTO для PowerPoint](walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)
- [Приступая к программированию надстроек VSTO](getting-started-programming-vsto-add-ins.md)
- [Общие сведения о разработке решений Office &#40;VSTO&#41;](office-solutions-development-overview-vsto.md)
- [Architecture of VSTO Add-ins](architecture-of-vsto-add-ins.md)
- [Как создавать проекты Office в Visual Studio](how-to-create-office-projects-in-visual-studio.md)
- [Программирование надстроек VSTO](programming-vsto-add-ins.md)
- [Написание кода в решениях Office](writing-code-in-office-solutions.md)
- [Основные сборки взаимодействия Office](office-primary-interop-assemblies.md)
- [Настройка пользовательского интерфейса Office](office-ui-customization.md)
- [PowerPoint 2010 в разработке решений для Office](/previous-versions/office/developer/office-2010/ff604967(v=office.14))
