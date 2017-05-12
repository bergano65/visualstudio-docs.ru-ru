---
title: "Настройка функций пользовательского интерфейса с помощью интерфейсов расширяемости"
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
  - "ICustomTaskPaneConsumer - интерфейс"
  - "IRibbonExtensibility - интерфейс"
  - "настройка пользовательского интерфейса [разработка решений Office в Visual Studio]"
  - "пользовательские интерфейсы [разработка решений Office в Visual Studio], настройка"
  - "надстройки уровня приложения [разработка решений Office в Visual Studio], интерфейсы расширяемости"
  - "настройка функций пользовательского интерфейса [разработка решений Office в Visual Studio]"
  - "FormRegionStartup - интерфейс"
  - "надстройки [разработка решений Office в Visual Studio], интерфейсы расширяемости"
  - "интерфейсы расширяемости [разработка решений Office в Visual Studio]"
ms.assetid: 3f3f7908-9404-4eda-8899-4d18c75e3b4a
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# Настройка функций пользовательского интерфейса с помощью интерфейсов расширяемости
  Средства разработки Office в Visual Studio предоставляют классы и конструкторы, которые обрабатывают многие сведения о реализации, когда вы используете их для создания настраиваемых панелей задач, настроек ленты и областей форм Outlook в надстройке VSTO. Однако при наличии особых потребностей вы также можете реализовать *интерфейс расширения* для каждого компонента.  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
## Обзор интерфейсов расширения  
 Microsoft Office определяет набор интерфейсов расширения, реализуемых надстройками VSTO модели COM для настройки определенных компонентов, таких как лента. Эти интерфейсы обеспечивают полный контроль над компонентами, к которым они предоставляют доступ. Тем не менее реализация этих интерфейсов требует некоторого знания принципов взаимодействия с COM в управляемом коде. В некоторых случаях модель программирования этих интерфейсов может быть непонятной для разработчиков, привыкших к .NET Framework.  
  
 При создании надстройки VSTO с помощью шаблонов проектов Office в Visual Studio нет необходимости реализовывать интерфейсы расширения для настройки таких компонентов, как лента.[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] реализует эти интерфейсы без вашего вмешательства. Кроме того, вы можете использовать более понятные классы и конструкторы, предоставляемые Visual Studio. Однако при желании интерфейсы расширения можно реализовать прямо в надстройке VSTO.  
  
 Дополнительные сведения о классах и конструкторах, предоставляемых Visual Studio для этих компонентов, см. в разделах [Настраиваемые области задач](../vsto/custom-task-panes.md), [Конструктор лент](../vsto/ribbon-designer.md) и [Создание областей форм Outlook](../vsto/creating-outlook-form-regions.md).  
  
## Интерфейсы расширения, которые можно реализовать в надстройке VSTO  
 В таблице ниже перечислены интерфейсы расширения, которые можно реализовать, а также поддерживающие их приложения.  
  
|Интерфейс|Описание|Приложения|  
|---------------|--------------|----------------|  
|<xref:Microsoft.Office.Core.IRibbonExtensibility>|Реализуйте этот интерфейс для настройки пользовательского интерфейса ленты. **Note:**  Элемент **Лента \(XML\)** можно добавить в проект для создания реализации <xref:Microsoft.Office.Core.IRibbonExtensibility> по умолчанию в надстройке VSTO. Дополнительные сведения см. в разделе [XML-ленты](../vsto/ribbon-xml.md).|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> InfoPath 2010<br /><br /> Outlook \- приложение<br /><br /> PowerPoint<br /><br /> Проект<br /><br /> Visio<br /><br /> Word|  
|<xref:Microsoft.Office.Core.ICustomTaskPaneConsumer>|Реализуйте этот интерфейс для создания настраиваемой панели задач.|Excel<br /><br /> Outlook \- приложение<br /><br /> PowerPoint<br /><br /> Word|  
|<xref:Microsoft.Office.Interop.Outlook.FormRegionStartup>|Реализуйте этот интерфейс для создания области формы Outlook.|Outlook \- приложение|  
  
 Существуют другие интерфейсы расширения, которые определены Microsoft Office, такие как <xref:Microsoft.Office.Core.IBlogExtensibility>, <xref:Microsoft.Office.Core.EncryptionProvider> и <xref:Microsoft.Office.Core.SignatureProvider>. Visual Studio не поддерживает реализацию этих интерфейсов в надстройке VSTO, созданной с помощью шаблонов проектов Office.  
  
## Использование интерфейсов расширения  
 Чтобы настроить компонент пользовательского интерфейса с помощью интерфейса расширения, реализуйте соответствующий интерфейс в проекте надстройки VSTO. Затем переопределите метод <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> для возврата экземпляра класса, который реализует интерфейс.  
  
 Пример приложения, демонстрирующий реализацию интерфейсов <xref:Microsoft.Office.Core.IRibbonExtensibility>, <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> и <xref:Microsoft.Office.Interop.Outlook.FormRegionStartup> в надстройке VSTO для Outlook, см. в примере диспетчера пользовательского интерфейса в [Примеры разработки решений Office](../vsto/office-development-samples.md).  
  
### Пример реализации интерфейса расширения  
 В следующем примере кода показан пример простой реализации интерфейса <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> для создания настраиваемой панели задач. В данном примере определяются два класса.  
  
-   Класс `TaskPaneHelper` реализует <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> для создания и отображения настраиваемой панели задач.  
  
-   Класс `TaskPaneUI` предоставляет пользовательский интерфейс панели задач. Атрибуты класса `TaskPaneUI` делают его доступным для COM, что позволяет приложениям Microsoft Office обнаруживать класс. В этом примере пользовательский интерфейс представляет собой пустой интерфейс <xref:System.Windows.Forms.UserControl>, однако вы можете добавить элементы управления, изменив код.  
  
    > [!NOTE]  
    >  Чтобы предоставить класс `TaskPaneUI` COM, для проекта необходимо также задать свойство **Регистрация для COM\-взаимодействия**.  
  
 [!code-csharp[Trin_SimpleExtensibilityInterface#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_SimpleExtensibilityInterface/CS/ThisAddIn.cs#1)]
 [!code-vb[Trin_SimpleExtensibilityInterface#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_SimpleExtensibilityInterface/VB/ThisAddIn.vb#1)]  
  
 Дополнительные сведения о реализации <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> см. в разделе [Создание настраиваемых панелей задач в выпуске 2007 системы Office](http://msdn.microsoft.com/ru-ru/256313db-18cc-496c-a961-381ed9ca94be) в документации Microsoft Office.  
  
### Пример переопределения метода RequestService  
 Следующий пример кода демонстрирует переопределение метода <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> для возврата экземпляра класса `TaskPaneHelper` из предыдущего примера кода. Он проверяет значение параметра *serviceGuid*, чтобы определить, какой интерфейс запрашивается, а затем возвращает объект, который реализует интерфейс.  
  
 [!code-csharp[Trin_SimpleExtensibilityInterface#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_SimpleExtensibilityInterface/CS/ThisAddIn.cs#2)]
 [!code-vb[Trin_SimpleExtensibilityInterface#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_SimpleExtensibilityInterface/VB/ThisAddIn.vb#2)]  
  
## См. также  
 [Образцы и пошаговые руководства разработки Office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Приступая к программированию надстроек VSTO](../vsto/programming-vsto-add-ins.md)   
 [Разработка решений Office](../vsto/developing-office-solutions.md)   
 [Вызов кода в надстройках VSTO из других решений Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)   
 [Практическое руководство. Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Архитектура надстроек VSTO](../vsto/architecture-of-vsto-add-ins.md)  
  
  