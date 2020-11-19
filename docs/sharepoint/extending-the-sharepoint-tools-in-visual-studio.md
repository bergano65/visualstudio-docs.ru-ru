---
title: Расширение инструментов SharePoint в Visual Studio | Документация Майкрософт
description: Расширение средств SharePoint в Visual Studio. Расширение системы проектов SharePoint. Расширение узла подключений SharePoint в обозревателе сервера.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: a921f45ea151ce7ee3313dba47e81a5acc86063d
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672630"
---
# <a name="extend-the-sharepoint-tools-in-visual-studio"></a>Расширение средств SharePoint в Visual Studio
  Инструменты SharePoint в Visual Studio соответствуют требованиям многих сценариев разработки приложений. Однако в некоторых случаях вам или другим разработчикам может не хватать функциональных возможностей, предоставляемых этими инструментами. В таких случаях можно расширить инструменты SharePoint, чтобы создать необходимые функциональные возможности.

## <a name="how-to-extend-the-sharepoint-tools"></a>Как расширить инструменты SharePoint
 Вы можете расширить систему проектов SharePoint и узел **Подключения SharePoint** в окне **обозревателя сервера**.

### <a name="extend-the-sharepoint-project-system"></a>Расширение системы проектов SharePoint
 В Visual Studio имеется ряд шаблонов проектов и шаблонов элементов, которые можно использовать для создания решений SharePoint. Например, существуют шаблоны для приемников событий, определений списков, рабочих процессов и веб-частей. Вы также можете определять свои собственные типы элементов проекта SharePoint для создания таких компонентов SharePoint, как поля или настраиваемые действия. Кроме того, вы можете создавать расширения для типов элементов проекта SharePoint, которые уже установлены в Visual Studio, и расширения для проектов SharePoint.

 Дополнительные сведения см. в разделе [Расширение системы проектов SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).

### <a name="extend-the-sharepoint-connections-node-in-server-explorer"></a>Расширение узла подключений SharePoint в обозревателе сервера
 В Visual Studio вы можете использовать узел **Подключения SharePoint** в окне **обозревателя сервера** для просмотра многих компонентов одного или нескольких локальных сайтов SharePoint в иерархическом представлении в виде дерева. Вы также можете расширять узел **Подключения SharePoint** следующими способами.

- Путем добавления собственных узлов. Этот способ удобен, когда вам нужно отображать компоненты сайтов SharePoint, которые не отображаются по умолчанию.

- Путем расширения существующих узлов. Например, можно добавить в существующий узел новый дочерний узел или добавить в узел пункт контекстного меню, чтобы разработчик мог выполнять задачи, нажав этот пункт меню.

  Дополнительные сведения см. в разделе [Расширение узла подключений SharePoint в обозревателе серверов](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

## <a name="development-computer-requirements"></a>Требования к компьютеру разработки
 Чтобы можно было создавать расширения для инструментов SharePoint, ваш компьютер разработки должен соответствовать требованиям, предусмотренным для создания решений SharePoint в Visual Studio.

 Также рекомендуется установить [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]. В этом пакете SDK содержатся шаблоны проектов и инструменты, которые можно использовать для расширения Visual Studio. В частности, в нем имеется проект шаблона, с помощью которого можно легко создать пакет Visual Studio Extension (VSIX). Пакеты VSIX являются рекомендуемым способом развертывания расширений Visual Studio в Visual Studio. Все расширения инструментов SharePoint должны развертываться с помощью пакетов VSIX. Во всех пошаговых руководствах в данном комплекте документации предполагается, что [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)] установлен.

 Сведения об установке пакета SDK для Visual Studio см. в разделе [Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md). Дополнительные сведения о расширениях Visual Studio см. в разделе [Начало разработки расширений Visual Studio](../extensibility/starting-to-develop-visual-studio-extensions.md).

## <a name="see-also"></a>См. также раздел

- [Обзор модели программирования расширений инструментов SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
- [Расширение системы проектов SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
- [Расширение узла подключений SharePoint в обозревателе сервера](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Концепции и функции программирования для расширений инструментов SharePoint](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)
- [Справочник "Возможности расширения инструментов SharePoint"](../sharepoint/reference-sharepoint-tools-extensibility.md)
- [Отладка расширений для инструментов SharePoint в Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)
- [Развертывание расширений для инструментов SharePoint в Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)