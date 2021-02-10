---
title: Отладка решений SharePoint | Документация Майкрософт
description: Отладка решений SharePoint с помощью отладчика Visual Studio. Изучите процесс отладки и развертывания F5, рабочие процессы отладки и приемники событий функций отладки.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f1a6abfbafcbafb9daa52fdc6af85156700efef7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948951"
---
# <a name="debug-sharepoint-solutions"></a>Отладка решений SharePoint
  Вы можете отлаживать решения SharePoint с помощью [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] отладчика. При запуске отладки [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] развертывает файлы проекта на сервере SharePoint, а затем открывает экземпляр сайта SharePoint в веб-браузере. В следующих разделах объясняется, как выполнять отладку приложений SharePoint в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

- [Тестирование навыка Кортаны](#enable-debugging)

- [Отладка и процесс развертывания F5](#f5-debug-and-deployment-process)

- [Функции проекта SharePoint](#sharepoint-project-features)

- [Отладка рабочих процессов](#debug-workflows)

- [Отладить приемники событий компонентов](#debug-feature-event-receivers)

- [Включение отладочной информации еханцед](#enable-enhanced-debugging-information)

## <a name="enable-debugging"></a>Включение отладки
 При первой отладке решения SharePoint в появляется [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] диалоговое окно с предупреждением о том, что web.config файл не настроен для включения отладки. (Файл web.config создается при установке SharePoint Server. Дополнительные сведения см. [в разделе Работа с файлами Web.config](/previous-versions/office/developer/sharepoint-2010/ms460914(v=office.14)).) Диалоговое окно дает возможность либо запустить проект без отладки, либо изменить файл web.config, чтобы включить отладку. Если выбрать первый вариант, проект выполняется обычным образом. Если выбрать второй вариант, параметры в файле web.config изменяются следующим образом:

- Включить стек вызовов ( `CallStack="true"` )

- Отключить пользовательские ошибки в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ( `<customErrors mode="Off" />` )

- Включить отладку компиляции ( `<compilation debug="true">` )

  Полученный web.config файл выглядит следующим образом:

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

 Чтобы отменить изменения и отключить отладку, измените следующие [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] файлы в файле web.config:

- Отключение стека вызовов ( `CallStack="false"` )

- Включить пользовательские ошибки в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ( `<customErrors mode="On" />` )

- Отключить отладку компиляции ( `<compilation debug="false">` )

## <a name="f5-debug-and-deployment-process"></a>Отладка и процесс развертывания F5
 При запуске проекта SharePoint в режиме отладки процесс развертывания SharePoint выполняет следующие задачи:

1. Выполняет настраиваемые команды перед развертыванием.

2. Создает файл пакета веб-решений (. wsp) с помощью [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] команд. Файл WSP включает все необходимые файлы и компоненты. Дополнительные сведения см. в разделе [Общие сведения о решениях](/previous-versions/office/developer/sharepoint-2010/aa543214(v=office.14)).

3. Если решение SharePoint является решением фермы, перезапускает [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] пул приложений для указанного сайта [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] . Этот шаг выпускает файлы, заблокированные [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] рабочим процессом.

4. Если предыдущая версия пакета уже существует, вызовите предыдущую версию компонентов и файлов в WSP-файле. Этот шаг деактивирует компоненты, удаляет пакет решения, а затем удалит пакет решения на сервере SharePoint.

5. Устанавливает текущую версию компонентов и файлов в WSP файл. На этом шаге выполняется добавление и установка решения на сервере SharePoint.

6. Для рабочих процессов устанавливает сборку рабочего процесса. Его расположение можно изменить с помощью свойства *расположение сборки* .

7. Активирует компонент проекта в SharePoint, если областью действия является site или Web. Функции в областях фермы и приложений не активированы.

8. Для рабочих процессов связывает рабочий процесс с библиотекой SharePoint, списком или сайтом, выбранным в **мастере настройки SharePoint**.

   > [!NOTE]
   > Эта ассоциация возникает только в том случае, если в мастере выбрано **Автоматическое связывание рабочего процесса** .

9. Выполняет настраиваемые команды, выполняемые после развертывания.

10. Присоединяет [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] отладчик к [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] процессу (*w3wp.exe*). Если тип проекта позволяет изменить свойство *изолированного решения* и его значение установлено в **true**, отладчик подключается к другому процессу (*SPUCWorkerProcess.exe*). Дополнительные сведения см. в статье [рекомендации по изолированным решениям](../sharepoint/sandboxed-solution-considerations.md).

11. Запускает отладчик JavaScript, если решение SharePoint является решением фермы.

12. Отображает соответствующую библиотеку, список или страницу сайта в веб-браузере.

    [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Отображает сообщение о состоянии в окне вывода после завершения каждой задачи. Если задача не может быть завершена, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] в окне Список ошибок отображается сообщение об ошибке.

## <a name="sharepoint-project-features"></a>Функции проекта SharePoint
 Компонент — это переносимая модульная единица функциональности, упрощающая изменение сайтов с помощью определений сайтов. Он также является пакетом [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] (WSS), который может быть активирован для определенной области и помогает пользователям выполнять определенную цель или задачу. Шаблоны развертываются в виде функций.

 При запуске проекта в режиме отладки процесс развертывания создает папку в каталоге *Features* по адресу *%COMMONPROGRAMFILES%\Microsoft Shared\web Server extensions\14\TEMPLATE\FEATURES*. Имена функций имеют формат *имя проекта* _Feature *x*, например TestProject_Feature1.

 Папка решения в каталоге Feature содержит файл *определения компонента* и файл *определения рабочего процесса* . Файл определения компонента (Feature.xml) описывает файлы в компоненте проекта. файл определения проекта (*Elements.xml*) описывает шаблон проекта. *Elements.xml* можно найти в **обозреватель решений**, но Feature.xml создается при создании пакета решения. Дополнительные сведения об этих файлах см. в разделе [проект SharePoint и шаблоны элементов проектов](../sharepoint/sharepoint-project-and-project-item-templates.md).

## <a name="debug-workflows"></a>Отладка рабочих процессов
 При отладке проектов рабочих процессов [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] добавляет шаблон рабочего процесса (в зависимости от его типа) в библиотеку или в список. Затем можно запустить шаблон рабочего процесса вручную или путем добавления или обновления элемента. Затем можно использовать [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] для отладки рабочего процесса.

> [!NOTE]
> При добавлении ссылок на другие сборки убедитесь, что эти сборки установлены в глобальном кэше сборок ( [!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)] ). В противном случае решение рабочего процесса завершится ошибкой. Сведения об установке сборок см. в разделе [Запуск рабочего процесса по документу или элементу вручную](https://support.office.com/article/Manually-start-a-workflow-on-a-document-or-item-5C106E0E-6FF2-4A75-AF99-F01653BC7963).

 Однако процесс развертывания не запускает рабочий процесс. Необходимо запустить рабочий процесс с веб-сайта SharePoint. Кроме того, Рабочий процесс можно запустить с помощью клиентского приложения, например Microsoft Office Word 2010 или с помощью отдельного серверного кода. Используйте один из подходов, указанных в **мастере настройки SharePoint**.

 Например, если вы указали, что рабочий процесс можно запустить вручную, запустите рабочий процесс непосредственно из элемента в библиотеке или списке. Дополнительные сведения о запуске рабочего процесса вручную см. в разделе [Запуск рабочего процесса для элемента документа вручную](https://support.office.com/article/Manually-start-a-workflow-on-a-document-or-item-5C106E0E-6FF2-4A75-AF99-F01653BC7963).

## <a name="debug-feature-event-receivers"></a>Отладить приемники событий компонентов
 По умолчанию при запуске [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] приложения SharePoint его функции автоматически активируются на сервере SharePoint. Однако это вызывает проблемы при отладке приемников событий компонентов, так как когда функция активируется [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , она выполняется в процессе, отличном от процесса отладчика. Это означает, что некоторые функции отладки, такие как точки останова, будут работать неправильно.

 Чтобы отключить автоматическую активацию компонента в SharePoint и разрешить правильную отладку приемников событий компонентов, задайте для свойства **Активная конфигурация развертывания** проекта значение **без активации** перед отладкой. Затем, после начала отладки вашего приложения SharePoint в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], вручную активируйте компонент в SharePoint. Чтобы активировать эту функцию, откройте меню **действия сайта** в SharePoint, выберите **Параметры сайта**, щелкните ссылку **Управление компонентами сайта** , а затем нажмите кнопку **активировать** рядом с компонентом, чтобы продолжить отладку как обычную.

## <a name="enable-enhanced-debugging-information"></a>Включить улучшенную отладочную информацию
 Из-за некоторых сложных взаимодействий между [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] процессом (devenv.exe), [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] процессом узла sharepoint (*vssphost4.exe*), SharePoint и уровнем WCF диагностика ошибок, возникающих при сборке, развертывании и т. д., может быть сложной задачей. Чтобы помочь вам устранить такие ошибки, можно включить улучшенную отладочную информацию. Для этого перейдите к следующему разделу реестра в реестре Windows:

 **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\11.0\SharePointTools**

 Если значение **REG_DWORD** "енабледиагностикс" еще не существует, создайте его вручную. Задайте для параметра "Енабледиагностикс" значение "1".

 Если задать для этого ключа значение 1, данные трассировки стека будут отображаться в окне **вывода** при каждом возникновении ошибок системы проекта во время работы в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Чтобы отключить отображение подробной отладочной информации, снова задайте для EnableDiagnostics значение 0 или удалите значение.

 Дополнительные сведения о других разделах реестра SharePoint см. [в разделе расширения отладки для инструментов SharePoint в Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>См. также раздел
- [Устранение неполадок решений SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md)
