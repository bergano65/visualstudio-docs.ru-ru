---
title: "Архитектура надстроек VSTO | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VSTOLoader.dll
- architecture [Office development in Visual Studio], application-level add-ins
- vstoee.dll
- application-level add-ins [Office development in Visual Studio], architecture
- add-ins [Office development in Visual Studio], architecture
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: a8abb77978731a9fa5cd43acdcb4928944c605b1
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="architecture-of-vsto-add-ins"></a>Архитектура надстроек VSTO
  Надстройки VSTO, созданные с помощью Office Developer Tools в Visual Studio, имеют архитектурные компоненты, предназначенные для обеспечения стабильности и безопасности и позволяющие им тесно взаимодействовать с Microsoft Office. В этой статье описываются следующие аспекты надстроек VSTO.  
  
-   [Основные сведения о надстройках VSTO](#UnderstandingAddIns)  
  
-   [Компоненты надстроек VSTO](#AddinComponents)  
  
-   [Как надстройки VSTO работают с приложениями Microsoft Office](#HowAddinsWork)  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
 Общие сведения о создании надстроек VSTO см. в разделе [Общие сведения о разработке решений Office &#40; VSTO &#41; ](../vsto/office-solutions-development-overview-vsto.md) и [Приступая к работе Программирование надстроек VSTO](../vsto/getting-started-programming-vsto-add-ins.md).  
  
##  <a name="UnderstandingAddIns"></a> Основные сведения о надстройках VSTO  
 При использовании Office Developer Tools в Visual Studio для разработки надстройки VSTO вы создаете сборку управляемого кода, которая загружается приложением Microsoft Office. После загрузки сборки надстройка VSTO может отвечать на события, возникающие в приложении (например, если пользователь выбирает пункт меню). Надстройка VSTO также может вызывать объектную модель для автоматизации и расширения приложения. Кроме того, она может использовать любой из классов в [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)].  
  
 Сборка взаимодействует с COM-компонентами приложения посредством основной сборки взаимодействия приложения. Дополнительные сведения см. в разделе [основных сборках взаимодействия Office](../vsto/office-primary-interop-assemblies.md) и [Общие сведения о разработке решений Office &#40; VSTO &#41; ](../vsto/office-solutions-development-overview-vsto.md).  
  
 Если для приложения установлены несколько надстроек VSTO, каждая надстройка VSTO загружается в свой домен приложения. Это означает, что некорректное поведение одной надстройки VSTO не может привести к сбою других надстроек VSTO. Это также позволяет гарантировать, что при закрытии приложения все сборки надстроек VSTO будут выгружены из памяти. Дополнительные сведения о доменах приложений см. в разделе [домены приложений](/dotnet/framework/app-domains/application-domains).  
  
> [!NOTE]  
>  Надстройки VSTO, создаваемые с помощью Office Developer Tools в Visual Studio, предназначены для использования только в том случае, когда ведущее приложение Microsoft Office запускается конечным пользователем. Если приложение запускается программным образом (например, с помощью автоматизации), надстройка VSTO может не работать должным образом.  
  
##  <a name="AddinComponents"></a> Компоненты надстроек VSTO  
 Несмотря на то что сборка надстройки VSTO является основным компонентом, существует несколько других компонентов, которые сильно влияют на то, как приложения Microsoft Office обнаруживают и загружают надстройки VSTO.  
  
### <a name="registry-entries"></a>Записи реестра  
 Приложения Microsoft Office обнаруживают надстройки VSTO путем поиска набора записей реестра. Полный список записей реестра, используемых надстройками VSTO см. в разделе [записи реестра для надстроек VSTO](../vsto/registry-entries-for-vsto-add-ins.md).  
  
 При сборке вашего решения Visual Studio создает все необходимые записи реестра на компьютере разработчика, что позволяет выполнять отладку надстройки VSTO и запускать ее. Дополнительные сведения см. в разделе [построение решений Office](../vsto/building-office-solutions.md).  
  
 Если для развертывания решения используется ClickOnce, программа установки, создаваемая процессом публикации, автоматически создает разделы реестра на компьютере конечного пользователя. Дополнительные сведения см. в разделе [развертывание решения Office с помощью ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
### <a name="deployment-manifest-and-application-manifest"></a>Манифест развертывания и манифест приложения  
 Надстройки VSTO используют манифесты развертывания и манифесты приложения для обозначения и загрузки самой последней версии сборки надстройки VSTO. Манифест развертывания указывает на текущий манифест приложения. Манифест приложения указывает на сборку надстройки VSTO и задает класс точки входа для выполнения в сборке. Для получения дополнительной информации см. [Application and Deployment Manifests in Office Solutions](../vsto/application-and-deployment-manifests-in-office-solutions.md).  
  
### <a name="visual-studio-tools-for-office-runtime"></a>Набор средств Visual Studio для Office (среда выполнения)  
 Для запуска надстроек VSTO, созданных с помощью Office Developer Tools в Visual Studio, на компьютерах конечных пользователей должна быть установлена [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Среда выполнения содержит неуправляемые компоненты и набор управляемых сборок. Неуправляемые компоненты загружают сборку надстройки VSTO. Управляемые сборки предоставляют объектную модель, которую ваш код надстройки VSTO использует для автоматизации и расширения ведущего приложения.  
  
 Дополнительные сведения см. в разделе [Visual Studio Tools for Office Runtime Overview](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
##  <a name="HowAddinsWork"></a> How VSTO Add-ins Work with Microsoft Office Applications  
 Когда пользователь запускает приложение Microsoft Office, приложение использует манифест развертывания и манифест приложения для поиска и загрузки последней версии сборки надстройки VSTO. На рисунке ниже показана основная архитектура этих надстроек VSTO.  
  
 ![Архитектура надстройки office 2007](../vsto/media/office07addin.png "Архитектура надстройки Office 2007")  
  
> [!NOTE]  
>  В решениях Office, ориентированных на [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], решения вызывают объектную модель ведущего приложения с помощью сведений о типах основной сборки взаимодействия, внедренных в сборку решения, а не вызывают непосредственно саму эту сборку. Для получения дополнительной информации см. [Designing and Creating Office Solutions](../vsto/designing-and-creating-office-solutions.md).  
  
### <a name="loading-process"></a>Процесс загрузки  
 Когда пользователь запускает приложение, происходит следующее:  
  
1.  Приложение проверяет реестр на наличие записей, обозначающих надстройки VSTO, созданные с помощью Office Developer Tools в Visual Studio.  
  
2.  Если приложение находит эти записи реестра, оно загружает файл VSTOEE.dll, который загружает файл VSTOLoader.dll. Эти файлы представляют собой неуправляемые библиотеки DLL и являются компонентами загрузчика для среды выполнения набора средств Visual Studio 2010 для Office. Для получения дополнительной информации см. [Visual Studio Tools for Office Runtime Overview](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
3.  VSTOLoader.dll загружает [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] и запускает управляемую часть среды [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
4.  [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] проверяет наличие обновлений манифестов и загружает последние манифесты приложения и развертывания.  
  
5.  [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] выполняет серию проверок безопасности. Для получения дополнительной информации см. [Securing Office Solutions](../vsto/securing-office-solutions.md).  
  
6.  Если надстройка VSTO имеет необходимый уровень доверия для выполнения, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] использует манифест развертывания и манифест приложения для проверки наличия обновлений сборки. Если доступна новая версия сборки, среда выполнения загружает эту версию в кэш [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] на клиентском компьютере. Дополнительные сведения см. в разделе [развертывание решения Office](../vsto/deploying-an-office-solution.md).  
  
7.  Среда выполнения [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] создает новый домен приложения для загрузки сборки надстройки VSTO.  
  
8.  Среда выполнения [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] загружает сборку надстройки VSTO в домен приложения.  
  
9. Среда выполнения [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] вызывает метод <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> в надстройке VSTO, если он был переопределен.  
  
     При необходимости этот метод можно переопределить, чтобы предоставить объект в надстройке VSTO другим решениям Microsoft Office. Для получения дополнительной информации см. [Вызов кода в надстройках VSTO из других решений Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).  
  
10. Среда выполнения [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] вызывает метод <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> в надстройке VSTO, если он был переопределен.  
  
     При необходимости этот метод можно переопределить для расширения возможностей Microsoft Office путем возврата объекта, который реализует интерфейс расширения. Дополнительные сведения см. в разделе [Customizing UI Features By Using Extensibility Interfaces](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md).  
  
    > [!NOTE]  
    >  [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] отправляет отдельные вызовы в метод <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> для каждого интерфейса расширения, который поддерживается ведущим приложением. Несмотря на то что первый вызов в метод <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> обычно происходит перед вызовом в метод `ThisAddIn_Startup` , ваша надстройка VSTO не должна делать никаких предположений о том, когда будет вызван метод <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> или сколько раз он будет вызываться.  
  
11. Среда выполнения [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] вызывает метод `ThisAddIn_Startup` в надстройке VSTO. Этот метод является обработчиком событий по умолчанию для события <xref:Microsoft.Office.Tools.AddInBase.Startup> . Дополнительные сведения см. в разделе [Events in Office Projects](../vsto/events-in-office-projects.md).  
  
## <a name="see-also"></a>См. также  
 [Архитектура решений Office в Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)   
 [Архитектура настроек на уровне документа](../vsto/architecture-of-document-level-customizations.md)   
 [Visual Studio Tools for Office Runtime Overview](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [Разработка решений Office](../vsto/developing-office-solutions.md)   
 [Обеспечение безопасности решений Office](../vsto/securing-office-solutions.md)   
 [Развертывание решения Office](../vsto/deploying-an-office-solution.md)  
  
  