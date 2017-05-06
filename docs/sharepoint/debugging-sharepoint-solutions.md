---
title: "Отладка решений SharePoint"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.Project.WebConfigModificationDialog"
  - "VS.SharePointTools.Project.DebuggingNotEnabled"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "разработка приложений SharePoint в Visual Studio, отладка"
ms.assetid: 5120f21e-4c27-4906-b982-85e9cd5170e6
caps.latest.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 28
---
# Отладка решений SharePoint
  Отладка решений SharePoint выполняется с помощью отладчика [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  При запуске отладки [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] развертывает файлы проекта на сервере SharePoint, затем открывает экземпляр сайта SharePoint в веб\-браузере.  В следующих разделах рассматриваются принципы отладки приложений SharePoint в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
-   [Включение отладки](#EnableDebug)  
  
-   [Отладка с помощью клавиши F5 и процесс развертывания](#Deployment)  
  
-   [Компоненты проектов SharePoint](#Features)  
  
-   [Отладка рабочих процессов](#Workflow)  
  
-   [Отладка приемников событий компонентов](#FeatureEvents)  
  
-   [Включение вывода подробных сведений об отладке](#EnhancedDebug)  
  
##  <a name="EnableDebug"></a> Включение отладки  
 Когда отладка решения SharePoint в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] выполняется впервые, выводится диалоговое окно с уведомлением о том, что в файле web.config не задан параметр, разрешающий отладку. \(Файл web.config создается при установке сервера SharePoint.  Дополнительные сведения см. в [Работа с файлами web.config](http://go.microsoft.com/fwlink/?LinkID=149266).\) В диалоговом окне предлагается либо запустить проект без отладки, либо изменить файл web.config, разрешив отладку.  Если выбрать первый вариант, проект выполняется обычным образом.  Если выбрать второй, параметры в файле web.config изменяются следующим образом:  
  
-   включается стек вызова \(`CallStack="true"`\);  
  
-   отключаются настраиваемые ошибки в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] \(`<customErrors mode="Off" />`\);  
  
-   включается отладка компиляции \(`<compilation debug="true">`\).  
  
 Ниже приведен результирующий файл web.config.  
  
```  
  
<configuration>  
    ...  
    <SharePoint>  
        <SafeMode MaxControls="200"  
            CallStack="true"  
            DirectFileDependencies="10"  
            TotalFileDependencies="50"  
            AllowPageLevelTrace="false">  
            ...  
        </SafeMode>  
    ...  
    </SharePoint>  
    <system.web>  
        ...  
        <customErrors mode="Off" />  
        ...  
        <compilation debug="true">  
        ...  
        </compilation>  
        ...  
    </system.web>  
    ...  
</configuration>  
```  
  
 Чтобы отменить изменения и отключить отладку, измените [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]\-код в файле web.config следующим образом:  
  
-   отключите стек вызова \(`CallStack="false"`\);  
  
-   включите настраиваемые ошибки в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] \(`<customErrors mode="On" />`\);  
  
-   отключите отладку компиляции \(`<compilation debug="false">`\).  
  
##  <a name="Deployment"></a> Отладка с помощью клавиши F5 и процесс развертывания  
 Если проект SharePoint выполняется в режиме отладки, в процессе развертывания SharePoint выполняются следующие задачи.  
  
1.  Выполняются пользовательские команды, выполняемые перед развертыванием.  
  
2.  Создается веб\-пакет решения \(WSP\-файл\) с помощью команд [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)].  WSP\-файл включает в себя все необходимые файлы и компоненты.  Дополнительные сведения см. в [Solutions Overview](http://go.microsoft.com/fwlink/?LinkID=128154).  
  
3.  Если решение SharePoint представляет собой решение фермы, пул приложений [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] повторно используется для указанного [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)]а сайта.  На этом этапе высвобождаются файлы, заблокированные рабочим процессом [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)].  
  
4.  Если существует предыдущая версия пакета, в WSP\-файл извлекаются предыдущие версии компонентов и файлов.  На этом этапе компоненты отключаются, пакет решения удаляется, затем он удаляется с сервера SharePoint.  
  
5.  Устанавливается текущая версия компонентов и файлов из WSP\-файла.  На этом этапе решение добавляется и устанавливается на сервер SharePoint.  
  
6.  Устанавливаются сборки рабочих процессов.  Расположение сборки можно изменить с помощью свойства *Assembly Location*.  
  
7.  Активируются компоненты проекта в SharePoint, для которых задана область Site или Web.  Компоненты с областями Farm и WebApplication не активируются.  
  
8.  Рабочие процессы связываются с библиотекой списка SharePoint, со списком или сайтом, указанным в **Мастере настройки SharePoint**.  
  
    > [!NOTE]  
    >  Это связывание происходит, только если в мастере выбран параметр **Автоматически связывать рабочий процесс**.  
  
9. Выполняются пользовательские команды, выполняемые после развертывания.  
  
10. Присоединяет отладчик [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] к процессу [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] с именем w3wp.exe.  Если тип проекта позволяет изменять свойство *Sandboxed Solution* и ему присвоено значение **true**, отладчик подключается к другому процессу \(SPUCWorkerProcess.exe\).  Для получения дополнительной информации см. [Замечания об обезвреженных решениях](../sharepoint/sandboxed-solution-considerations.md).  
  
11. Запускается отладчик JavaScript, если решение SharePoint является решением фермы.  
  
12. В веб\-браузере отображается соответствующая библиотека, список или страница сайта.  
  
 После каждого выполненного задания в окне "Вывод" [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] выводится сообщение о состоянии.  Если выполнить задачу не удается, в окне "Список ошибок" [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] выводится сообщение об ошибке.  
  
##  <a name="Features"></a> Компоненты проектов SharePoint  
 Компонент представляет собой переносимый модульный функциональный элемент, упрощающий изменение сайтов за счет использования определений сайтов.  Он также является пакетом для элементов служб [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] \(WSS\), которые можно активировать для определенной области, и которые помогают пользователю в выполнении определенных задач.  Шаблоны развертываются в качестве компонентов.  
  
 При запуске проекта в режиме отладки процесс развертывания создает новую папку в каталоге *компонентов* %COMMONPROGRAMFILES%\\Microsoft Shared\\web server extensions\\14\\TEMPLATE\\FEATURES.  Имена компонентов имеют формат *project name*\_Feature*x*, например TestProject\_Feature1.  
  
 Папка решения в каталоге функций содержит файл *определения функций* и файл *определения рабочих процессов*.  В файле определения компонента проекта \(Feature.xml\) содержится описание файлов этого компонента.В файле определения проекта \(Elements.xml\) описывается шаблон проекта.  Файл Elements.xml можно открыть через **Обозреватель решений**, тогда как файл Feature.xml создается при создании пакета решения.  Дополнительные сведения об этих файлах см. в разделе [Шаблоны проектов и элементов проектов SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
##  <a name="Workflow"></a> Отладка рабочих процессов  
 При отладке проекта рабочего процесса [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] добавляет шаблон этого рабочего процесса в библиотеку или список \(в зависимости от его типа\).  После этого можно запустить шаблон рабочего процесса \(вручную или путем добавления или обновления элемента\).  Затем можно выполнить отладку рабочего процесса в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
> [!NOTE]  
>  При добавлении ссылок на другие сборки удостоверьтесь, что данные сборки установлены в глобальном кэше сборок \([!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)]\).  В противном случае решение рабочего процесса запустить не удастся.  Дополнительные сведения об установке сборок см. в [Manually start a workflow on a document or item](http://go.microsoft.com/fwlink/?LinkID=79938).  
  
 Впрочем, развертывание не запускает рабочий процесс.  Следует запустить его из узла SharePoint.  Рабочий процесс также можно запустить с помощью клиентского приложения — например, Microsoft Office Word 2010, или же с помощью отдельного кода на стороне сервера.  Используйте один из подходов, указанных в **Мастере настройки SharePoint**.  
  
 Например, если в мастере было указано, что рабочий процесс можно запустить вручную, следует запустить рабочий процесс непосредственно из элемента в библиотеке или списке.  Дополнительные сведения о запуске рабочего процесса вручную см. в [Manually start a workflow on a document item](http://go.microsoft.com/fwlink/?LinkID=79938).  
  
##  <a name="FeatureEvents"></a> Отладка приемников событий компонентов  
 По умолчанию при запуске приложения [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint его компоненты автоматически активируются на сервере SharePoint.  Впрочем, это вызывает проблемы при отладке приемников событий этого компонента, поскольку когда он активируется системой [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], он выполняется не в том же процессе, что отладчик.  Поэтому функции отладки, такие как точка останова, не действуют надлежащим образом.  
  
 Чтобы отключить автоматическую активацию компонента в SharePoint, прежде чем выполнять отладку содержащихся в нем приемников событий задайте свойству проекта **Активная конфигурация развертывания** значение **Без активации**.  Затем, после начала отладки вашего приложения SharePoint в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], вручную активируйте компонент в SharePoint.  Для активации компонента откройте меню SharePoint **Действия сайта**, выберите пункт **Параметры сайта**, выберите ссылку **Управление компонентами сайта**, а затем нажмите кнопку **Активировать** рядом с нужным компонентом, для продолжения отладки.  
  
##  <a name="EnhancedDebug"></a> Включение вывода подробных сведений об отладке  
 В связи с тем, что взаимодействие между процессом [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] \(devenv.exe\), ведущим процессом SharePoint [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] \(vssphost4.exe\), SharePoint и уровнем WCF бывает крайне сложным, иногда очень непросто диагностировать ошибки, возникающие при построении, развертывании и выполнении других операций.  Чтобы упростить эту задачу, можно включить подробную информацию отладки.  Для этого откройте следующий раздел реестра Windows:  
  
 \[HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\11.0\\SharePointTools\]  
  
 Если значение **REG\_DWORD** "EnableDiagnostics" уже не существует, необходимо создать его вручную.  Установите значение «EnableDiagnostics» в «1».  
  
 Если задать это значение ключа равным 1, при каждой ошибке, возникающей во время работы в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], сведения трассировки стека отображаются в окне **Вывод**.  Чтобы отключить отображение подробной отладочной информации, снова задайте для EnableDiagnostics значение 0 или удалите значение.  
  
 Дополнительные сведения о других разделах реестра SharePoint см. в разделе [Debugging Extensions for the SharePoint Tools in Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## См. также  
 [Устранение неполадок решений SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md)  
  
  