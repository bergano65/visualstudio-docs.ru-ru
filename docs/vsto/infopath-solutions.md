---
title: решения InfoPath
ms.date: 02/02/2017
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 674050711e69ae97c7e1faa361122bee0d755ae7
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56621153"
---
# <a name="infopath-solutions"></a>решения InfoPath
  Visual Studio предоставляет шаблоны проектов, которые можно использовать для создания надстроек VSTO для Microsoft Office InfoPath 2013 и InfoPath 2010. В Office 2016 InfoPath отсутствует.

> [!NOTE]
>  Можно по-прежнему создать надстройку VSTO для InfoPath даже если установлен Office 2016. Просто установите InfoPath 2013 или Office 2013 параллельно с Office 2016.

 [!INCLUDE[appliesto_infoallapp](../vsto/includes/appliesto-infoallapp-md.md)]

> [!NOTE]
>  Занимаетесь разработкой решений, расширяющих возможности Office по [нескольких платформ](https://dev.office.com/add-in-availability)? Ознакомьтесь с новой [модель надстроек Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Надстройки Office имеют небольшого размера, по сравнению с VSTO Add-ins и решения, и вы можете создавать их с помощью почти любой технологии веб-программирования, таких как HTML5, JavaScript, CSS3 и XML.

 Надстройки VSTO для InfoPath похожи на надстройки VSTO для других приложений Microsoft Office. Решения такого типа содержат сборку, которую загружает приложение. Конечные пользователи могут получать доступ к функциям этой сборки, независимо от того, какая форма или шаблон формы открыт. Дополнительные сведения о надстройках VSTO см. в разделе [приступить к программированию надстроек VSTO](../vsto/getting-started-programming-vsto-add-ins.md) и [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md).

> [!NOTE]
>  Visual Studio 2015 не содержит проекты шаблонов форм InfoPath, которые присутствовали в предыдущих версиях Visual Studio. Visual Studio 2015 также нельзя использовать для открытия или изменения проекта шаблонов форм InfoPath, который был создан в предыдущей версии Visual Studio. Однако проект шаблонов форм InfoPath можно открыть и изменить с помощью набора средств Visual Studio Tools для работы с приложениями. Дополнительные сведения см. в разделе [работать с проектами VSTO 2008 в InfoPath 2010.](http://go.microsoft.com/fwlink/?LinkID=218903).

## <a name="automate-infopath-by-using-an-add-in"></a>Автоматизация InfoPath с помощью надстройки
 Чтобы получить доступ к объектной модели InfoPath из надстройки VSTO Office, созданной с помощью средств разработки решений на базе Office в Visual Studio, используйте поле `Application` класса `ThisAddIn` в своем проекте. Поле `Application` возвращает объект <xref:Microsoft.Office.Interop.InfoPath.Application> , представляющий текущий экземпляр InfoPath. Дополнительные сведения см. в разделе [программы VSTO Add-ins](../vsto/programming-vsto-add-ins.md).

 При вызове объектной модели InfoPath из надстройки VSTO, можно использовать типы, предоставляемые в основной сборке взаимодействия для InfoPath. Основная сборка взаимодействия представляет собой мост между управляемым кодом в надстройке VSTO и объектной моделью COM в InfoPath. Все типы в основной сборке взаимодействия InfoPath определены в пространстве имен <xref:Microsoft.Office.Interop.InfoPath> . Дополнительные сведения об основной сборке взаимодействия InfoPath см. в разделе [о Microsoft Office InfoPath основной сборки взаимодействия](https://msdn.microsoft.com/1b3ae03c-6951-49e4-a489-4712d3f7ba72). Как правило, Дополнительные сведения об основных сборках взаимодействия см. в разделе [Общие сведения о разработке решений Office &#40;VSTO&#41; ](../vsto/office-solutions-development-overview-vsto.md) и [основных сборок взаимодействия Office](../vsto/office-primary-interop-assemblies.md).

## <a name="customize-the-user-interface-of-infopath-by-using-an-add-in"></a>Настройка пользовательского интерфейса для InfoPath с помощью надстройки
 При создании надстройки VSTO для InfoPath, у вас есть несколько вариантов настройки пользовательского интерфейса. Некоторые из них указаны в следующей таблице.

|Задача|Дополнительные сведения|
|----------|--------------------------|
|Создание настраиваемой области задач.|[Настраиваемые области задач](../vsto/custom-task-panes.md)|
|Добавление настраиваемых вкладок на ленту в InfoPath.|[Настройка ленты для InfoPath](../vsto/customizing-a-ribbon-for-infopath.md)|

 Дополнительные сведения о настройке пользовательского интерфейса InfoPath и других приложений Microsoft Office, см. в разделе [настройки пользовательского интерфейса Office](../vsto/office-ui-customization.md).

## <a name="see-also"></a>См. также
- [Об основной сборке взаимодействия Microsoft Office InfoPath](https://msdn.microsoft.com/1b3ae03c-6951-49e4-a489-4712d3f7ba72)
- [Приступить к программированию надстроек VSTO](../vsto/getting-started-programming-vsto-add-ins.md)
- [Общие сведения о разработке решений Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Архитектура надстроек VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Практическое руководство. Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Программирование надстроек VSTO](../vsto/programming-vsto-add-ins.md)
- [Написание кода в решениях Office](../vsto/writing-code-in-office-solutions.md)
- [Основные сборки взаимодействия Office](../vsto/office-primary-interop-assemblies.md)
- [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md)
- [InfoPath 2010 при разработке решений Office](http://go.microsoft.com/fwlink/?LinkId=199012)
