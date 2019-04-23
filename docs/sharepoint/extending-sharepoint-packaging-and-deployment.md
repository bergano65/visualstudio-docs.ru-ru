---
title: Расширение SharePoint Packaging and Deployment | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4bb98e2b1c83ff06570a77dc84ce6a7bf690f81d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60097002"
---
# <a name="extend-sharepoint-packaging-and-deployment"></a>Расширение SharePoint упаковки и развертывания
  Вы можете расширить процесс упаковки и развертывания для проектов SharePoint.

## <a name="create-deployment-steps"></a>Создание шагов развертывания
 При развертывании проекта SharePoint [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] выполняет ряд шагов развертывания. Visual Studio включает встроенные шаги развертывания для многих задач, например для отзыва или добавления решений. Однако вы также можете создать собственные шаги развертывания.

 Пошаговое руководство по созданию шага развертывания, см. в разделе [Пошаговое руководство: Создание пользовательского шага развертывания для проектов SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).

## <a name="create-deployment-configurations"></a>Создание конфигураций развертывания
 Конфигурация развертывания представляет собой набор шагов развертывания, который выполняется для данного проекта, но может повлиять на все элементы проекта SharePoint. Каждая конфигурация развертывания содержит один набор шагов, который выполняется при развертывании проекта, и другой набор, который выполняется при отзыве проекта. [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] включает две встроенные конфигурации развертывания, но можно также создать свои собственные. При создании конфигурации развертывания можно включить встроенные шаги развертывания, а также специально созданные шаги.

 Пошаговое руководство по созданию конфигурации развертывания, см. в разделе [Пошаговое руководство: Создание пользовательского шага развертывания для проектов SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).

## <a name="run-code-when-a-sharepoint-solution-is-deployed-or-retracted"></a>Выполнения кода при развертывании или отзыве решения SharePoint
 Для выполнения дополнительных задач при развертывании или отзыве решения SharePoint можно настроить обработку событий. Visual Studio создает события, которые можно обрабатывать, в следующих сценариях.

- До и после выполнения каждого шага развертывания для элемента проекта SharePoint. Дополнительные сведения см. в разделе [Как Выполнения кода при выполнении шагов развертывания](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md).

- До и после развертывания или отзыва проекта SharePoint. Дополнительные сведения см. в разделе [Как Выполнения кода при развертывания или отзыва проекта SharePoint](../sharepoint/how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted.md).

## <a name="handle-deployment-conflicts"></a>Обработка конфликтов развертывания
 Некоторые типы элементов проекта SharePoint, включая модули, веб-части, экземпляры списков и типы содержимого, предоставляют встроенную функцию разрешения конфликтов развертывания. При развертывании решения, содержащего один из таких элементов проекта, Visual Studio сначала проверяет, существует ли на сайте SharePoint файл с тем же именем, URL-адресом или идентификатором, что и файл в развертываемом элементе. В случае обнаружения конфликта Visual Studio может автоматически разрешить его или запросить у пользователя, следует ли Visual Studio разрешить конфликт или отменить развертывание. Для получения дополнительной информации см. [Troubleshooting SharePoint Packaging and Deployment](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).

 Эту возможность можно расширить, добавив собственный код, который проверяет наличие конфликтов развертывания и разрешает их. Дополнительные сведения см. в разделе [Как Обработка конфликтов развертывания](../sharepoint/how-to-handle-deployment-conflicts.md).

## <a name="run-command-line-operations-before-or-after-a-project-is-deployed"></a>Для запуска до или после развертывания проекта
 Чтобы выполнить операцию командной строки при развертывании решения SharePoint, можно задать свойства <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.PreDeploymentCommand%2A> и <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.PostDeploymentCommand%2A> объекта <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>. Visual Studio выполнит эти команды до и после развертывания проекта.

 В некоторых случаях могут возникать конфликты развертывания. Существует несколько способов разрешения конфликтов. Дополнительные сведения см. в разделе [SharePoint, устранение неполадок с упаковкой и развертыванием](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).

## <a name="customize-validation-rules"></a>Настройка правил проверки
 Перед развертыванием пакета решения (WSP-файла) можно создать настраиваемые правила проверки компонентов и пакетов для проверки допустимости компонента или пакета. Например, можно передать разработчикам сведения, предупреждения или ошибки, которые помогут им устранить проблемы проверки. Дополнительные сведения см. в разделе [Как Создание пользовательских компонентов и пакетов правила проверки для решений SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).

## <a name="see-also"></a>См. также
- [Практическое руководство. Выполнения кода при выполнении шагов развертывания](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)
- [Пошаговое руководство: Создание пользовательского шага развертывания для проектов SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)
- [Практическое руководство. Создание пользовательских компонентов и пакетов правила проверки для решений SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)
- [Расширение системы проектов SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
