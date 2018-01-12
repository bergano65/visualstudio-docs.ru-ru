---
title: "Расширение инструментов SharePoint в Visual Studio | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio, extending tools
- extensibility [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, extending tools
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: db0afa41641cd9d5ae04cfe6d391dbf0fe814f0f
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="extending-the-sharepoint-tools-in-visual-studio"></a>Расширение средств SharePoint в Visual Studio
  Средства SharePoint в Visual Studio, требованиям многих сценариев развертывания приложений. Однако бывают ситуации, где они не предоставляют функций, которые вы или другими разработчиками. В таких случаях можно расширения инструментов SharePoint для создания функциональных возможностей.  
  
## <a name="how-to-extend-the-sharepoint-tools"></a>Механизм расширения инструментов SharePoint  
 Можно расширить систему проектов SharePoint и **подключения SharePoint** узел в **обозревателя серверов** окна.  
  
### <a name="extending-the-sharepoint-project-system"></a>Расширение системы проектов SharePoint  
 Visual Studio включает набор шаблонов проектов и шаблонов элементов, которые можно использовать для создания решений SharePoint. Например существуют шаблоны для приемников событий, определения списков, рабочие процессы и веб-частей. Однако можно также определить собственные типы элементов проекта SharePoint для создания компонентов SharePoint, таких как поля и настраиваемые действия. Также можно создавать расширения для типов элементов проектов SharePoint, которые уже установлены в Visual Studio, и можно создавать расширения для проектов SharePoint.  
  
 Дополнительные сведения см. в разделе [расширение системы проектов SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).  
  
### <a name="extending-the-sharepoint-connections-node-in-server-explorer"></a>Расширение узла подключений SharePoint в обозревателе сервера  
 В Visual Studio можно использовать **подключения SharePoint** узел в**обозревателя серверов** служит для отображения различных компонентов одного или нескольких локальных сайтов SharePoint в режиме дерева иерархии. Кроме того, можно расширить **подключения SharePoint** узел следующим образом:  
  
-   Путем добавления собственных узлов. Это полезно, если требуется отображать компоненты сайтов SharePoint, которые не отображаются по умолчанию.  
  
-   Путем расширения имеющихся узлов. Например можно добавить новый дочерний узел в существующий узел или вы Добавление пункта контекстного меню к узлу и выполнять задачи, если разработчик выбирает пункт меню.  
  
 Дополнительные сведения см. в разделе [расширение узла подключений SharePoint в обозревателе серверов](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
## <a name="development-computer-requirements"></a>Требования к компьютеру разработчика  
 Для создания расширений для средств SharePoint, на компьютере разработчика должен соответствовать тем же требованиям для создания решений SharePoint в Visual Studio. Дополнительные сведения см. в разделе [требования к разработке решений SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
 Также рекомендуется установить [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. Пакет SDK включает шаблоны проектов и средства, которые можно использовать для расширения Visual Studio. В частности пакет SDK включает шаблон проекта, которые можно использовать для простого создания пакета расширения Visual Studio (VSIX). Пакеты VSIX являются предпочтительным способом развертывания расширений Visual Studio в Visual Studio. Все расширения инструментов SharePoint должны быть развернуты с помощью пакетов VSIX. Все примеры в этой документации предполагается, что вы [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)] установлен.  
  
 Чтобы установить пакет SDK для Visual Studio, в разделе [Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md). Дополнительные сведения о расширениях Visual Studio см. в разделе [начинается разработка расширений Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md).  
  
## <a name="see-also"></a>См. также  
 [Обзор SharePoint модели программирования расширений средств](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)   
 [Расширение системы проектов SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)   
 [Расширение узла подключений SharePoint в обозревателе серверов](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Основные понятия программирования и функции расширений SharePoint](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)   
 [Справочник по &#40; Расширения средств SharePoint &#41;](../sharepoint/reference-sharepoint-tools-extensibility.md)   
 [Отладка расширений для средств SharePoint в Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)   
 [Развертывание расширений для инструментов SharePoint в Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  