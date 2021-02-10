---
title: решения InfoPath
description: Узнайте, как можно использовать Visual Studio для создания надстроек VSTO для Microsoft InfoPath 2013 и InfoPath 2010.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], InfoPath
- templates [Office development in Visual Studio], InfoPath
- InfoPath [Office development in Visual Studio]
- Office development in Visual Studio, InfoPath solutions
- projects [Office development in Visual Studio], InfoPath
- Office solutions [Office development in Visual Studio], InfoPath
- Office projects [Office development in Visual Studio], InfoPath
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b3feab4a4b66ed2d6cf96fbccc8aaf1fb7de3bb6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99962370"
---
# <a name="infopath-solutions"></a>решения InfoPath
  Visual Studio предоставляет шаблоны проектов, которые можно использовать для создания надстроек VSTO для Microsoft Office InfoPath 2013 и InfoPath 2010. В Office 2016 InfoPath отсутствует.

> [!NOTE]
> Вы по-прежнему можете создать надстройку VSTO для InfoPath, даже если вы установили Office 2016. Просто установите InfoPath 2013 или Office 2013 параллельно с Office 2016.

 [!INCLUDE[appliesto_infoallapp](../vsto/includes/appliesto-infoallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 Надстройки VSTO для InfoPath похожи на надстройки VSTO для других приложений Microsoft Office. Решения такого типа содержат сборку, которую загружает приложение. Конечные пользователи могут получать доступ к функциям этой сборки, независимо от того, какая форма или шаблон формы открыт. Дополнительные сведения о надстройках VSTO см. в статье Приступая к [программированию надстроек VSTO](../vsto/getting-started-programming-vsto-add-ins.md) и [Архитектура надстроек VSTO](../vsto/architecture-of-vsto-add-ins.md).

> [!NOTE]
> Visual Studio 2015 не содержит проекты шаблонов форм InfoPath, которые присутствовали в предыдущих версиях Visual Studio. Visual Studio 2015 также нельзя использовать для открытия или изменения проекта шаблонов форм InfoPath, который был создан в предыдущей версии Visual Studio. Однако проект шаблонов форм InfoPath можно открыть и изменить с помощью набора средств Visual Studio Tools для работы с приложениями. Дополнительные сведения см [. в статье работа с проектами VSTO 2008 в InfoPath 2010.](/archive/blogs/infopath/working-with-vsto-2008-projects-in-infopath-2010)

## <a name="automate-infopath-by-using-an-add-in"></a>Автоматизация InfoPath с помощью надстройки
 Чтобы получить доступ к объектной модели InfoPath из надстройки VSTO Office, созданной с помощью средств разработки решений на базе Office в Visual Studio, используйте поле `Application` класса `ThisAddIn` в своем проекте. Поле `Application` возвращает объект <xref:Microsoft.Office.Interop.InfoPath.Application> , представляющий текущий экземпляр InfoPath. Дополнительные сведения см. в разделе [программирование VSTO Add-ins](../vsto/programming-vsto-add-ins.md).

 При вызове объектной модели InfoPath из надстройки VSTO используются типы, предоставляемые в основной сборке взаимодействия для InfoPath. Основная сборка взаимодействия представляет собой мост между управляемым кодом в надстройке VSTO и объектной моделью COM в InfoPath. Все типы в основной сборке взаимодействия InfoPath определены в пространстве имен <xref:Microsoft.Office.Interop.InfoPath> . Дополнительные сведения о основной сборке взаимодействия InfoPath см. в разделе [сведения о основной сборке взаимодействия infopath Microsoft Office](/office/client-developer/infopath/external-automation/about-the-microsoft-office-infopath-primary-interop-assembly). Дополнительные сведения о основных сборках взаимодействия см. в статье [Общие сведения о разработке решений office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md) и [основные сборки взаимодействия Office](../vsto/office-primary-interop-assemblies.md).

## <a name="customize-the-user-interface-of-infopath-by-using-an-add-in"></a>Настройка пользовательского интерфейса InfoPath с помощью надстройки
 При создании надстройки VSTO для InfoPath существует несколько различных вариантов настройки пользовательского интерфейса. Некоторые из них указаны в следующей таблице.

|Задача|Дополнительные сведения|
|----------|--------------------------|
|Создание настраиваемой области задач.|[Настраиваемые области задач](../vsto/custom-task-panes.md)|
|Добавление настраиваемых вкладок на ленту в InfoPath.|[Настройка ленты для InfoPath](../vsto/customizing-a-ribbon-for-infopath.md)|

 Дополнительные сведения о настройке пользовательского интерфейса InfoPath и других Microsoft Office приложений см. в разделе [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md).

## <a name="see-also"></a>См. также раздел
- [Сведения о Microsoft Office основной сборке взаимодействия InfoPath](/office/client-developer/infopath/external-automation/about-the-microsoft-office-infopath-primary-interop-assembly)
- [Приступая к программированию надстроек VSTO](../vsto/getting-started-programming-vsto-add-ins.md)
- [Общие сведения о разработке решений Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)
- [Как создавать проекты Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Программирование надстроек VSTO](../vsto/programming-vsto-add-ins.md)
- [Написание кода в решениях Office](../vsto/writing-code-in-office-solutions.md)
- [Основные сборки взаимодействия Office](../vsto/office-primary-interop-assemblies.md)
- [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md)
- [InfoPath 2010 в разработке решений для Office](/previous-versions/office/developer/office-2010/ff604966(v=office.14))