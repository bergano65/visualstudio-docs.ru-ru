---
title: "Архитектура надстроек VSTO"
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
  - "VSTOLoader.dll"
  - "архитектура [разработка решений Office в Visual Studio], надстройки уровня приложения"
  - "vstoee.dll"
  - "надстройки уровня приложения [разработка решений Office в Visual Studio], архитектура"
  - "надстройки [разработка решений Office в Visual Studio], архитектура"
ms.assetid: 978f102f-15c6-44e4-84e8-80b161408324
caps.latest.revision: 70
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 66
---
# Архитектура надстроек VSTO
  Надстройки VSTO, созданные с помощью Office Developer Tools в Visual Studio, имеют архитектурные компоненты, предназначенные для обеспечения стабильности и безопасности и позволяющие им тесно взаимодействовать с Microsoft Office. В этой статье описываются следующие аспекты надстроек VSTO.  
  
-   [Основные сведения о надстройках VSTO](#UnderstandingAddIns)  
  
-   [Компоненты надстроек VSTO](#AddinComponents)  
  
-   [Как надстройки VSTO работают с приложениями Microsoft Office](#HowAddinsWork)  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
 Общие сведения о создании надстроек VSTO см. в разделах [Общие сведения о разработке решений Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md) и [Приступая к программированию надстроек VSTO](../vsto/getting-started-programming-vsto-add-ins.md).  
  
##  <a name="UnderstandingAddIns"></a> Основные сведения о надстройках VSTO  
 При использовании Office Developer Tools в Visual Studio для разработки надстройки VSTO вы создаете сборку управляемого кода, которая загружается приложением Microsoft Office. После загрузки сборки надстройка VSTO может отвечать на события, возникающие в приложении \(например, если пользователь выбирает пункт меню\). Надстройка VSTO также может вызывать объектную модель для автоматизации и расширения приложения. Кроме того, она может использовать любой из классов в [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)].  
  
 Сборка взаимодействует с COM\-компонентами приложения посредством основной сборки взаимодействия приложения. Дополнительные сведения см. в разделах [Основные сборки взаимодействия Office](../vsto/office-primary-interop-assemblies.md) и [Общие сведения о разработке решений Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 Если для приложения установлены несколько надстроек VSTO, каждая надстройка VSTO загружается в свой домен приложения. Это означает, что некорректное поведение одной надстройки VSTO не может привести к сбою других надстроек VSTO. Это также позволяет гарантировать, что при закрытии приложения все сборки надстроек VSTO будут выгружены из памяти. Дополнительные сведения о доменах приложений см. в статье [Домены приложений](http://msdn.microsoft.com/library/113a8bbf-6875-4a72-a49d-ca2d92e19cc8).  
  
> [!NOTE]  
>  Надстройки VSTO, создаваемые с помощью Office Developer Tools в Visual Studio, предназначены для использования только в том случае, когда ведущее приложение Microsoft Office запускается конечным пользователем. Если приложение запускается программным образом \(например, с помощью автоматизации\), надстройка VSTO может не работать должным образом.  
  
##  <a name="AddinComponents"></a> Компоненты надстроек VSTO  
 Несмотря на то что сборка надстройки VSTO является основным компонентом, существует несколько других компонентов, которые сильно влияют на то, как приложения Microsoft Office обнаруживают и загружают надстройки VSTO.  
  
### Записи реестра  
 Приложения Microsoft Office обнаруживают надстройки VSTO путем поиска набора записей реестра. Полный список записей реестра, используемых надстройками VSTO, см. в статье [Записи реестра для надстроек VSTO](../vsto/registry-entries-for-vsto-add-ins.md).  
  
 При сборке вашего решения Visual Studio создает все необходимые записи реестра на компьютере разработчика, что позволяет выполнять отладку надстройки VSTO и запускать ее. Для получения дополнительной информации см. [Построение решений Office](../vsto/building-office-solutions.md).  
  
 Если для развертывания решения используется ClickOnce, программа установки, создаваемая процессом публикации, автоматически создает разделы реестра на компьютере конечного пользователя. Дополнительные сведения см. в разделе [Развертывание решения Office с помощью ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
### Манифест развертывания и манифест приложения  
 Надстройки VSTO используют манифесты развертывания и манифесты приложения для обозначения и загрузки самой последней версии сборки надстройки VSTO. Манифест развертывания указывает на текущий манифест приложения. Манифест приложения указывает на сборку надстройки VSTO и задает класс точки входа для выполнения в сборке. Для получения дополнительной информации см. [Манифесты приложения и развертывания в решениях Office](../vsto/application-and-deployment-manifests-in-office-solutions.md).  
  
### Набор средств Visual Studio для Office \(среда выполнения\)  
 Для запуска надстроек VSTO, созданных с помощью Office Developer Tools в Visual Studio, на компьютерах конечных пользователей должна быть установлена [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Среда выполнения содержит неуправляемые компоненты и набор управляемых сборок. Неуправляемые компоненты загружают сборку надстройки VSTO. Управляемые сборки предоставляют объектную модель, которую ваш код надстройки VSTO использует для автоматизации и расширения ведущего приложения.  
  
 Для получения дополнительной информации см. [Общие сведения об инструментах Visual Studio для среды выполнения Office](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
##  <a name="HowAddinsWork"></a> Как надстройки VSTO работают с приложениями Microsoft Office  
 Когда пользователь запускает приложение Microsoft Office, приложение использует манифест развертывания и манифест приложения для поиска и загрузки последней версии сборки надстройки VSTO. На рисунке ниже показана основная архитектура этих надстроек VSTO.  
  
 ![Архитектура надстройки Office 2007](../vsto/media/office07addin.png "Архитектура надстройки Office 2007")  
  
> [!NOTE]  
>  В решениях Office, ориентированных на [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], решения вызывают объектную модель ведущего приложения с помощью сведений о типах основной сборки взаимодействия, внедренных в сборку решения, а не вызывают непосредственно саму эту сборку. Дополнительные сведения см. в разделе [Проектирование и создание решений Office](../vsto/designing-and-creating-office-solutions.md).  
  
### Процесс загрузки  
 Когда пользователь запускает приложение, происходит следующее:  
  
1.  Приложение проверяет реестр на наличие записей, обозначающих надстройки VSTO, созданные с помощью Office Developer Tools в Visual Studio.  
  
2.  Если приложение находит эти записи реестра, оно загружает файл VSTOEE.dll, который загружает файл VSTOLoader.dll. Эти файлы представляют собой неуправляемые библиотеки DLL и являются компонентами загрузчика для среды выполнения набора средств Visual Studio 2010 для Office. Дополнительные сведения см. в разделе [Общие сведения об инструментах Visual Studio для среды выполнения Office](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
3.  VSTOLoader.dll загружает [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] и запускает управляемую часть среды [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
4.  [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] проверяет наличие обновлений манифестов и загружает последние манифесты приложения и развертывания.  
  
5.  [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] выполняет серию проверок безопасности. Для получения дополнительной информации см. [Обеспечение безопасности решений Office](../vsto/securing-office-solutions.md).  
  
6.  Если надстройка VSTO имеет необходимый уровень доверия для выполнения, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] использует манифест развертывания и манифест приложения для проверки наличия обновлений сборки. Если доступна новая версия сборки, среда выполнения загружает эту версию в кэш [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] на клиентском компьютере. Дополнительные сведения см. в разделе [Развертывание решения Office](../vsto/deploying-an-office-solution.md).  
  
7.  Среда выполнения [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] создает новый домен приложения для загрузки сборки надстройки VSTO.  
  
8.  Среда выполнения [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] загружает сборку надстройки VSTO в домен приложения.  
  
9. Среда выполнения [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] вызывает метод <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> в надстройке VSTO, если он был переопределен.  
  
     При необходимости этот метод можно переопределить, чтобы предоставить объект в надстройке VSTO другим решениям Microsoft Office. Для получения дополнительной информации см. [Вызов кода в надстройках VSTO из других решений Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).  
  
10. Среда выполнения [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] вызывает метод <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> в надстройке VSTO, если он был переопределен.  
  
     При необходимости этот метод можно переопределить для расширения возможностей Microsoft Office путем возврата объекта, который реализует интерфейс расширения. Дополнительные сведения см. в разделе [Настройка функций пользовательского интерфейса с помощью интерфейсов расширяемости](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md).  
  
    > [!NOTE]  
    >  [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] отправляет отдельные вызовы в метод <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> для каждого интерфейса расширения, который поддерживается ведущим приложением. Несмотря на то что первый вызов в метод <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> обычно происходит перед вызовом в метод `ThisAddIn_Startup`, ваша надстройка VSTO не должна делать никаких предположений о том, когда будет вызван метод <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> или сколько раз он будет вызываться.  
  
11. Среда выполнения [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] вызывает метод `ThisAddIn_Startup` в надстройке VSTO. Этот метод является обработчиком событий по умолчанию для события <xref:Microsoft.Office.Tools.AddInBase.Startup>. Для получения дополнительной информации см. [События в проектах Office](../vsto/events-in-office-projects.md).  
  
## См. также  
 [Архитектура решений Office в Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)   
 [Архитектура настроек на уровне документа](../vsto/architecture-of-document-level-customizations.md)   
 [Общие сведения об инструментах Visual Studio для среды выполнения Office](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Приступая к программированию надстроек VSTO](../vsto/programming-vsto-add-ins.md)   
 [Разработка решений Office](../vsto/developing-office-solutions.md)   
 [Обеспечение безопасности решений Office](../vsto/securing-office-solutions.md)   
 [Развертывание решения Office](../vsto/deploying-an-office-solution.md)  
  
  