---
title: Устранение неполадок SharePoint упаковки и развертывания | Документация Майкрософт
ms.custom: ''
ms.date: 02/22/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VSTO.WorkflowDeployment.Troubleshooting
- VS.SharePointTools.Project.PackageRetraction
- VS.SharePointTools.Deployment.Troubleshooting
- VS.SharePointTools.Deploying.Troubleshooting
- VS.SharePointTools.Project.DeploymentTroubleshooting
- VS.SharePointTools.Project.SharePointNotInstalled
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packaging
- SharePoint development in Visual Studio, troubleshooting
- SharePoint development in Visual Studio, deployment conflict resolution
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 46cd388079db9d7869bcae733c6baef33c07a212
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/27/2018
ms.locfileid: "53805137"
---
# <a name="troubleshoot-sharepoint-packaging-and-deployment"></a>Устранение неполадок SharePoint упаковки и развертывания
  В разделе рассмотрены различные проблемы, которые могут возникнуть при упаковке и развертывании решений SharePoint.

## <a name="enable-enhanced-debugging"></a>Включение улучшенной отладки
 Чтобы выявить причины неполадок в Visual Studio, SharePoint и на других уровнях, можно воспользоваться разделом реестра EnableDiagnostics для просмотра трассировки стека. Дополнительные сведения см. в разделе [решений SharePoint Отладка](../sharepoint/debugging-sharepoint-solutions.md).

## <a name="add-project-output-to-the-solution-package"></a>Добавление выходных данных проекта в пакет решения
 Выходные данные проекта можно добавлять с помощью "Конструктора пакетов". Однако при добавлении выходных данных пакета, убедитесь, что платформа проекта соответствует платформе решения SharePoint. Мы рекомендуем использовать **любой ЦП** целевой платформы для сборок, которые вы хотите развернуть на сервере SharePoint. Дополнительные сведения см. в разделе [страница "Компиляция", конструктор проектов &#40;Visual Basic&#41; ](../ide/reference/compile-page-project-designer-visual-basic.md) и [компилятора диалоговое &#40;Visual Basic&#41;](../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md).

## <a name="validation-warnings-and-errors"></a>Предупреждения и ошибки проверки
 Средства разработки SharePoint в Visual Studio выполняют проверочные шаги для проверки правильности формирования пакета решения. Также, для компонентов и пакетов, можно создать пользовательские проверочные шаги. Дополнительные сведения см. в разделе [Как Создание пользовательских компонентов и пакетов правила проверки для решений SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).

## <a name="deployment-conflict-resolution"></a>Устранение конфликта развертывания
 При развертывании решения SharePoint может возникнуть конфликт, когда элемент на сервере и элемент в пакете решения имеют одинаковое имя, URL-адрес или идентификатор. Вы можете изменить **Устранение конфликта развертывания** свойство, чтобы разрешить, игнорировать о конфликте для модулей, веб-частей, экземпляры списка и содержимого типов или отчетов.

 В следующей таблице показаны параметры для **Устранение конфликта развертывания** свойство.

|Значение|Описание:|
|-----------|-----------------|
|Автоматический|Обнаруживает и разрешает конфликты автоматически.|
|Запрашивать|Обнаруживает и выводит отчет о конфликтах для разработчика перед их разрешением.|
|Нет|Не обнаруживает конфликты.|

## <a name="differences-between-f5-deployment"></a>Различия между развертываниями F5
 При использовании [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] для развертывания проекта SharePoint на локальном сервере SharePoint с целью тестирования и отладки, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] выполняет некоторые дополнительные действия.

1. Сброс службы IIS во время выполнения развертывания.

2. Автоматическое назначение рабочих процессов.

3. Задание в конструкторе пакетов порядка активации компонентов в соответствии с иерархией.

   Можно добавить пользовательские действия по развертыванию дальнейших изменениях **F5** поведение. Дополнительные сведения см. в разделе [Пошаговое руководство: Создание пользовательского шага развертывания для проектов SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).

## <a name="delay-displaying-sharepoint-page-when-deploy-visual-web-part"></a>Задержка в отображении страницы SharePoint при развертывании визуальной веб-части
 Странице SharePoint требуется длительный промежуток времени для отображения при развертывании визуальной веб-части в папке Bin в [!INCLUDE[wiprlhext](../sharepoint/includes/wiprlhext-md.md)], [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] или [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)]. При изменении любых файлов каталога верхнего уровня [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)], например, каталога Bin, происходит рекомпилирование всего веб-приложения. Это может привести к задержке рендеринга страницы SharePoint до 25 секунд.

### <a name="error-message"></a>Сообщение об ошибке
 Отсутствует.

### <a name="resolution"></a>Решение
 Чтобы решить эту проблему, выполните следующие действия:

1.  Установите обновление кв967535, как описано в статье службы поддержки Майкрософт [ИСПРАВЛЕНИЯ: Доступно исправление для решения двух проблем ASP.NET в IIS 7.0 для Windows Vista и Windows Server 2008](http://go.microsoft.com/fwlink/?LinkId=179055).

2.  Добавьте следующую строку в файл Web.config:

    ```xml
    <compilation batch="false" optimizeCompilations="true">
    ```

## <a name="sharepoint-project-deployment-fails-with-error-failed-to-extract-the-cab-file-in-the-solution"></a>Развертывание проекта SharePoint происходит сбой с ошибкой «Не удалось извлечь CAB-файл в решении»
 Если имя любого элемента проекта SharePoint содержит круглые скобки, при развертывании решения возникнет ошибка.

### <a name="error-message"></a>Сообщение об ошибке
 Произошла ошибка в шаге развертывания «Добавление решения»: Не удалось извлечь CAB-файл в решении.

### <a name="resolution"></a>Решение
 Чтобы решить эту проблему, удалите круглые скобки в именах элементов проектов SharePoint.

## <a name="error-appears-when-deploying-a-visual-web-part-to-a-site-on-a-different-web-application"></a>Ошибка при развертывании визуальной веб-части на сайт другого веб-приложения
 При первом развертывании визуальной веб-части на сайт веб-приложения, отличного от развернутого в настоящий момент (в результате изменения свойства веб-части SiteUrl), возникает сообщение об ошибке.

### <a name="error-message"></a>Сообщение об ошибке
 Произошла ошибка в шаге развертывания «Добавление решения»: Компонент с Идентификатором [#] уже установлен на этой ферме. Используйте атрибут "force" для явной переустановки компонента.

### <a name="resolution"></a>Решение
 Эта ошибка возникает из-за механизма отзыва компонентов визуальных веб-частей в SharePoint. Для успешного развертывания визуальной веб-части, повторите развертывание, выбрав **F5** ключ.

## <a name="warning-appears-when-deploying-nested-user-controls"></a>Предупреждение появляется при развертывании вложенных пользовательских элементов управления
 Это предупреждение появляется при развертывании решения SharePoint, которое содержит вложенные пользовательские элементы управления, например визуальная веб-часть содержит пользовательский элемент управления или пользовательский элемент управления содержит веб-часть или другой пользовательский элемент управления. Это предупреждение появляется при добавлении элемента управления в конструктор, перетащив его с панели инструментов или с помощью @Register директив в представлении источника.

### <a name="error-message"></a>Сообщение об ошибке
 Предупреждение 1: элемент "[*имя элемента управления*]" не является известным элементом. Это может произойти, если существует ошибка компиляции или отсутствует файл web.config.

### <a name="resolution"></a>Решение
 Если [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] системе проектов не имеет сведений о вложенных пользовательских элементах управления, он не может предоставить IntelliSense и выдает предупреждение. Системе проектов не знают о вложенных пользовательских элементах управления, если проект не построен, а конструктор не закрытия и повторного открытия или автоматически отозвать параметр включен, который вызывает пользовательский элемент управления к отзыву из куста SharePoint после отладки.

 Чтобы удалить это предупреждение, постройте проект, закройте и повторно откройте конструктор или отключите параметр автоматического отзыва для проекта. Для этого снимите **автоматически отозвать после отладки** флажок на **SharePoint** вкладка диалогового окна свойств проекта.

## <a name="see-also"></a>См. также

- [Упаковка и развертывание решений SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)