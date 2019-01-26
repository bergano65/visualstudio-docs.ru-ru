---
title: Отладка решений SharePoint | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.WebConfigModificationDialog
- VS.SharePointTools.Project.DebuggingNotEnabled
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, debugging
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9c602654b5d9a8aac16f671db4e68063ad15a2d5
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2019
ms.locfileid: "54874462"
---
# <a name="debug-sharepoint-solutions"></a>Отладка решений SharePoint
  Можно отлаживать решения SharePoint с помощью [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] отладчика. При запуске отладки, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] развертывает файлы проекта на сервере SharePoint, а затем открывает экземпляр сайта SharePoint в веб-браузере. Ниже описаны способы отладки приложений SharePoint в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
-   [Включение отладки](#EnableDebug)  
  
-   [Отладку по клавише F5 и процесс развертывания](#Deployment)  
  
-   [Функции проекта SharePoint](#Features)  
  
-   [Отладка рабочих процессов](#Workflow)  
  
-   [Отладка приемников событий компонентов](#FeatureEvents)  
  
-   [Включение расширенные сведения об отладке](#EnhancedDebug)  
  
## <a name="enable-debugging"></a>Включить отладку
 При первом отладке решения SharePoint в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], диалоговое окно предупреждения, что файл web.config настроен для включения отладки. (Файл web.config создается при установке сервера SharePoint. Дополнительные сведения см. в разделе [работа с файлами Web.config](http://go.microsoft.com/fwlink/?LinkID=149266).) Диалоговое окно предоставляет возможность либо запустить проект без отладки или изменения файла web.config для включения отладки. Если выбрать первый вариант, проект выполняется обычным образом. Если выбрать второй вариант, параметры в файле web.config изменяются следующим образом:  
  
- Включить в стеке вызовов (`CallStack="true"`)  
  
- Запретить пользовательские ошибки в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] (`<customErrors mode="Off" />`)  
  
- Включить отладку компиляции (`<compilation debug="true">`)  
  
  Полученный файл web.config следующим образом:  
  
```xml  
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
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
  
 Чтобы отменить изменения и отключить отладку, измените следующие [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] в файле web.config:  
  
-   Отключить стек вызовов (`CallStack="false"`)  
  
-   Включить настраиваемые ошибки в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] (`<customErrors mode="On" />`)  
  
-   Отключить отладку компиляции (`<compilation debug="false">`)  
  
## <a name="f5-debug-and-deployment-process"></a>Процесс отладки и развертывания F5
 При запуске проекта SharePoint в режиме отладки, процесс развертывания SharePoint выполняет следующие задачи:  
  
1. Выполняет настраиваемые команды перед развертыванием.  
  
2. Создает файл пакета (.wsp) Web решения с помощью [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] команды. WSP-файл содержит все необходимые файлы и компоненты. Дополнительные сведения см. в разделе [Обзор решений](http://go.microsoft.com/fwlink/?LinkID=128154).  
  
3. Если решение SharePoint представляет собой решение фермы, перезапускается [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] пул приложений для заданного узла [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)]. Этот шаг освобождает файлы, заблокированные [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] рабочего процесса.  
  
4. Если уже существует предыдущая версия пакета, отзывается предыдущей версии компонентов и файлов в WSP-файл. Это отключит возможности, удаляет пакет решения, а затем удаляет пакет решения на сервере SharePoint.  
  
5. Устанавливает текущей версии компонентов и файлов в WSP-файл. Этот шаг добавляет и устанавливает решение на сервере SharePoint.  
  
6. Для рабочих процессов устанавливает сборку рабочего процесса. Его расположение можно изменить с помощью *расположение сборки* свойство.  
  
7. Активирует компонент проекта в SharePoint, если область сайта или веб. Возможности в области фермы и веб-приложения не активированы.  
  
8. Для рабочих процессов, связываются с библиотеки SharePoint, списка или сайта, выбранного в **мастер настройки SharePoint**.  
  
   > [!NOTE]  
   >  Это связывание происходит только в том случае, если вы выбрали **автоматически связать рабочий процесс** в мастере.  
  
9. Выполняет настраиваемые команды после развертывания.  
  
10. Присоединяет [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] отладчик [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] процесса (*w3wp.exe*). Если тип проекта позволяет изменять *изолированное решение* свойство и его значение будет присвоено **true**, отладчик подключается к другому процессу (*SPUCWorkerProcess.exe*). Дополнительные сведения см. в разделе [замечания об изолированных решениях](../sharepoint/sandboxed-solution-considerations.md).  
  
11. Запускает отладчик JavaScript, если решение SharePoint представляет собой решение фермы.  
  
12. Отображает соответствующую библиотеку, список или страница сайта в веб-браузере.  
  
    [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] выводит сообщение о состоянии в окне вывода, после завершения каждой задачи. Если задачу выполнить не удастся, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] отображает сообщение об ошибке в окне списка ошибок.  
  
## <a name="sharepoint-project-features"></a>Функции проекта SharePoint
 Функция — это переносимые и модульной единица функциональности, который упрощает изменение узлов с помощью определений сайтов. Это также пакет [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] элементы (WSS), которые можно активировать для определенной области, и которые помогают пользователям при выполнении определенных задач. Шаблоны были развернуты как функции.  
  
 При запуске проекта в режиме отладки, процесс развертывания создает папку в *функция* находящемся *%COMMONPROGRAMFILES%\Microsoft Shared\web server extensions\14\TEMPLATE\FEATURES*. Имена компонентов имеют формат *имя_проекта*_Feature*x*, например TestProject_Feature1.  
  
 Папка решения в каталоге функций содержит *Определение компонента* файл и *определения рабочего процесса* файл. Файлом определения компонента (Feature.xml) описывает файлы в файл определения проекта Feature.The проекта (*Elements.xml*) описывается шаблон проекта. *Elements.XML* можно найти в **обозревателе решений**, но файл Feature.xml создается при создании пакета решения. Дополнительные сведения об этих файлах см. в разделе [SharePoint проект и проект шаблоны элементов](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
## <a name="debug-workflows"></a>Отладка рабочих процессов
 При отладке проекта рабочего процесса, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] добавляет шаблон рабочего процесса (в зависимости от его типа) в библиотеку или список. После этого вы сможете в шаблон рабочего процесса вручную или путем добавления или обновления элемента. Затем можно использовать [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] отладку рабочего процесса.  
  
> [!NOTE]
>  При добавлении ссылки на другие сборки, убедитесь, что эти сборки установлены в глобальный кэш сборок ( [!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)]). В противном случае не удастся решения рабочего процесса. Сведения об установке сборок см. в разделе [вручную запустить рабочий процесс на документ или элемент](https://support.office.com/article/Manually-start-a-workflow-on-a-document-or-item-5C106E0E-6FF2-4A75-AF99-F01653BC7963).  
  
 Тем не менее процесс развертывания не запускается рабочий процесс. Необходимо запустить рабочий процесс с сайта SharePoint. Можно также запустить рабочий процесс, с помощью клиентского приложения, такие как Microsoft Office Word 2010 или с помощью отдельного кода на стороне сервера. Используйте один из подходов, указанных в **мастер настройки SharePoint**.  
  
 Например если вы указали, что рабочий процесс можно запустить вручную, следует запустите рабочий процесс непосредственно из элемента в библиотеке или списке. Дополнительные сведения о том, как запустить рабочий процесс вручную см. в разделе [вручную запустить рабочий процесс на элемент документа](https://support.office.com/article/Manually-start-a-workflow-on-a-document-or-item-5C106E0E-6FF2-4A75-AF99-F01653BC7963).  
  
## <a name="debug-feature-event-receivers"></a>Отладка приемников событий компонентов
 По умолчанию при запуске [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] приложения SharePoint, его функции автоматически активируются для вас на сервере SharePoint. Тем не менее, это вызывает проблемы при отладке приемников событий компонентов, поскольку если активировать функцию с [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], оно выполняется в другом процессе, отладчик. Это означает, что некоторые функции отладки, такие как точки останова, не будут работать правильно.  
  
 Чтобы отключить автоматическую активацию компонента в SharePoint и выполнять отладку из приемников событий компонентов, установите для параметра проекта **активная конфигурация развертывания** свойства **без активации** перед отладкой. Затем, после начала отладки вашего приложения SharePoint в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], вручную активируйте компонент в SharePoint. Чтобы активировать функцию, откройте **действия сайта** в SharePoint, в меню выберите **параметры сайта**, выберите **управление функциями сайта** связать, а затем щелкните **Активировать** кнопку рядом с компонентом, чтобы продолжить отладку в обычном режиме.  
  
## <a name="enable-enhanced-debug-information"></a>Включение расширенного отладочной информации
 Из-за сложных взаимодействий между [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] процесса (devenv.exe), [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] хост-процессе SharePoint (*vssphost4.exe*), SharePoint и на уровне WCF, диагностировать ошибки, возникающие во время построение, развертывание и так далее может быть сложной задачей. Чтобы облегчить эту задачу, вы можете включить расширенные сведения об отладке. Чтобы сделать это, перейдите к следующему разделу реестра в реестре Windows:  
  
 **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\11.0\SharePointTools**  
  
 Если «EnableDiagnostics» **REG_DWORD** значение еще не существует, создайте его вручную. Задайте значение «EnableDiagnostics» в «1».  
  
 Значение ключа 1 стека причины трассировки сведения отображаются в **вывода** окно при каждой ошибке, возникающей при запуске [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Чтобы отключить отображение подробной отладочной информации, снова задайте для EnableDiagnostics значение 0 или удалите значение.  
  
 Дополнительные сведения о других разделах реестра SharePoint, см. в разделе [отладка расширений для инструментов SharePoint в Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>См. также
 [Устранение неполадок решений SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md)  
