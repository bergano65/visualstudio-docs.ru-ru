---
title: "Отладка решений SharePoint | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.Project.WebConfigModificationDialog
- VS.SharePointTools.Project.DebuggingNotEnabled
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, debugging
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 85317332cd6b142bb8e0e916e3d7ac80e4aa836c
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="debugging-sharepoint-solutions"></a>Отладка решений SharePoint
  Можно отлаживать решения SharePoint с помощью [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] отладчика. При запуске отладки, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] развертывает файлы проекта на сервере SharePoint, а затем открывает экземпляр сайта SharePoint в веб-браузере. Ниже описаны способы отладки приложений SharePoint в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
-   [Включение отладки](#EnableDebug)  
  
-   [Отладка F5 и процесс развертывания](#Deployment)  
  
-   [Функции проекта SharePoint](#Features)  
  
-   [Отладка рабочих процессов](#Workflow)  
  
-   [Отладка приемников событий компонентов](#FeatureEvents)  
  
-   [Включение расширенные сведения об отладке](#EnhancedDebug)  
  
##  <a name="EnableDebug"></a>Включение отладки  
 При отладке сначала решения SharePoint в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], диалоговое окно предупреждения, что в файле web.config не задан для включения отладки. (Файл web.config создается при установке сервера SharePoint. Дополнительные сведения см. в разделе [работа с файлами Web.config](http://go.microsoft.com/fwlink/?LinkID=149266).) Диалоговое окно позволяет либо запустить проект без отладки, либо изменить файл web.config для включения отладки. Если выбрать первый вариант, проект выполняется обычным образом. Если выбрать второй вариант, параметры в файле web.config изменяются следующим образом:  
  
-   Включить в стеке вызовов (`CallStack="true"`)  
  
-   Запретить пользовательские ошибки в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] (`<customErrors mode="Off" />`)  
  
-   Включить отладку компиляции (`<compilation debug="true">`)  
  
 Результирующий файл web.config следующим образом:  
  
```  
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
  
-   Включите настраиваемые ошибки в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] (`<customErrors mode="On" />`)  
  
-   Отключите отладку компиляции (`<compilation debug="false">`)  
  
##  <a name="Deployment"></a>Отладка F5 и процесс развертывания  
 При запуске проекта SharePoint в режиме отладки, в процессе развертывания SharePoint выполняет следующие задачи:  
  
1.  Выполняются пользовательские команды, выполняемые перед развертыванием.  
  
2.  Создает веб-файл пакета (.wsp) решения с помощью [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] команд. WSP-файл содержит все необходимые файлы и компоненты. Дополнительные сведения см. в разделе [Обзор решений](http://go.microsoft.com/fwlink/?LinkID=128154).  
  
3.  Если решение SharePoint представляет собой решение фермы, запускается повторно [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] пул приложений для указанного сайта [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)]. Этот шаг высвобождаются файлы, заблокированные [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] рабочего процесса.  
  
4.  Если уже существует предыдущая версия пакета, извлечение предыдущей версии компонентов и файлы в WSP-файл. Этот шаг отключает возможности, удаляет пакет решения, а затем удаляет пакета решения на сервере SharePoint.  
  
5.  Устанавливает текущую версию компонентов и файлы в WSP-файл. Этот шаг добавляет и устанавливает решение на сервере SharePoint.  
  
6.  Для рабочих процессов устанавливает сборки рабочего процесса. Его расположение можно изменить с помощью *расположения сборки* свойство.  
  
7.  Активирует компонент проекта SharePoint, если область сайта или веб. Не включены возможности в области фермы и веб-приложения.  
  
8.  Для рабочих процессов, рабочий процесс будет связан с библиотекой SharePoint, списка или сайта, выбранного в **мастер настройки SharePoint**.  
  
    > [!NOTE]  
    >  Это сопоставление происходит только в том случае, если вы выбрали **автоматически связать рабочий процесс** в мастере.  
  
9. Выполняются пользовательские команды, выполняемые после развертывания.  
  
10. Присоединяет отладчик [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] к процессу [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] (w3wp.exe). Если тип проекта позволяет изменять *изолированное решение* свойство и его значение равно **true**, отладчик подключается к другому процессу (SPUCWorkerProcess.exe). Дополнительные сведения см. в разделе [замечания об изолированных решениях](../sharepoint/sandboxed-solution-considerations.md).  
  
11. Запускает отладчик JavaScript, если решение SharePoint представляет собой решение фермы.  
  
12. Отображает соответствующие библиотека, список или страница сайта в веб-браузере.  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Отображает сообщение о состоянии в окне «Вывод», после завершения каждой задачи. Если не удается выполнить задачу, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] отображает сообщение об ошибке в окне списка ошибок.  
  
##  <a name="Features"></a>Функции проекта SharePoint  
 Компонент является переносимый модульный элемент функциональных возможностей, который упрощает изменение узлов с помощью определения сайтов. Это также пакета [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] (WSS) элементов, которые можно активировать для определенной области, и которые помогают пользователю в выполнении конкретной задачи. Как компоненты развертываются шаблоны.  
  
 При запуске проекта в режиме отладки процесс развертывания создает папку в *функция* каталог на %COMMONPROGRAMFILES%\Microsoft Shared\web server extensions\14\TEMPLATE\FEATURES. Имена компонентов имеют формат *имя проекта*_Feature*x*, например TestProject_Feature1.  
  
 Папка решения в каталоге функций содержит *Определение компонента* файла и *определение рабочего процесса* файла. Файл определения компонента (Feature.xml) описывает файлы в проекте Feature.The файл определения проекта (Elements.xml) описывается шаблон проекта. Файл Elements.XML можно найти в **обозревателе решений**, но файл Feature.xml создается при создании пакета решения. Дополнительные сведения об этих файлах см. в разделе [проект SharePoint и шаблоны элементов проекта](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
##  <a name="Workflow"></a>Отладка рабочих процессов  
 При отладке проекта рабочего процесса [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] добавляет шаблон рабочего процесса (в зависимости от его типа) в библиотеку или список. Затем в шаблон рабочего процесса можно запустить вручную или путем добавления или обновления элемента. Затем можно использовать [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] для отладки рабочего процесса.  
  
> [!NOTE]  
>  При добавлении ссылки на другие сборки, убедитесь, что данные сборки установлены в глобальном кэше сборок ([!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)]). В противном случае не удастся решения рабочего процесса. Сведения об установке сборок см. в разделе [вручную запустите рабочий процесс для документа или элемента](http://go.microsoft.com/fwlink/?LinkID=79938).  
  
 Тем не менее процесс развертывания не запускается рабочий процесс. Рабочий процесс необходимо запускать с веб-сайта SharePoint. Можно также запустить рабочий процесс, с помощью клиентского приложения, такие как Microsoft Office Word 2010, либо используя отдельный код на стороне сервера. Используйте один из подходов, указанных в **мастер настройки SharePoint**.  
  
 Например, если вы указали, что рабочий процесс можно запустить вручную, рабочий процесс запускается непосредственно из элемента в библиотеке или списке. Дополнительные сведения о том, как запустить рабочий процесс вручную см. в разделе [вручную запустить рабочий процесс на элемент документа](http://go.microsoft.com/fwlink/?LinkID=79938).  
  
##  <a name="FeatureEvents"></a>Отладка приемников событий компонентов  
 По умолчанию при запуске [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] приложения SharePoint его компоненты автоматически активируются для вас на сервере SharePoint. Тем не менее, это вызывает проблемы при отладке приемников событий компонентов, поскольку при активации компонент по [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], он выполняется в другом процессе, что отладчик. Это означает, что функции отладки, например точки останова, не будут работать правильно.  
  
 Чтобы отключить автоматическую активацию компонента в SharePoint и выполнять отладку для приемников событий компонентов, установите для параметра проекта **активная конфигурация развертывания** свойства **без активации** перед отладкой. Затем, после начала отладки вашего приложения SharePoint в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], вручную активируйте компонент в SharePoint. Чтобы активировать компонент, откройте **действия сайта** в SharePoint, в меню выберите **параметры сайта**, выберите **Управление компонентами сайта** связь, а затем выберите **Активировать** рядом с компонентом для продолжения отладки в обычном режиме.  
  
##  <a name="EnhancedDebug"></a>Включение расширенные сведения об отладке  
 Из-за сложных взаимодействий между [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] процесса (devenv.exe) [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint хост-процесса (vssphost4.exe), SharePoint и уровнем WCF, можно диагностировать ошибки, возникающие во время построения, развертывания и так далее запрос. Чтобы облегчить эту задачу, можно включить расширенные сведения об отладке. Чтобы сделать это, перейдите к следующему разделу реестра, в реестре Windows:  
  
 [HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\11.0\SharePointTools]  
  
 Если «EnableDiagnostics» **REG_DWORD** значение еще не существует, создайте его вручную. Задайте значение «EnableDiagnostics» в «1».  
  
 Установка этого значения ключа в 1 стека причины трассировки сведения отображаются в **вывода** окна при каждой ошибке, возникающей при запуске [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Чтобы отключить отображение подробной отладочной информации, снова задайте для EnableDiagnostics значение 0 или удалите значение.  
  
 Дополнительные сведения о других разделах реестра SharePoint см. в разделе [отладка расширений для средств SharePoint в Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>См. также  
 [Устранение неполадок решений SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md)  
  
  