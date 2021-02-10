---
title: Расширение упаковки и развертывания SharePoint | Документация Майкрософт
description: Расширьте упаковку и развертывание SharePoint. Создание шагов и конфигураций развертывания. Обрабатывает конфликты развертывания. Настройка правил проверки.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: cd4967e38738018f9b30365575a2dcb9e8970963
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948756"
---
# <a name="extend-sharepoint-packaging-and-deployment"></a>Расширение упаковки и развертывания SharePoint
  Вы можете расширить процесс упаковки и развертывания для проектов SharePoint.

## <a name="create-deployment-steps"></a>Создание шагов по развертыванию
 При развертывании проекта SharePoint [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] выполняет ряд шагов развертывания. Visual Studio включает встроенные шаги развертывания для многих задач, например для отзыва или добавления решений. Однако вы также можете создать собственные шаги развертывания.

 Пошаговое руководство, в котором показано, как создать шаг развертывания, см. в разделе [Пошаговое руководство. Создание настраиваемого шага развертывания для проектов SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).

## <a name="create-deployment-configurations"></a>Создание конфигураций развертывания
 Конфигурация развертывания представляет собой набор шагов развертывания, который выполняется для данного проекта, но может повлиять на все элементы проекта SharePoint. Каждая конфигурация развертывания содержит один набор шагов, который выполняется при развертывании проекта, и другой набор, который выполняется при отзыве проекта. [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] включает две встроенные конфигурации развертывания, но вы также можете создать собственные. При создании конфигурации развертывания можно включить встроенные шаги развертывания, а также специально созданные шаги.

 Пошаговое руководство, в котором показано, как создать конфигурацию развертывания, см. в разделе [Пошаговое руководство. Создание настраиваемого шага развертывания для проектов SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).

## <a name="run-code-when-a-sharepoint-solution-is-deployed-or-retracted"></a>Выполнение кода при развертывании или отзыве решения SharePoint
 Для выполнения дополнительных задач при развертывании или отзыве решения SharePoint можно настроить обработку событий. Visual Studio создает события, которые можно обрабатывать, в следующих сценариях.

- До и после выполнения каждого шага развертывания для элемента проекта SharePoint. Дополнительные сведения см. [в разделе инструкции. выполнение кода при выполнении шагов развертывания](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md).

- До и после развертывания или отзыва проекта SharePoint. Дополнительные сведения см. [в разделе инструкции. выполнение кода при развертывании или отзыве проекта SharePoint](../sharepoint/how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted.md).

## <a name="handle-deployment-conflicts"></a>Обработку конфликтов развертывания
 Некоторые типы элементов проекта SharePoint, включая модули, веб-части, экземпляры списков и типы содержимого, предоставляют встроенную функцию разрешения конфликтов развертывания. При развертывании решения, содержащего один из таких элементов проекта, Visual Studio сначала проверяет, существует ли на сайте SharePoint файл с тем же именем, URL-адресом или идентификатором, что и файл в развертываемом элементе. В случае обнаружения конфликта Visual Studio может автоматически разрешить его или запросить у пользователя, следует ли Visual Studio разрешить конфликт или отменить развертывание. Для получения дополнительной информации см. [Troubleshooting SharePoint Packaging and Deployment](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).

 Эту возможность можно расширить, добавив собственный код, который проверяет наличие конфликтов развертывания и разрешает их. Дополнительные сведения см. [в разделе как управлять конфликтами развертывания](../sharepoint/how-to-handle-deployment-conflicts.md).

## <a name="run-command-line-operations-before-or-after-a-project-is-deployed"></a>Выполнять операции командной строки до или после развертывания проекта
 Чтобы выполнить операцию командной строки при развертывании решения SharePoint, можно задать свойства <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.PreDeploymentCommand%2A> и <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.PostDeploymentCommand%2A> объекта <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>. Visual Studio выполнит эти команды до и после развертывания проекта.

 В некоторых случаях могут возникать конфликты развертывания. Существует несколько способов разрешения конфликтов. Дополнительные сведения см. в разделе [Устранение неполадок упаковки и развертывания SharePoint](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).

## <a name="customize-validation-rules"></a>Настройка правил проверки
 Перед развертыванием пакета решения (WSP-файла) можно создать настраиваемые правила проверки компонентов и пакетов для проверки допустимости компонента или пакета. Например, можно передать разработчикам сведения, предупреждения или ошибки, которые помогут им устранить проблемы проверки. Дополнительные сведения см. в разделе [Практическое руководство. Создание пользовательских правил проверки компонентов и пакетов для решений SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).

## <a name="see-also"></a>См. также раздел
- [Инструкции. выполнение кода при выполнении шагов развертывания](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)
- [Пошаговое руководство. Создание настраиваемого шага развертывания для проектов SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)
- [Как создать настраиваемые правила проверки компонентов и пакетов для решений SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)
- [Расширение системы проектов SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
