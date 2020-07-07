---
title: Расширение инструментов SharePoint в Visual Studio | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: overview
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
ms.openlocfilehash: 7dc0cc0d0af73d032d870629877b62c94e6b347b
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: ru-RU
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016041"
---
# <a name="extend-the-sharepoint-tools-in-visual-studio"></a>Расширение средств SharePoint в Visual Studio
  Средства SharePoint в Visual Studio соответствуют требованиям многих сценариев разработки приложений. Однако вы можете обнаружить случаи, когда они не предоставляют никаких функциональных возможностей, которые требуются для вас или других разработчиков. В таких случаях можно расширить средства SharePoint, чтобы создать необходимые функции.

## <a name="how-to-extend-the-sharepoint-tools"></a>Расширение инструментов SharePoint
 В окне **Обозреватель сервера** можно расширить систему проектов SharePoint и узел **подключения SharePoint** .

### <a name="extend-the-sharepoint-project-system"></a>Расширение системы проектов SharePoint
 Visual Studio включает набор шаблонов проектов и шаблонов элементов, которые можно использовать для создания решений SharePoint. Например, существуют шаблоны для приемников событий, определений списков, рабочих процессов и веб-части. Однако можно также определить собственные типы элементов проектов SharePoint для создания таких компонентов SharePoint, как поля или настраиваемые действия. Кроме того, можно создавать расширения для типов элементов проектов SharePoint, уже установленных в Visual Studio, а также создавать расширения для проектов SharePoint.

 Дополнительные сведения см. [в разделе расширение системы проектов SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).

### <a name="extend-the-sharepoint-connections-node-in-server-explorer"></a>Расширение узла подключений SharePoint в обозреватель сервера
 В Visual Studio можно использовать узел **подключения SharePoint** в окне **Обозреватель сервера** для просмотра многих компонентов одного или нескольких локальных сайтов SharePoint в иерархическом представлении дерева. Узел **подключения SharePoint** также можно расширить следующими способами.

- Путем добавления собственных узлов. Это полезно, если необходимо отобразить компоненты сайтов SharePoint, которые не отображаются по умолчанию.

- Путем расширения существующих узлов. Например, можно добавить новый дочерний узел в существующий узел или добавить к узлу пункт контекстного меню и выполнять задачи, когда разработчик щелкает пункт меню.

  Дополнительные сведения см. [в разделе Расширение узла подключений SharePoint в обозреватель сервера](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

## <a name="development-computer-requirements"></a>Требования к компьютеру по разработке
 Для создания расширений для инструментов SharePoint компьютер разработчика должен удовлетворять тем же требованиям для создания решений SharePoint в Visual Studio.

 Также рекомендуется установить [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)] . Пакет SDK содержит шаблоны проектов и средства, которые можно использовать для расширения возможностей Visual Studio. В частности, пакет SDK содержит шаблон проекта, который можно использовать для простого создания пакета расширения Visual Studio (VSIX). Пакеты VSIX являются предпочтительным способом развертывания расширений Visual Studio в Visual Studio. Все расширения инструментов SharePoint должны быть развернуты с помощью пакетов VSIX. Во всех пошаговых руководствах в этой документации предполагается, что у вас [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)] установлен.

 Сведения об установке пакета SDK для Visual Studio см. в разделе [Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md). Дополнительные сведения о расширениях Visual Studio см. [в разделе Начало разработки расширений Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md).

## <a name="see-also"></a>См. также раздел

- [Общие сведения о модели программирования расширений инструментов SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
- [Расширение системы проектов SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
- [Расширение узла подключений SharePoint в обозреватель сервера](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Основные понятия и функции программирования для расширений инструментов SharePoint](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)
- [Справочные материалы &#40;расширяемости средств SharePoint&#41;](../sharepoint/reference-sharepoint-tools-extensibility.md)
- [Расширения отладки для инструментов SharePoint в Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)
- [Развертывание расширений для инструментов SharePoint в Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)