---
title: Построение и отладка решений SharePoint | Документация Майкрософт
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
ms.openlocfilehash: cf89354880059b8fe743e5558b2c406467a38014
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/22/2018
ms.locfileid: "36326118"
---
# <a name="build-and-debug-sharepoint-solutions"></a>Построение и отладка решений SharePoint
  Как правило, построение и отладка решений SharePoint является таким же, как построение и отладка других типов проектов в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. В этом разделе описываются существующие различия.  
  
## <a name="project-output-for-sharepoint-solutions"></a>Выходные данные проекта для решений SharePoint
 Построение решений SharePoint создаются сборки и пакет решения (*.wsp*) файла. В следующей таблице показано расположение этих файлов во время построения.  
  
|Создание элемента|Выходная папка|  
|----------------|-------------------|  
|Сборка, база данных программы (*.pdb*), и *.wsp* файлов.|*\<ИмяПроекта > \bin\debug* или  *\<имя_проекта > \bin\release*|  
|Файлы элементов проекта SharePoint.|*\<Имя проекта > \pkg\debug* или  *\<имя_проекта > \pkg\release*|  
|Создание промежуточных файлов.|*\<Имя проекта > \obj\debug* или  *\<имя_проекта > \obj\release*|  
|Пакет промежуточных файлов.|*\<Имя проекта > \pkgobj\debug* или  *\<имя_проекта > \pkgobj\release*|  
  
## <a name="build-sharepoint-solutions"></a>Построение решений SharePoint
 Для построения решений SharePoint, на компьютере разработчика должен иметь правильную версию установлен SharePoint server. В противном случае построение решений SharePoint совпадает со значением создания других типов проектов в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Дополнительные сведения см. в разделе [как: решений SharePoint построения](../sharepoint/how-to-build-sharepoint-solutions.md).  
  
## <a name="debug-and-test-sharepoint-solutions"></a>Отладка и тестирование решений SharePoint
 Перед отладкой [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] копий *.wsp* пакет сервера SharePoint, активирует сайт и веб-компоненты, а в некоторых случаях запускает проект. В других случаях может понадобиться открыть проект вручную. Дополнительные сведения см. в разделе [решений SharePoint, устранение неполадок](../sharepoint/troubleshooting-sharepoint-solutions.md) и [решений SharePoint Отладка](../sharepoint/debugging-sharepoint-solutions.md).  
  
## <a name="debug-and-verify-sharepoint-solutions-by-using-alm-features"></a>Отладка и проверка решений SharePoint с помощью возможностей ALM
 Возможности Visual Studio ALM, такие как модульное тестирование и IntelliTrace, обеспечивают качественный поиск проблем в решениях SharePoint. Профилирование позволяет найти и определить области с проблемами производительности в решениях SharePoint. Дополнительные сведения см. в разделе [проверка и отладка кода SharePoint](../sharepoint/verifying-and-debugging-sharepoint-code.md) и [профилирование производительности приложений SharePoint](../sharepoint/profiling-the-performance-of-sharepoint-applications.md).  
  
## <a name="security-during-the-build-process"></a>Безопасность во время процесса построения
 Для упаковки и развертывания решений SharePoint [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] должен иметь разрешение на копирование файлов на сервер SharePoint. Необходимо запустить [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] процессе с повышенными привилегиями и пользователя учетная запись должна быть администратор семейства сайтов на сервере SharePoint. Кроме того необходимо указать, является ли проект изолированное решение или решение фермы. Дополнительные сведения см. в разделе [различия между изолированными решениями и решениями фермы](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).  
  
## <a name="using-the-clean-command"></a>Использование команды очистки  
 При установке решения SharePoint на сервере SharePoint для отладки, **Очистить** команда не приводит к удалению решения. Вместо этого необходимо отключить компоненты с помощью конфигурации SharePoint.  
  
## <a name="see-also"></a>См. также
 [Разработка решений SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Просмотр подключений SharePoint с помощью обозревателя серверов](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)   
 [Упаковка и развертывание решений SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
 
