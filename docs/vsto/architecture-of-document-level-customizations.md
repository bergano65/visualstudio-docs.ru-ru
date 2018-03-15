---
title: "Архитектура настроек на уровне документа | Документы Microsoft"
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
- formats [Office development in Visual Studio]
- file formats [Office development in Visual Studio]
- vstoee.dll
- managed code extensions [Office development in Visual Studio], definition
- document-level customizations [Office development in Visual Studio]
- AddInLoader.dll
- architecture [Office development in Visual Studio], document-level customizations
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 09a8700086ec8a718e14764f807e57fcb1f882f7
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="architecture-of-document-level-customizations"></a>Архитектура настроек на уровне документа
  [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] является частью настроек на уровне документа для Microsoft Office Word и Microsoft Office Excel. В этой статье описываются следующие аспекты надстроек уровня документа.  
  
-   [Основные сведения о настройках](#UnderstandingCustomizations)  
  
-   [Компоненты настроек](#Components)  
  
-   [Как настройки работают с приложениями Microsoft Office](#HowCustomizationsWork)  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Общие сведения о создании настроек уровня документа см. в разделе [Общие сведения о разработке решений Office &#40; VSTO &#41; ](../vsto/office-solutions-development-overview-vsto.md), [Приступая к программированию настроек на уровне документа для Word](../vsto/getting-started-programming-document-level-customizations-for-word.md), и [Приступая к программированию настроек на уровне документа для Excel](../vsto/getting-started-programming-document-level-customizations-for-excel.md).  
  
##  <a name="UnderstandingCustomizations"></a> Understanding Customizations  
 При использовании инструментов разработчика Office в Visual Studio для построения настройки уровня документа вы создаете сборку управляемого кода, связанную с определенным документом. Документ или книга со связанной сборкой называются имеющими расширения управляемого кода. Для получения дополнительной информации см. [Designing and Creating Office Solutions](../vsto/designing-and-creating-office-solutions.md).  
  
 Когда пользователь открывает документ, сборка загружается приложением Microsoft Office. После загрузки сборки настройка может отвечать на события при открытом документе. Настройка также может обращаться к объектной модели для автоматизации и расширения приложения при открытом документе и использовать любой из классов в [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)].  
  
 Сборка взаимодействует с COM-компонентами приложения посредством основной сборки взаимодействия приложения. Дополнительные сведения см. в разделе [основных сборках взаимодействия Office](../vsto/office-primary-interop-assemblies.md) и [Общие сведения о разработке решений Office &#40; VSTO &#41; ](../vsto/office-solutions-development-overview-vsto.md).  
  
 Если пользователь открывает несколько настроек уровня документа в одно и то же время, то каждая сборка загружается в отдельном домене приложения. Это означает, что некорректное поведение одного решения не может привести к сбою других решений. Настройки уровня документа предназначены для работы с одним документом в одном домене приложений. Они не предназначены для взаимодействия между документами. Дополнительные сведения о доменах приложений см. в разделе [домены приложений](/dotnet/framework/app-domains/application-domains).  
  
> [!NOTE]  
>  Настройки уровня документа, создаваемые с помощью средств разработчика Office в Visual Studio, предназначены для использования только в том случае, когда приложение запускается конечным пользователем. Если приложение запускается программными средствами (например, с помощью автоматизации), настройка может не работать должным образом.  
  
### <a name="design-time-and-run-time-experiences"></a>Взаимодействие во время разработки и во время выполнения  
 Чтобы понимать архитектуру настроек уровня документа, полезно понимать процесс разработки решения и выполнения решения.  
  
#### <a name="design-time"></a>Во время разработки  
 Возможности во время разработки включает следующие шаги.  
  
1.  Разработчик создает проект уровня документа в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Проект включает документ и сборку, выполняющуюся за документом. Документ может уже существовать (возможно, он создан проектировщиком), или можно создать новый документ вместе с проектом.  
  
2.  Проектировщик — разработчик, создающий проект, или кто-то другой — создает окончательный вид и функции документа для конечного пользователя.  
  
#### <a name="run-time"></a>Время выполнения  
 Возможности во время выполнения включают следующие шаги.  
  
1.  Конечный пользователь открывает документ или книгу, имеющую расширения управляемого кода.  
  
2.  Этот документ или книга загружают скомпилированную сборку.  
  
3.  Сборка реагирует на события по мере работы пользователя в документе или книге.  
  
#### <a name="developer-and-end-user-perspective-compared"></a>Сравнение с точек зрения разработчика и конечного пользователя  
 Поскольку разработчик работает в основном в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], а конечный пользователь работает в Word или Excel, существует два пути понимания настроек на уровне документа.  
  
|С точки зрения разработчика|С точки зрения пользователя|  
|-----------------------------|----------------------------|  
|Используя [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], разработчик пишет код, доступный для Word и Excel.<br /><br /> Хотя может показаться, что разработчик создает исполняемый файл, который выполняется в Word или Excel, в действительности процесс работает в обратном направлении. Документ связан со сборкой и содержит указатель на эту сборку. При открытии документа Word или Excel находит сборку и выполняет код в ответ на все обработанные события.|Тех, кто использует решение, просто открывают документ или книгу (или создают новый документ из шаблона) точно так же, как любой другой файл Microsoft Office.<br /><br /> Сборка предоставляет настройки в документе или книге, такие как автоматическое заполнение текущими данными или отображение диалогового окна для запроса информации.|  
  
### <a name="supported-document-formats-for-document-level-customizations"></a>Поддерживаемые форматы документов для настроек уровня документа  
 При создании проекта настройки можно выбрать формат документа, который вы хотите использовать в проекте. Дополнительные сведения см. в разделе [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
 В следующей таблице перечислены форматы документов, которые можно использовать в настройках уровня документа для Excel и Word.  
  
|Excel|Слово|  
|-----------|----------|  
|Книга Excel (XLSX)<br /><br /> Книга Excel с поддержкой макросов (XLSM)<br /><br /> Двоичная книга Excel (XLSB)<br /><br /> Книга Excel 97-2003 (XLS)<br /><br /> Шаблон Excel (XLTX)<br /><br /> Шаблон Excel с поддержкой макросов (XLTM)<br /><br /> Шаблон Excel 97-2003 (XLT)|Документ Word (DOCX)<br /><br /> Документ Word с поддержкой макросов (DOCM)<br /><br /> Документ Word 97-2003 (DOC)<br /><br /> Шаблон Word (DOTX)<br /><br /> Шаблон Word с поддержкой макросов (DOTM)<br /><br /> Шаблон Word 97-2003 (DOT)|  
  
 Следует разрабатывать расширения управляемого кода только для документов в поддерживаемых форматов. В противном случае некоторые события могут не возникать при открытии документа в приложении. Например, событие <xref:Microsoft.Office.Tools.Excel.Workbook.Open> не возникает при использовании расширений управляемого кода с книгами, сохраненными в формате электронной таблицы Excel XML или в формате веб-страницы (HTM, HTML).  
  
### <a name="support-for-word-documents-that-have-xml-file-name-extensions"></a>Поддержка документов Word, которые имеют расширения имени файла XML  
 Шаблоны проектов уровня документа не позволяют создавать проекты на основе следующих форматов файлов.  
  
-   XML-документ Word (XML).  
  
-   XML-документ Word 2003 (XML).  
  
 Если требуется, чтобы пользователи применяли настройки в этих форматах файлов, выполните сборку и развертывание настройки, которая использует один из поддерживаемых форматов файлов, указанных в таблице выше. После установки такой настройки пользователи смогут сохранить документ в XML-документа Word (* xml) формате или XML-документа Word 2003 (\*xml) формат и настройки будут продолжать работать должным образом.  
  
##  <a name="Components"></a> Components of Customizations  
 Основные компоненты настройки — это документ и сборка. Помимо этих компонентов существует несколько других частей, играющих важную роль в том, как приложения Microsoft Office обнаруживают и загружают настройки.  
  
### <a name="deployment-manifest-and-application-manifest"></a>Манифест развертывания и манифест приложения  
 Настройки используют манифесты развертывания и манифесты приложений для обнаружения и загрузки самой последней версии сборки настройки. Манифест развертывания указывает на текущий манифест приложения. Манифест приложения указывает на сборку настройки и задает класс (или классы) точки входа для выполнения в сборке. Для получения дополнительной информации см. [Application and Deployment Manifests in Office Solutions](../vsto/application-and-deployment-manifests-in-office-solutions.md).  
  
### <a name="visual-studio-tools-for-office-runtime"></a>Набор средств Visual Studio для Office (среда выполнения)  
 Для запуска настроек уровня документа, созданных с помощью средств разработчика Office в Visual Studio, на компьютерах конечных пользователей должна быть установлена среда выполнения [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] . Среда выполнения [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] содержит неуправляемые компоненты, которые загружают сборку настройки, а также набор управляемых сборок. Эти управляемые сборки предоставляют объектную модель, которую код надстройки использует для автоматизации и расширения ведущего приложения.  
  
 Дополнительные сведения см. в разделе [Visual Studio Tools for Office Runtime Overview](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
##  <a name="HowCustomizationsWork"></a> How Customizations Work with Microsoft Office Applications  
 Когда пользователь открывает документ, который является частью настройки Microsoft Office, приложение использует манифест развертывания, связанный с этим документом, для обнаружения и загрузки последней версии сборки настройки. Расположение манифеста развертывания хранится в пользовательском свойстве документа с именем _AssemblyLocation. Строка, идентифицирующая данное расположение, вставляется в свойство при сборке решения.  
  
 Манифест развертывания указывает на манифест приложения, который в свою очередь указывает на последнюю сборку. Для получения дополнительной информации см. [Application and Deployment Manifests in Office Solutions](../vsto/application-and-deployment-manifests-in-office-solutions.md).  
  
 На следующем рисунке показана основная архитектура настройки уровня документа.  
  
 ![Архитектура настройки office 2007](../vsto/media/office07-custom.png "архитектура настройки Office 2007")  
  
> [!NOTE]  
>  В решениях Office, ориентированных на [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], решения вызывают объектную модель ведущего приложения с помощью сведений о типах основной сборки взаимодействия, внедренных в сборку решения, а не вызывают непосредственно саму эту сборку. Для получения дополнительной информации см. [Designing and Creating Office Solutions](../vsto/designing-and-creating-office-solutions.md).  
  
### <a name="loading-process"></a>Процесс загрузки  
 Следующие действия выполняются, когда пользователь открывает документ, который является частью решения Microsoft Office.  
  
1.  Приложение Microsoft Office проверяет настраиваемые свойства документа, чтобы увидеть, есть ли в этом документе расширения управляемого кода. Для получения дополнительной информации см. [Custom Document Properties Overview](../vsto/custom-document-properties-overview.md).  
  
2.  Если расширения управляемого кода присутствуют, приложение загружает файл VSTOEE.dll, который загружает файл VSTOLoader.dll. Эти файлы представляют собой неуправляемые библиотеки DLL и являются компонентами загрузчика для среды выполнения набора средств Visual Studio 2010 для Office. Для получения дополнительной информации см. [Visual Studio Tools for Office Runtime Overview](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
3.  VSTOLoader.dll загружает [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] и запускает управляемую часть среды [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  
  
4.  Если документ открывается из расположения, отличного от локального компьютера, среда выполнения [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] проверяет, указано ли расположение этого документа в списке **надежных расположений** в **параметрах центра управления безопасностью** для данного конкретного приложения Office. Если расположение документа не указано в списке надежных расположений, настройка не является доверенной, и на этом процесс загрузки останавливается.  
  
5.  Среда выполнения [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] устанавливает решение, если оно еще не установлено, загружает последние манифесты приложения и развертывания и выполняет серию проверок безопасности. Для получения дополнительной информации см. [Securing Office Solutions](../vsto/securing-office-solutions.md).  
  
6.  Если настройка имеет необходимый уровень доверия для выполнения, среда выполнения [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] использует манифест развертывания и манифест приложения для проверки наличия обновлений сборки. Если доступна новая версия сборки, среда выполнения загружает эту версию в кэш [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] на клиентском компьютере. Дополнительные сведения см. в разделе [развертывание решения Office](../vsto/deploying-an-office-solution.md).  
  
7.  Среда выполнения [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] создает новый домен приложения для загрузки сборки настройки.  
  
8.  Среда выполнения [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] загружает сборку настройки в домен приложения.  
  
9. Среда выполнения [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] вызывает обработчик событий **Startup** в сборке настройки. Дополнительные сведения см. в разделе [Events in Office Projects](../vsto/events-in-office-projects.md).  
  
## <a name="see-also"></a>См. также  
 [Архитектура решений Office в Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)   
 [Архитектура надстроек VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Visual Studio Tools for Office Runtime Overview](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Обеспечение безопасности решений Office](../vsto/securing-office-solutions.md)   
 [Проектирование и создание решений Office](../vsto/designing-and-creating-office-solutions.md)   
 [Общие сведения о свойствах пользовательского документа](../vsto/custom-document-properties-overview.md)   
 [Кэшированные данные в настройках на уровне документа](../vsto/cached-data-in-document-level-customizations.md)  
  
  