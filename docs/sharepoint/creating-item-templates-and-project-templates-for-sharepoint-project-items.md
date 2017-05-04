---
title: "Creating Item Templates and Project Templates for SharePoint Project Items | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "SharePoint project items, creating custom templates"
  - ".spdata files"
  - "projects [SharePoint development in Visual Studio], creating custom templates"
  - "SharePoint projects, creating custom templates"
  - "SharePoint development in Visual Studio, creating custom project and item templates"
  - "project items [SharePoint development in Visual Studio], creating custom templates"
ms.assetid: c95b5e35-76c4-4f0a-b645-0467ae683659
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# Creating Item Templates and Project Templates for SharePoint Project Items
  При определении пользовательского типа элемента проекта SharePoint можно связать его с шаблоном элемента или проекта, чтобы другие разработчики могли использовать элемент проекта в Visual Studio.  Также можно создать мастер для шаблона.  
  
 Например, Visual Studio не содержит шаблон проекта или шаблон элемента для добавления поля к сайту SharePoint.  Можно определить тип элемента проекта SharePoint, представляющий поле и формирующий шаблон элемента, который другие разработчики могут использовать для добавления элемента поля в проект SharePoint.  Или можно создать шаблон проекта, чтобы разработчики могли создать новый проект SharePoint, содержащий элемент поля. В обоих случаях можно также предоставить мастер, который появляется, когда разработчики используют ваш шаблон.  Этот мастер может запрашивать информацию у разработчиков для настройки нового элемента или проекта SharePoint.  
  
 Шаблоны элементов и проектов представляют собой ZIP\-файлы, в которых содержатся файлы, используемые Visual Studio для создания проекта или элемента проекта.  Дополнительные сведения об основных принципах работы с шаблонами элементов и проектов см. в разделе [Создание пользовательских шаблонов проектов и элементов в Visual Studio](../ide/creating-project-and-item-templates.md).  
  
##  <a name="creatingitemtemplates"></a> Создание шаблонов элементов  
 При создании шаблона элемента для элемента проекта SharePoint есть файлы, которые требуются всегда, и необязательные файлы, которые могут использоваться некоторыми типами элементов проектов.  Пошаговое руководство по определению типа элемента проекта SharePoint и созданию для него шаблона элемента см. в разделе [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md).  
  
 В следующей таблице приведены файлы, требуемые для создания шаблона элемента для элемента проекта SharePoint.  
  
|Требуемый файлы|Описание|  
|---------------------|--------------|  
|SPDATA\-файл|Это XML\-файл, указывающий содержимое и поведение по умолчанию для элемента проекта.  Этот файл должен содержаться в шаблоне элемента.  Дополнительные сведения о содержимом SPDATA\-файлов см. в разделе [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md).|  
|VSTEMPLATE\-файл.|Этот файл предоставляет системе Visual Studio сведения, необходимые для отображения шаблона в диалоговом окне **Добавление нового элемента** и для создания элемента проекта из шаблона.  Этот файл должен содержаться в шаблоне элемента.  Дополнительные сведения см. в разделе [NIB: Visual Studio Template Metadata Files](http://msdn.microsoft.com/ru-ru/129d59b5-7f9c-4daf-9832-eaedb3c4c961).|  
|Сборка расширения Visual Studio, реализующая интерфейс <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>.|Эта сборка определяет поведение элемента проекта во время выполнения.  Эта сборка должна содержаться в пакете VSIX с шаблоном элемента.  Дополнительные сведения см. в разделах [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md) и [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).|  
  
 В следующем списке приведены некоторые из наиболее типичных необязательных файлов, которые могут содержаться в шаблоне элемента.  Для некоторых типов элементов проектов могут требоваться другие файлы, не указанные здесь.  
  
|Необязательный файл|Описание|  
|-------------------------|--------------|  
|Elements.xml|Файл *Элемент компонента*.  Этот файл определяет пользовательский интерфейс и поведение настройки, созданной элементом проекта.  Каждый тип настройки, такой как экземпляры списков, типы контента или настраиваемые действия, имеют различную схему, определяющую содержимое файла.  Дополнительные сведения см. в разделе [Стандартный блок: Компоненты](http://go.microsoft.com/fwlink/?LinkId=169183) и [Схемы компонента](http://go.microsoft.com/fwlink/?LinkId=169192).|  
|Schema.xml|Файл схемы для определений списка.  Дополнительные сведения см. в разделе [Стандартный блок: Списки и библиотеки документов](http://go.microsoft.com/fwlink/?LinkId=177792) и [Schema.xml](http://go.microsoft.com/fwlink/?LinkId=177793).|  
|.webpart|Файл *Определение веб\-части*.  Этот файл содержит настройки свойства для веб\-части.  Дополнительные сведения см. в разделе [Стандартный блок: Веб\-части](http://go.microsoft.com/fwlink/?LinkId=177791).|  
|ASCX|Файл ASP.NET UserControl.  Этот файл определяет пользовательский интерфейс визуальной веб\-части.|  
|ASPX|Файл страница ASP.NET.  Этот файл содержит разметку XML, которая определяет страницу приложения.|  
|Файлы .cs или .vb|Эти файлы кода определяют поведение настроек SharePoint, содержащих модели программирования, доступ к которым может осуществляться из кода Visual C\# или Visual Basic, такие как страницы приложения, веб\-части и рабочие процессы.|  
  
## Создание шаблонов проектов  
 При создании шаблона проекта SharePoint есть файлы, которые требуются всегда, и необязательные файлы, которые могут использоваться некоторыми типами проектов.  Как правило, проекты SharePoint включают как минимум один элемент проекта SharePoint.  Впрочем, это не обязательно.  Например, можно определить шаблон проекта SharePoint, предназначенный для использования только для развертывания решений SharePoint, созданных в других проектах.  
  
 Пошаговое руководство по определению типа элемента проекта SharePoint и созданию для него шаблона проекта см. в разделе [Пошаговое руководство. Создание элемента проекта столбца сайта с помощью шаблона элемента, часть 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).  
  
 В следующей таблице указаны файлы, которые должны содержаться в шаблоне проекта SharePoint.  
  
|Требуемый файлы|Описание|  
|---------------------|--------------|  
|VSTEMPLATE\-файл|Этот файл предоставляет системе Visual Studio сведения, необходимые для отображения шаблона в диалоговом окне **Новый проект** и для создания проекта из шаблона.  Дополнительные сведения см. в разделе [NIB: Visual Studio Template Metadata Files](http://msdn.microsoft.com/ru-ru/129d59b5-7f9c-4daf-9832-eaedb3c4c961).|  
|CSPROJ\- или VBPROJ\-файл|Это файл проекта.  Он определяет содержимое и параметры конфигурации проекта.|  
|Package.package|Этот файл определяет пакет развертывания для проекта.  При использовании конструктора пакетов для настройки пакета решения для проекта Visual Studio сохраняет данные о пакете решения в файле.<br /><br /> При создании пользовательского шаблона проекта SharePoint в файл Package.package рекомендуется включать минимальное количество необходимого содержимого, а также настраивать пакет решения с помощью интерфейсов API в пространстве имен <xref:Microsoft.VisualStudio.SharePoint.Packages> в расширении, связанном с шаблоном проекта.  В этом случае шаблон проекта защищен от возможных изменений в структуре файла Package.package.  Пример Package.package файла с минимально необходимым содержимым см. в разделе [Пошаговое руководство. Создание элемента проекта столбца сайта с помощью шаблона элемента, часть 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).<br /><br /> При необходимости изменения каталога файла Package.package можно проверить содержимое с помощью схемы, находящейся по адресу %Program Files \(x86\)%\\Microsoft Visual Studio 11.0\\Xml\\Schemas\\PackageModelSchema.xsd.|  
|Package.Template.xml|Этот файл предоставляет основу для файла манифеста решения \(manifest.xml\) для пакета решения SharePoint \(.wsp\), сформированного из проекта.  В этот файл можно добавить содержимое, если следует указать определенное поведение, которое не предполагается изменять в соответствии с типом проекта.  Дополнительные сведения см. в разделе [Стандартный блок: Решения](http://go.microsoft.com/fwlink/?LinkId=169186) и [Схема решения](http://go.microsoft.com/fwlink/?LinkId=177794).<br /><br /> При построении пакета решения из проекта Visual Studio объединяет содержимое файлов Package.package и Package.Template.xml в файл манифеста решения.  Дополнительные сведения о построении пакетов решений см. в разделе [How to: Create a SharePoint Solution Package \(wsp\)](http://msdn.microsoft.com/ru-ru/b24be45c-e91d-49bb-afb0-7b265404214b).|  
  
 В следующей таблице указаны необязательные файлы, которые могут содержаться в шаблоне проекта.  
  
|Дополнительные файлы|Описание|  
|--------------------------|--------------|  
|Элементы проекта SharePoint|Можно добавить один или несколько SPDATA\-файлов, определяющих типы элементов проектов SharePoint.  Для каждого SPDATA\-файла должен быть реализован соответствующий интерфейс <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> в сборке расширения, содержащейся в пакете VSIX вместе с шаблоном проекта.  Дополнительные сведения см. в разделе [Создание шаблонов элементов](#creatingitemtemplates).<br /><br /> Как правило, проекты SharePoint включают как минимум один элемент проекта SharePoint.  Впрочем, это не обязательно.|  
|*featureName*.feature|Этот файл определяет компонент SharePoint, используемый для группировки нескольких элементов проекта для развертывания.  При использовании "Конструктора компонентов" для настройки компонента в проекте, Visual Studio сохраняет данные о компоненте в этом файле.  Для группировки элементов проекта в различных компонентах, можно включить несколько FEATURE\-файлов.<br /><br /> При создании пользовательского шаблона проекта SharePoint в FEATURE\-файл рекомендуется включать минимально необходимое количество содержимого, а также настраивать компоненты с помощью интерфейсов API в пространстве имен <xref:Microsoft.VisualStudio.SharePoint.Features> в расширении, связанном с шаблоном проекта.  В этом случае шаблон проекта защищен от возможных изменений в структуре FEATURE\-файла.  Пример FEATURE\-файла с минимально необходимым содержимым см. в разделе [Пошаговое руководство. Создание элемента проекта столбца сайта с помощью шаблона элемента, часть 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md).<br /><br /> При необходимости изменения каталога FEATURE\-файла можно проверить содержимое с помощью схемы, находящейся по адресу %Program Files \(x86\)%\\Microsoft Visual Studio 11.0\\Xml\\Schemas\\FeatureModelSchema.xsd.|  
|*featureName*.Template.xml|Этот файл предоставляет основу для файла манифеста компонента \(Feature.xml\) для каждого компонента, сформированного из проекта.  В этот файл можно добавить содержимое, если следует указать определенное поведение, которое не предполагается изменять в соответствии с типом проекта.  Дополнительные сведения см. в файлах [Стандартный блок: Компоненты](http://go.microsoft.com/fwlink/?LinkId=169183) и [Feature.xml](http://go.microsoft.com/fwlink/?LinkId=177795).<br /><br /> При построении пакета решения из проекта Visual Studio сливает содержимое каждой пары файлов *featureName*.feature и *featureName*.Template.xml в файл манифеста компонента.  Дополнительные сведения о построении пакетов решений см. в разделе [How to: Create a SharePoint Solution Package \(wsp\)](http://msdn.microsoft.com/ru-ru/b24be45c-e91d-49bb-afb0-7b265404214b).|  
  
## Создание мастеров для шаблонов элементов и проектов  
 После определения типа элемента проекта SharePoint и связывания его с шаблоном элемента или проекта, также можно создать мастер.  Мастер отображается, когда разработчик использует шаблон элемента для добавления элемента проекта SharePoint к проекту, или когда разработчик использует шаблон проекта для создания нового проекта, содержащего элемент проекта SharePoint.  Мастер может быть использован для сбора информации от разработчиков и для инициализации нового элемента проекта SharePoint.  
  
 Пошаговые руководства по созданию шаблонов элементов и проектов см. в разделах [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md) и [Пошаговое руководство. Создание элемента проекта столбца сайта с помощью шаблона элемента, часть 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md).  
  
## См. также  
 [Defining Custom SharePoint Project Item Types](../sharepoint/defining-custom-sharepoint-project-item-types.md)   
 [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)   
 [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)   
 [Пошаговое руководство. Создание элемента проекта столбца сайта с помощью шаблона элемента, часть 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)   
 [Пошаговое руководство. Создание элемента проекта столбца сайта с помощью шаблона элемента, часть 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)   
 [Создание пользовательских шаблонов проектов и элементов в Visual Studio](../ide/creating-project-and-item-templates.md)  
  
  