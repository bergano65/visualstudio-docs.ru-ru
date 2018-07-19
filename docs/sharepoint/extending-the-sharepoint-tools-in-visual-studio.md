---
title: Расширение инструментов SharePoint в Visual Studio | Документация Майкрософт
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio, extending tools
- extensibility [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, extending tools
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 4394c583d281f114392088ed6a346e05d084070e
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/22/2018
ms.locfileid: "36327311"
---
# <a name="extend-the-sharepoint-tools-in-visual-studio"></a>Расширения инструментов SharePoint в Visual Studio
  Средства SharePoint в Visual Studio требованиям многих сценариев разработки приложений. Однако бывают ситуации, где они не предоставляют функций, которые вы или другие разработчики. В таких случаях вы можете расширить средства SharePoint для создания необходимые функциональные возможности.  
  
## <a name="how-to-extend-the-sharepoint-tools"></a>Способы расширения средств SharePoint
 Можно расширить систему проекта SharePoint и **подключения SharePoint** узел в **обозревателя серверов** окна.  
  
### <a name="extend-the-sharepoint-project-system"></a>Расширение системы проектов SharePoint
 Visual Studio включает набор шаблонов проектов и шаблоны элементов, которые можно использовать для создания решений SharePoint. Например существуют шаблоны для приемников событий, определения списков, рабочие процессы и веб-частей. Тем не менее можно также определить собственные типы элементов проекта SharePoint для создания компонентов SharePoint, таких как поля и настраиваемые действия. Можно также создавать расширения для типов элементов проектов SharePoint, которые уже установлены в Visual Studio, а можно создавать расширения для проектов SharePoint.  
  
 Дополнительные сведения см. в разделе [расширение системы проектов SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).  
  
### <a name="extend-the-sharepoint-connections-node-in-server-explorer"></a>Расширение узла подключений SharePoint в обозревателе серверов
 В Visual Studio, можно использовать **подключения SharePoint** узел в **обозревателя серверов** окно для просмотра различных компонентов одного или нескольких локальных сайтов SharePoint в виде иерархического дерева. Также можно расширить **подключения SharePoint** узел одним из следующих способов:  
  
-   Путем добавления собственных узлов. Это полезно, если вы хотите отображать компоненты сайтов SharePoint, которые не отображаются по умолчанию.  
  
-   Путем расширения существующих узлов. Например можно добавить новый дочерний узел в существующий узел, или можно добавить пункта контекстного меню к узлу и выполнять задачи, когда разработчик щелкает пункт меню.  
  
 Дополнительные сведения см. в разделе [расширение узла подключений SharePoint в обозревателе серверов](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
## <a name="development-computer-requirements"></a>Требования к компьютеру разработки
 Для создания расширений для инструментов SharePoint, на компьютере разработчика должен удовлетворять те же требования для создания решений SharePoint в Visual Studio. Дополнительные сведения см. в разделе [требования по разработке решений SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
 Мы также рекомендуем установить [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. Пакет SDK включает шаблоны проектов и средства, которые можно использовать для расширения Visual Studio. В частности пакет SDK включает шаблон проекта, которые можно использовать для создания пакетов Visual Studio Extension (VSIX). Пакеты VSIX являются предпочтительным способом развертывания расширений Visual Studio в Visual Studio. Все расширения инструментов SharePoint должны быть развернуты с помощью пакетов VSIX. Все примеры в этой документации предполагается, что у вас есть [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)] установлен.  
  
 Чтобы установить пакет SDK для Visual Studio, см. в разделе [установка Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md). Дополнительные сведения о расширениях Visual Studio см. в разделе [начинается разработка расширений Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md).  
  
## <a name="see-also"></a>См. также
 [Обзор модели программирования SharePoint средств расширения](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)   
 [Расширение системы проектов SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)   
 [Расширение узла подключений SharePoint в обозревателе серверов](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Основные понятия программирования и функции для расширения инструментов SharePoint](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)   
 [Справочник по &#40;расширения инструментов SharePoint&#41;](../sharepoint/reference-sharepoint-tools-extensibility.md)   
 [Отладка расширений для инструментов SharePoint в Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)   
 [Развертывание расширений для инструментов SharePoint в Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  
