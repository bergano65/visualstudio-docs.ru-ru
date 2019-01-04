---
title: решения Outlook
ms.date: 02/02/2017
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6c1849a832bcc2bda8ea63b9939968ea44f5cd5b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53868700"
---
# <a name="outlook-solutions"></a>решения Outlook
  Visual Studio предоставляет шаблоны проектов, которые можно использовать для создания надстроек VSTO для Microsoft Office Outlook. Надстройки VSTO можно использовать для автоматизации Outlook, расширения его функциональных возможностей и настройки пользовательского интерфейса Outlook. Дополнительные сведения о надстройках VSTO см. в разделе [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
> [!NOTE]  
>  Занимаетесь разработкой решений, расширяющих возможности Office по [нескольких платформ](https://dev.office.com/add-in-availability)? Ознакомьтесь с новой [модель надстроек Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Надстройки Office имеют небольшого размера, по сравнению с надстройками VSTO и решения, и вы можете создавать их с помощью почти любой технологии веб-программирования, таких как HTML5, JavaScript, CSS3 и XML.  
  
## <a name="create-an-outlook-vsto-add-in-project"></a>Создайте проект надстройки VSTO Outlook  
 Проекты Outlook создаются с помощью шаблона проекта **Надстройки Outlook** в диалоговом окне **Создание проекта** . Этот шаблон включает в себя необходимые ссылки на сборки и файлы проекта.  
  
 Дополнительные сведения о том, как создать проект надстройки VSTO см. в разделе [как: Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Дополнительные сведения о шаблонах проектов см. в разделе [Общие сведения о шаблонах проектов Office](../vsto/office-project-templates-overview.md).  
  
## <a name="outlook-vsto-add-in-programming-model"></a>Outlook надстройками VSTO модели программирования  
 При создании проекта надстройки VSTO для Outlook Visual Studio создает класс с именем `ThisAddIn`, который служит базой для вашего решения. Этот класс служит отправной точкой для написания собственного кода, а также предоставляет объектную модель Outlook для надстройки.  
  
 Дополнительные сведения о `ThisAddIn` класса и другие функции, можно использовать в надстройке VSTO, см. в разделе [программы VSTO Add-ins](../vsto/programming-vsto-add-ins.md).  
  
## <a name="automate-outlook-by-using-the-outlook-object-model"></a>Автоматизация Outlook с помощью объектной модели Outlook  
 Объектная модель Outlook предоставляет различные типы, которые можно использовать для автоматизации Outlook. С их помощью можно написать код для выполнения распространенных задач:  
  
- программное создание и отправка электронных сообщений;  
  
- отправка новых приглашений на собрание;  
  
- поиск элементов в папках Outlook.  
  
  Дополнительные сведения см. в разделе [обзор объектной модели Outlook](../vsto/outlook-object-model-overview.md).  
  
## <a name="customize-the-user-interface-of-an-outlook-application"></a>Настройка пользовательского интерфейса приложения Outlook  
  
|Задача|Дополнительные сведения|  
|----------|--------------------------|  
|Добавление пользовательских вкладок на ленту инспектора Outlook.|[Обзор ленты](../vsto/ribbon-overview.md)|  
|Добавление настраиваемых групп на встроенную вкладку инспектора Outlook.|[Практическое руководство. Настройка встроенной вкладки](../vsto/how-to-customize-a-built-in-tab.md)|  
|Добавление настраиваемой области задач, которая отображается в окне инспектора Outlook.|[Настраиваемые области задач](../vsto/custom-task-panes.md).|  
|Добавление области формы, расширяющей или заменяющей существующие формы Outlook.|[Создание областей форм Outlook](../vsto/creating-outlook-form-regions.md)|  
  
 Дополнительные сведения о настройке пользовательского интерфейса Outlook и других приложений Microsoft Office, см. в разделе [настройки пользовательского интерфейса Office](../vsto/office-ui-customization.md).  
  
## <a name="related-topics"></a>См. также  
  
|Заголовок|Описание|  
|-----------|-----------------|  
|[Обзор объектной модели Outlook](../vsto/outlook-object-model-overview.md)|Обзор объектов, предоставляемых объектной моделью Outlook.|  
|[Создание областей форм Outlook](../vsto/creating-outlook-form-regions.md)|Описание средств Visual Studio, которые упрощают процесс проектирования, разработки и отладки областей формы.|  
|[Пошаговое руководство: Создание вашей первой надстройки VSTO для Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)|Здесь показано, как создать надстройку VSTO для Microsoft Office Outlook.|  
|[Outlook 2010 при разработке решений Office](http://go.microsoft.com/fwlink/?LinkId=199013)|Раздел библиотеки MSDN, содержащий статьи и справочную документацию по разработке решений для Outlook (не только с помощью Visual Studio).|  
