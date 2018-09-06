---
title: Решения проектов
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9be194bb2812f46163a6844a9fa038ee79b5f0e7
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2018
ms.locfileid: "35675159"
---
# <a name="project-solutions"></a>Решения проектов
  [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] предоставляет шаблоны проектов, которые можно использовать для создания надстроек VSTO для Microsoft Office Project. Надстройки VSTO можно использовать для автоматизации Project, расширения функциональных возможностей этого продукта и настройки его пользовательского интерфейса.  
  
 Дополнительные сведения о надстройках VSTO см. в разделе [приступить к программированию надстроек VSTO](../vsto/getting-started-programming-vsto-add-ins.md) и [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md). Если вы не знакомы с программированием Microsoft Office, см. в разделе [приступить к работе &#40;разработка решений Office в Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md).  
  
 [!INCLUDE[appliesto_projallapp](../vsto/includes/appliesto-projallapp-md.md)]  
  
> [!NOTE]  
>  Занимаетесь разработкой решений, расширяющих возможности Office по [нескольких платформ](https://dev.office.com/add-in-availability)? Ознакомьтесь с новой [модель надстроек Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Надстройки Office имеют небольшого размера, по сравнению с надстройками VSTO и решения, и вы можете создавать их с помощью почти любой технологии веб-программирования, таких как HTML5, JavaScript, CSS3 и XML.  
  
## <a name="automate-project-by-using-the-project-object-model"></a>Автоматизация проекта с помощью объектной модели project  
 Объектная модель Project предоставляет различные типы, которые можно использовать для автоматизации Project. Эти типы позволяют создавать код для выполнения общих задач, таких как программное создание и изменение задач в проекте.  
  
 Чтобы получить доступ к объектной модели Project из надстройки VSTO, используйте `Application` поле `ThisAddIn` в своем проекте. `Application` Возвращает `Microsoft.Office.Interop.MsProject.Application` , представляющий текущий экземпляр Project. Дополнительные сведения см. в разделе [программы VSTO Add-ins](../vsto/programming-vsto-add-ins.md).  
  
 При вызове объектной модели Project используются типы, предоставляемые в основной сборке взаимодействия для Project. Основная сборка взаимодействия представляет собой мост между управляемым кодом в надстройке VSTO и объектной моделью COM в Project. Все типы в основной сборке взаимодействия Project определены в `Microsoft.Office.Interop.MSProject` пространства имен. Дополнительные сведения об основных сборках взаимодействия см. в разделе [Общие сведения о разработке решений Office &#40;VSTO&#41; ](../vsto/office-solutions-development-overview-vsto.md) и [основных сборок взаимодействия Office](../vsto/office-primary-interop-assemblies.md).  
  
## <a name="use-the-project-object-model-documentation"></a>Использование документации по объектной модели проекта  
 Полные сведения об объектной модели Project см. в справочнике по объектной модели Project VBA. В справочных документах по объектной модели VBA объектная модель Project описана в том виде, в котором она предоставляется коду Visual Basic для приложений. Дополнительные сведения см. в разделе [Справочник по объектной модели Project 2010](http://go.microsoft.com/fwlink/?LinkId=199771).  
  
 Все объекты и элементы в справочнике объектной модели VBA соответствуют типам и членам основной сборки взаимодействия Project. Например, объект календаря в справочнике по объектной модели VBA соответствует `Microsoft.Office.Interop.MSProject.Calendar` тип в основной сборке ВЗАИМОДЕЙСТВИЯ Project. Несмотря на то, что объектной модели VBA содержатся примеры кода для большинства свойств, методов и событий, необходимо преобразовать код VBA в этом справочнике в Visual Basic или Visual C#, если вы хотите использовать их в проекте надстройки VSTO проект, созданный с помощью Visual Studio.  
  
> [!NOTE]  
>  В настоящее время справочная документация по основной сборке взаимодействия Project отсутствует.  
  
### <a name="infrastructure-types-in-the-project-primary-interop-assembly"></a>Типы инфраструктуры в основной сборке взаимодействия project  
 При написании кода, использующего основную сборку взаимодействия Project, можно заметить, что многие типы не описаны в справочнике по VBA. Эти дополнительные типы, используемые для преобразования объектов в объектной модели COM Project в управляемый код, не предназначены для непосредственного использования в коде.  
  
 Дополнительные сведения см. в разделе [Общие сведения о классах и интерфейсах в основных сборках взаимодействия Office](http://go.microsoft.com/fwlink/?LinkId=189592).  
  
## <a name="customize-the-user-interface-of-project"></a>Настройка пользовательского интерфейса project  
 Пользовательский интерфейс Project можно настраивать следующими способами.  
  
|Задача|Дополнительные сведения|  
|----------|--------------------------|  
|Добавление настраиваемых вкладок на ленту в Project.|[Обзор ленты](../vsto/ribbon-overview.md)|  
  
 Дополнительные сведения о настройке пользовательского интерфейса Project и других приложений Microsoft Office, см. в разделе [настройки пользовательского интерфейса Office](../vsto/office-ui-customization.md).  
  
## <a name="see-also"></a>См. также  
 [Пошаговое руководство по Созданию вашей первой надстройки VSTO для проекта](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)   
 [Приступить к программированию надстроек VSTO](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Общие сведения о разработке решений Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Архитектура надстроек VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Практическое: Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Программирование надстроек VSTO](../vsto/programming-vsto-add-ins.md)   
 [Написание кода в решениях Office](../vsto/writing-code-in-office-solutions.md)   
 [Основные сборки взаимодействия Office](../vsto/office-primary-interop-assemblies.md)   
 [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md)   
 [Project 2010 и Project Server 2010 при разработке решений Office](http://go.microsoft.com/fwlink/?LinkId=199016)  
  
  