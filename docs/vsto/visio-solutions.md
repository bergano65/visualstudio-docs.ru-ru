---
title: Решения Visio | Документы Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a5cf82776989d21be60c38aff280d7f9613327c7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="visio-solutions"></a>Решения Visio
  Visual Studio предоставляет шаблоны проектов, которые можно использовать для создания надстроек VSTO для Microsoft Office Visio. Надстройки VSTO можно использовать для автоматизации Visio, расширения функциональных возможностей этого продукта и настройки его пользовательского интерфейса.  
  
 Дополнительные сведения о надстройках VSTO см. в разделах [Getting Started Programming VSTO Add-ins](../vsto/getting-started-programming-vsto-add-ins.md) и [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md). Если вы не знакомы с программированием для Microsoft Office, см. раздел [Приступая к работе &#40;разработка решений Office в Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md).  
  
 **Применимость.** Информация в этой статье относится к проектам надстроек VSTO для Visio 2010. Дополнительные сведения см. в разделе [Доступность функций по типам приложений Office и проектов](../vsto/features-available-by-office-application-and-project-type.md).  
  
> [!NOTE]  
>  Заинтересованы в разработке решений, расширяющих возможности Office через [нескольких платформ](https://dev.office.com/add-in-availability)? Ознакомьтесь с новой [модель надстроек Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Надстройки Office имеют небольшого размера, по сравнению с надстройками VSTO и решения, и их можно создавать с помощью почти любой технологии веб-программирования, таких как HTML5, JavaScript, CSS3 и XML.  
  
## <a name="automating-visio-by-using-the-visio-object-model"></a>Автоматизация Visio с помощью объектной модели Visio  
 Объектная модель Visio предоставляет различные классы, которые можно использовать для автоматизации Visio с целью создания диаграмм для организационных диаграмм, блок-схем, временных шкал проекта, сетевых диаграмм, пространств Office и проч. Интерфейс API позволяет написать код для выполнения общих задач.  
  
-   Конструирование и размещение фигур и текста в диаграммах.  
  
-   Управление поведением фигур с учетом бизнес-логики и данных, вводимых пользователем.  
  
-   Управление отображением диаграмм, например панорамированием и масштабированием.  
  
-   Настройка пользовательского интерфейса приложения.  
  
-   Импортируйте внешние данные в Visio, свяжите их с фигурами и отобразите в графическом виде на странице.  
  
 Пошаговые инструкции и примеры кода по использованию объектной модели Visio для работы с документами и фигурами см. в разделах [Working with Visio Documents](../vsto/working-with-visio-documents.md) и [Working with Visio Shapes](../vsto/working-with-visio-shapes.md).  
  
 Для доступа к объектной модели Visio из надстройки VSTO используйте поле `Application` класса `ThisAddIn` в своем проекте. `Application` Поле возвращает объект Microsoft.Office.Interop.Visio.Application, который представляет текущий экземпляр Visio. Для получения дополнительной информации см. [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
 При вызове объектной модели Visio используются типы, предоставляемые в основной сборке взаимодействия (PIA) для Visio. Основная сборка взаимодействия выступает в качестве моста между управляемым кодом в надстройке VSTO и объектной моделью COM в Visio. Все типы в основной сборке ВЗАИМОДЕЙСТВИЯ Visio определены в пространстве имен Microsoft.Office.Interop.Visio. Дополнительные сведения об основных сборках взаимодействия см. в разделе [Общие сведения о разработке решений Office &#40;VSTO&#41; ](../vsto/office-solutions-development-overview-vsto.md) и [основных сборках взаимодействия Office](../vsto/office-primary-interop-assemblies.md).  
  
## <a name="visio-object-model-overview"></a>Общие сведения об объектной модели Visio  
 Обзор объектной модели Visio см. в разделе [Visio Object Model Overview](../vsto/visio-object-model-overview.md), который содержит ссылки на справочник по объектной модели Visio и пакеты SDK.  
  
## <a name="customizing-the-user-interface-of-visio"></a>Настройка пользовательского интерфейса Visio  
 Пользовательский интерфейс Visio имеет следующие возможности настройки.  
  
|Задача|Дополнительные сведения|  
|----------|--------------------------|  
|Настройка ленты.|[Обзор ленты](../vsto/ribbon-overview.md)|  
  
 Сведения о настройке пользовательского интерфейса Visio см. в справочной документации по VBA для класса [Visio.UIObject](https://msdn.microsoft.com/library/office/ff765763.aspx) .  
  
## <a name="see-also"></a>См. также  
 [Getting Started Programming VSTO Add-ins](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Общие сведения о разработке решений Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Архитектура надстроек VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Как: Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [Написание кода в решениях Office](../vsto/writing-code-in-office-solutions.md)   
 [Основные сборки взаимодействия Office](../vsto/office-primary-interop-assemblies.md)   
 [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md)   
 [Общие сведения о модели объектов Visio](../vsto/visio-object-model-overview.md)   
 [Visio 2010 при разработке решений Office](http://go.microsoft.com/fwlink/?LinkId=199017)  
  
  