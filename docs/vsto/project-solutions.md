---
title: Решения проекта
description: Узнайте, как можно использовать надстройки VSTO для автоматизации проектов, расширения функций проекта или настройки пользовательского интерфейса проекта.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [Office development in Visual Studio], Project
- Office solutions [Office development in Visual Studio], Project
- Project [Office development in Visual Studio]
- templates [Office development in Visual Studio], Project
- Office projects [Office development in Visual Studio], Project
- solutions [Office development in Visual Studio], Project
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b17ff0312574a4e41b283bd3c631977a834c64c2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99971821"
---
# <a name="project-solutions"></a>Решения проекта
  [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] предоставляет шаблоны проектов, которые можно использовать для создания надстроек VSTO для Microsoft Office Project. Надстройки VSTO можно использовать для автоматизации Project, расширения функциональных возможностей этого продукта и настройки его пользовательского интерфейса.

 Дополнительные сведения о надстройках VSTO см. в статье Приступая к [программированию надстроек VSTO](../vsto/getting-started-programming-vsto-add-ins.md) и [Архитектура надстроек VSTO](../vsto/architecture-of-vsto-add-ins.md). Если вы не знакомы с программированием с Microsoft Office, см. статью Приступая к [работе &#40;разработке решений Office в Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md).

 [!INCLUDE[appliesto_projallapp](../vsto/includes/appliesto-projallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="automate-project-by-using-the-project-object-model"></a>Автоматизация проекта с помощью объектной модели проекта
 Объектная модель Project предоставляет различные типы, которые можно использовать для автоматизации Project. Эти типы позволяют создавать код для выполнения общих задач, таких как программное создание и изменение задач в проекте.

 Чтобы получить доступ к объектной модели проекта из надстройки VSTO, используйте `Application` поле `ThisAddIn` класса в проекте. `Application`Поле возвращает `Microsoft.Office.Interop.MsProject.Application` объект, представляющий текущий экземпляр Project. Дополнительные сведения см. в разделе [программирование VSTO Add-ins](../vsto/programming-vsto-add-ins.md).

 При вызове объектной модели Project используются типы, предоставляемые в основной сборке взаимодействия для Project. Основная сборка взаимодействия представляет собой мост между управляемым кодом в надстройке VSTO и объектной моделью COM в Project. Все типы в основной сборке взаимодействия Project определены в пространстве имен `Microsoft.Office.Interop.MSProject`. Дополнительные сведения о первичных сборках взаимодействия см. в статье [Общие сведения о разработке решений Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md) и [основные сборки взаимодействия Office](../vsto/office-primary-interop-assemblies.md).

## <a name="use-the-project-object-model-documentation"></a>Использование документации по объектной модели Project
 Полные сведения об объектной модели Project см. в справочнике по объектной модели Project VBA. В справочных документах по объектной модели VBA объектная модель Project описана в том виде, в котором она предоставляется коду Visual Basic для приложений. Дополнительные сведения см. в разделе [Справочник по объектной модели проекта](/office/vba/api/project.object).

 Все объекты и элементы в справочнике объектной модели VBA соответствуют типам и членам основной сборки взаимодействия Project. Например, объект Calendar в справочнике по объектной модели VBA соответствует `Microsoft.Office.Interop.MSProject.Calendar` типу в сборке PIA проекта. Несмотря на то, что Справочник по объектной модели VBA содержит примеры кода для большинства свойств, методов и событий, необходимо преобразовать код VBA в этой ссылке в Visual Basic или Visual C#, если вы хотите использовать их в проекте надстройки VSTO проекта, созданном с помощью Visual Studio.

> [!NOTE]
> В настоящее время справочная документация по основной сборке взаимодействия Project отсутствует.

### <a name="infrastructure-types-in-the-project-primary-interop-assembly"></a>Типы инфраструктуры в основной сборке взаимодействия проекта
 При написании кода, использующего основную сборку взаимодействия Project, можно заметить, что многие типы не описаны в справочнике по VBA. Эти дополнительные типы, используемые для преобразования объектов в объектной модели COM Project в управляемый код, не предназначены для непосредственного использования в коде.

 Дополнительные сведения см. в разделе Общие сведения о [классах и интерфейсах в основных сборках взаимодействия Office](/previous-versions/office/office-12/ms247299(v=office.12)).

## <a name="customize-the-user-interface-of-project"></a>Настройка пользовательского интерфейса проекта
 Пользовательский интерфейс Project можно настраивать следующими способами.

|Задача|Дополнительные сведения|
|----------|--------------------------|
|Добавление настраиваемых вкладок на ленту в Project.|[Общие сведения о ленте](../vsto/ribbon-overview.md)|

 Дополнительные сведения о настройке пользовательского интерфейса проекта и других Microsoft Office приложений см. в разделе [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md).

## <a name="see-also"></a>См. также раздел
- [Пошаговое руководство. Создание первой надстройки VSTO для Project](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)
- [Приступая к программированию надстроек VSTO](../vsto/getting-started-programming-vsto-add-ins.md)
- [Общие сведения о разработке решений Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)
- [Как создавать проекты Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Программирование надстроек VSTO](../vsto/programming-vsto-add-ins.md)
- [Написание кода в решениях Office](../vsto/writing-code-in-office-solutions.md)
- [Основные сборки взаимодействия Office](../vsto/office-primary-interop-assemblies.md)
- [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md)
- [Project 2010 и Project Server 2010 при разработке решений для Office](/previous-versions/office/developer/office-2010/ee758031(v=office.14))
