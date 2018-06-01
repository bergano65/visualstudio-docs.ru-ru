---
title: Построение и отладка решений SharePoint | Документы Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, building and debugging
- SharePoint development in Visual Studio, debugging
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e04f60ea5cfe72235bac6630b413c9c437255681
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/01/2018
ms.locfileid: "34691291"
---
# <a name="building-and-debugging-sharepoint-solutions"></a>Построение и отладка решений SharePoint
  Как правило, построение и отладка решений SharePoint является таким же, как построение и отладка других типов проектов в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. В этом разделе описываются существующие различия.  
  
## <a name="project-output-for-sharepoint-solutions"></a>Выходной файл проекта для решений SharePoint
 Построение решений SharePoint создаются сборки и файл пакета (.wsp) решения. Следующая таблица показывает расположение этих файлов во время построения.  
  
|Построение элементов|Выходная папка|  
|----------------|-------------------|  
|Сборки, база данных программы (PDB) и WSP-файлы.|*Имя_проекта*\bin\debug или *ProjectName*\bin\release|  
|Файлы элементов проекта SharePoint.|*Имя_проекта*\pkg\debug или *ProjectName*\pkg\release|  
|Построение промежуточных файлов.|*Имя_проекта*\obj\debug или *ProjectName*\obj\release|  
|Пакет промежуточных файлов.|*Имя_проекта*\pkgobj\debug или *ProjectName*\pkgobj\release|  
  
## <a name="build-sharepoint-solutions"></a>Построение решений SharePoint
 Для построения решений SharePoint на компьютере разработчика должен иметь правильную версию установлен SharePoint server. В противном случае построение решений SharePoint совпадает с создания других типов проектов в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Дополнительные сведения см. в разделе [как: построение решений SharePoint](../sharepoint/how-to-build-sharepoint-solutions.md).  
  
## <a name="debug-and-test-sharepoint-solutions"></a>Отладка и тестирование решений SharePoint
 Перед отладкой [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] копирует пакет .wsp на сервер SharePoint, активирует сайт и веб-компоненты и в некоторых случаях, запускает проект. В других случаях может понадобиться открыть проект вручную. Дополнительные сведения см. в разделе [Устранение неполадок решений SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md) и [отладка решений SharePoint](../sharepoint/debugging-sharepoint-solutions.md).  
  
## <a name="debug-and-verify-sharepoint-solutions-by-using-alm-features"></a>Отладка и проверка решений SharePoint с помощью возможностей ALM
 Возможности Visual Studio ALM, такие как модульное тестирование и IntelliTrace, обеспечивают качественный поиск проблем в решениях SharePoint. Профилирование позволяет найти и определить области с проблемами производительности в решениях SharePoint. Дополнительные сведения см. в разделе [проверка и отладка кода SharePoint](../sharepoint/verifying-and-debugging-sharepoint-code.md) и [профилирование производительности приложений SharePoint](../sharepoint/profiling-the-performance-of-sharepoint-applications.md).  
  
## <a name="security-during-the-build-process"></a>Безопасность во время процесса построения
 Для упаковки и развертывания решений SharePoint [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] должен иметь разрешение на копирование файлов на сервере SharePoint. Необходимо запустить [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] как процесс с повышенными правами и пользователь учетная запись должна быть администратором коллекции веб-сайтов на сервере SharePoint. Кроме того необходимо указать, является ли проект изолированное решение или решение фермы. Дополнительные сведения см. в разделе [различия между изолированными решениями и решениями фермы](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).  
  
## <a name="using-the-clean-command"></a>Использование команды очистки  
 При установке решения SharePoint на сервере SharePoint для отладки, **Очистить** команда удалит решение. Вместо этого необходимо отключить компоненты с помощью конфигурации SharePoint.  
  
## <a name="see-also"></a>См. также
 [Разработка решений SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Просмотр подключений SharePoint с помощью обозревателя серверов](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)   
 [Упаковка и развертывание решений SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
 