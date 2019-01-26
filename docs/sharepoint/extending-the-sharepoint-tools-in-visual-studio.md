---
title: Расширение инструментов SharePoint в Visual Studio | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio, extending tools
- extensibility [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, extending tools
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7d70d9b5bac260dc0731d06ebb11780114f0edf5
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2019
ms.locfileid: "54867173"
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

- Путем добавления собственных узлов. Это полезно, если вы хотите отображать компоненты сайтов SharePoint, которые не отображаются по умолчанию.

- Путем расширения существующих узлов. Например можно добавить новый дочерний узел в существующий узел, или можно добавить пункта контекстного меню к узлу и выполнять задачи, когда разработчик щелкает пункт меню.

  Дополнительные сведения см. в разделе [расширение узла подключений SharePoint в обозревателе серверов](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

## <a name="development-computer-requirements"></a>Требования к компьютеру разработки
 Для создания расширений для инструментов SharePoint, на компьютере разработчика должен удовлетворять те же требования для создания решений SharePoint в Visual Studio.

 Мы также рекомендуем установить [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. Пакет SDK включает шаблоны проектов и средства, которые можно использовать для расширения Visual Studio. В частности пакет SDK включает шаблон проекта, которые можно использовать для создания пакетов Visual Studio Extension (VSIX). Пакеты VSIX являются предпочтительным способом развертывания расширений Visual Studio в Visual Studio. Все расширения инструментов SharePoint должны быть развернуты с помощью пакетов VSIX. Все примеры в этой документации предполагается, что у вас есть [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)] установлен.

 Чтобы установить пакет SDK для Visual Studio, см. в разделе [установка Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md). Дополнительные сведения о расширениях Visual Studio см. в разделе [начинается разработка расширений Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md).

## <a name="see-also"></a>См. также

- [Обзор модели программирования SharePoint средств расширения](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
- [Расширение системы проектов SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
- [Расширение узла подключений SharePoint в обозревателе серверов](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Основные понятия программирования и функции для расширения инструментов SharePoint](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)
- [Справочник по &#40;расширения инструментов SharePoint&#41;](../sharepoint/reference-sharepoint-tools-extensibility.md)
- [Отладка расширений для инструментов SharePoint в Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)
- [Развертывание расширений для инструментов SharePoint в Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)