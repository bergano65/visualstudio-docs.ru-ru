---
title: Решения PowerPoint
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 70968682a8221b88859fd561c9f678aced2911b9
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551473"
---
# <a name="powerpoint-solutions"></a>Решения PowerPoint
  Visual Studio предоставляет шаблоны проектов, которые можно использовать для создания надстроек VSTO для Microsoft Office PowerPoint. Вы можете использовать надстройки VSTO для автоматизации PowerPoint, расширения и настройки пользовательского интерфейса PowerPoint.

 Дополнительные сведения о надстройках VSTO см. в статье Приступая к программированию надстроек [VSTO](../vsto/getting-started-programming-vsto-add-ins.md) и [Архитектура надстроек VSTO](../vsto/architecture-of-vsto-add-ins.md). Если вы не знакомы с программированием с Microsoft Office, см. статью [Начало работы &#40;с Office&#41;Development в Visual Studio](../vsto/getting-started-office-development-in-visual-studio.md).

 [!INCLUDE[appliesto_pptallapp](../vsto/includes/appliesto-pptallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 ![ссылка на видео](../vsto/media/playvideo.gif "ссылка на видео") Связанные демонстрационные видеоролики см [. в разделе разделы справки: Создаете надстройку для Microsoft PowerPoint? ](http://go.microsoft.com/fwlink/?LinkId=132767).

## <a name="automate-powerpoint-by-using-the-powerpoint-object-model"></a>Автоматизация PowerPoint с помощью объектной модели PowerPoint
 Объектная модель Word предоставляет различные типы, которые можно использовать для автоматизации Word. С их помощью можно написать код для выполнения распространенных задач:

- программное создание и форматирование презентаций;

- добавление и удаление слайдов из презентаций;

- добавление и изменение фигур на слайде.

  Чтобы получить доступ к объектной модели PowerPoint из надстройки VSTO, используйте `Application` поле `ThisAddIn` класса в проекте. Поле `Application` возвращает объект [приложения](/previous-versions/office/developer/office-2010/ff764034(v=office.14)), представляющий текущий экземпляр PowerPoint. Дополнительные сведения см. в разделе [программирование VSTO Add-ins](../vsto/programming-vsto-add-ins.md).

  При вызове объектной модели PowerPoint используются типы, предоставляемые в основной сборке взаимодействия для PowerPoint. Основная сборка взаимодействия представляет собой мост между управляемым кодом в надстройке VSTO и объектной моделью COM в PowerPoint. Все типы в основной сборке взаимодействия PowerPoint определяются в пространстве имен [Microsoft. Office. Interop. PowerPoint](/previous-versions/office/developer/office-2010/ff763170(v=office.14)) . Дополнительные сведения о первичных сборках взаимодействия см. в разделе [Общие &#40;сведения&#41; о разработке решений Office VSTO](../vsto/office-solutions-development-overview-vsto.md) и [основные сборки взаимодействия Office](../vsto/office-primary-interop-assemblies.md).

## <a name="WordOMDocumentation"></a>Использование документации по объектной модели PowerPoint
 Полные сведения об объектной модели PowerPoint см. в справочнике по основной сборке взаимодействия PowerPoint и в справочнике по объектной модели VBA.

### <a name="primary-interop-assembly-reference"></a>Ссылка на основную сборку взаимодействия
 В справочной документации по основной сборке взаимодействия PowerPoint описываются типы основной сборки взаимодействия для PowerPoint. Эта документация доступна по следующему адресу: [Справочник по основной сборке взаимодействия PowerPoint 2010](http://go.microsoft.com/fwlink/?LinkId=189588).

 Дополнительные сведения о проектировании основных сборок взаимодействия PowerPoint, таких как различия между классами и интерфейсами в основной сборке взаимодействия и способ реализации событий в PIA, см. [в разделе Общие сведения о классах и интерфейсах в основных сборках взаимодействий Office](http://go.microsoft.com/fwlink/?LinkId=199885).

### <a name="vba-object-model-reference"></a>Справочник по объектной модели VBA
 В справочных документах по объектной модели VBA объектная модель PowerPoint описана в том виде, в котором она предоставляется коду Visual Basic для приложений. Дополнительные сведения см. в [справочнике по объектной модели PowerPoint 2010](http://go.microsoft.com/fwlink/?LinkId=199770).

 Все объекты и элементы в справочнике объектной модели VBA соответствуют типам и членам основной сборки взаимодействия PowerPoint. Например, объект представления в справочнике по объектной модели VBA соответствует типу [представления](/previous-versions/office/developer/office-2010/ff761925(v=office.14)) в основной сборке взаимодействия PowerPoint. Несмотря на то что в справочнике по объектной модели VBA содержатся примеры кода для большинства свойств, методов и событий, необходимо преобразовать код VBA в этом справочнике в код Visual Basic или Visual C#, если требуется использовать его в проекте надстройки VSTO для PowerPoint, создаваемом с помощью Visual Studio.

## <a name="customize-the-user-interface-of-powerpoint"></a>Настройка пользовательского интерфейса PowerPoint
 Пользовательский интерфейс PowerPoint можно изменить следующими способами.

|Задача|Дополнительные сведения|
|----------|--------------------------|
|Создание настраиваемой области задач.|[Настраиваемые области задач](../vsto/custom-task-panes.md)|
|Добавление настраиваемых вкладок на ленту.|[Общие сведения о ленте](../vsto/ribbon-overview.md)|
|Добавление настраиваемых групп на встроенную вкладку на ленте.|[Практическое руководство. Настройка встроенной вкладки](../vsto/how-to-customize-a-built-in-tab.md)|

 Дополнительные сведения о настройке пользовательского интерфейса PowerPoint и других Microsoft Office приложений см. в разделе [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md).

## <a name="see-also"></a>См. также
- [Пошаговое руководство: Создание первой надстройки VSTO для PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)
- [Приступая к программированию надстроек VSTO](../vsto/getting-started-programming-vsto-add-ins.md)
- [Общие сведения о &#40;разработке решений Office VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Архитектура надстроек VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Практическое руководство. Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Программирование надстроек VSTO](../vsto/programming-vsto-add-ins.md)
- [Написание кода в решениях Office](../vsto/writing-code-in-office-solutions.md)
- [Основные сборки взаимодействия Office](../vsto/office-primary-interop-assemblies.md)
- [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md)
- [PowerPoint 2010 в разработке решений для Office](http://go.microsoft.com/fwlink/?LinkId=199015)
