---
title: Решения Visio
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], Visio
- solutions [Office development in Visual Studio], Visio
- Visio [Office development in Visual Studio]
- templates [Office development in Visual Studio], Visio
- projects [Office development in Visual Studio], Visio
- Office solutions [Office development in Visual Studio], Visio
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 41a583b54caa706d0e103bb8652b80a25b6837b7
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2019
ms.locfileid: "54873025"
---
# <a name="visio-solutions"></a>Решения Visio
  Visual Studio предоставляет шаблоны проектов, которые можно использовать для создания надстроек VSTO для Microsoft Office Visio. Надстройки VSTO можно использовать для автоматизации Visio, расширения функциональных возможностей этого продукта и настройки его пользовательского интерфейса.  
  
 Дополнительные сведения о надстройках VSTO см. в разделе [приступить к программированию надстроек VSTO](../vsto/getting-started-programming-vsto-add-ins.md) и [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md). Если вы не знакомы с программированием Microsoft Office, см. в разделе [приступить к работе &#40;разработка решений Office в Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md).  
  
 **Область применения:** Сведения этого раздела применяются к проектам надстроек VSTO для Visio 2010. Дополнительные сведения см. в разделе [Доступность функций по типам приложений Office и проектов](../vsto/features-available-by-office-application-and-project-type.md).  
  
> [!NOTE]  
>  Занимаетесь разработкой решений, расширяющих возможности Office по [нескольких платформ](https://dev.office.com/add-in-availability)? Ознакомьтесь с новой [модель надстроек Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Надстройки Office имеют небольшого размера, по сравнению с надстройками VSTO и решения, и вы можете создавать их с помощью почти любой технологии веб-программирования, таких как HTML5, JavaScript, CSS3 и XML.  
  
## <a name="automate-visio-by-using-the-visio-object-model"></a>Автоматизация Visio с помощью объектной модели Visio  
 Объектная модель Visio предоставляет различные классы, которые можно использовать для автоматизации Visio с целью создания диаграмм для организационных диаграмм, блок-схем, временных шкал проекта, сетевых диаграмм, пространств Office и проч. Интерфейс API позволяет написать код для выполнения общих задач.  
  
- Конструирование и размещение фигур и текста в диаграммах.  
  
- Управление поведением фигур с учетом бизнес-логики и данных, вводимых пользователем.  
  
- Управление отображением диаграмм, например панорамированием и масштабированием.  
  
- Настройка пользовательского интерфейса приложения.  
  
- Импортируйте внешние данные в Visio, свяжите их с фигурами и отобразите в графическом виде на странице.  
  
  Пошаговые инструкции и примеры кода по использованию объектной модели Visio для работы с документами и фигурами [работы с документами Visio](../vsto/working-with-visio-documents.md) и [работать с фигурами Visio](../vsto/working-with-visio-shapes.md).  
  
  Для доступа к объектной модели Visio из надстройки VSTO используйте поле `Application` класса `ThisAddIn` в своем проекте. Поле `Application` возвращает объект `Microsoft.Office.Interop.Visio.Application`, представляющий текущий экземпляр Visio. Дополнительные сведения см. в разделе [программы VSTO Add-ins](../vsto/programming-vsto-add-ins.md).  
  
  При вызове объектной модели Visio используются типы, предоставляемые в основной сборке взаимодействия (PIA) для Visio. Основная сборка взаимодействия выступает в качестве моста между управляемым кодом в надстройке VSTO и объектной моделью COM в Visio. Все типы в основной сборке взаимодействия Visio определены в пространстве имен `Microsoft.Office.Interop.Visio`. Дополнительные сведения об основных сборках взаимодействия см. в разделе [Общие сведения о разработке решений Office &#40;VSTO&#41; ](../vsto/office-solutions-development-overview-vsto.md) и [основных сборок взаимодействия Office](../vsto/office-primary-interop-assemblies.md).  
  
## <a name="visio-object-model-overview"></a>Обзор объектной модели Visio  
 Вы найдете обзор объектной модели Visio [обзор объектной модели Visio](../vsto/visio-object-model-overview.md), который содержит ссылки на Справочник по объектной модели Visio и пакеты SDK.  
  
## <a name="customize-the-user-interface-of-visio"></a>Настройка пользовательского интерфейса Visio  
 Пользовательский интерфейс Visio имеет следующие возможности настройки.  
  
|Задача|Дополнительные сведения|  
|----------|--------------------------|  
|Настройка ленты.|[Обзор ленты](../vsto/ribbon-overview.md)|  
  
 Сведения о настройке пользовательского интерфейса Visio см. в справочной документации по VBA для класса [Visio.UIObject](/office/vba/api/Visio.UIObject) .  
  
## <a name="see-also"></a>См. также  
 [Приступить к программированию надстроек VSTO](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Общие сведения о разработке решений Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)   
 [Практическое руководство. Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Программирование надстроек VSTO](../vsto/programming-vsto-add-ins.md)   
 [Написание кода в решениях Office](../vsto/writing-code-in-office-solutions.md)   
 [Основные сборки взаимодействия Office](../vsto/office-primary-interop-assemblies.md)   
 [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md)   
 [Обзор объектной модели Visio](../vsto/visio-object-model-overview.md)   
 [Visio 2010 при разработке решений Office](http://go.microsoft.com/fwlink/?LinkId=199017)  
