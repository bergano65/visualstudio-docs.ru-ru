---
title: Построение и отладка решений SharePoint | Документация Майкрософт
description: Научитесь выполнять сборку и отладку решений SharePoint и поймите отличие этих процессов от сборки и отладки других типов проектов в Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: overview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, building and debugging
- SharePoint development in Visual Studio, debugging
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: c16414e6a49d727cf6b2113184c507feb7a73569
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955797"
---
# <a name="build-and-debug-sharepoint-solutions"></a>Сборка и отладка решений SharePoint
  Сборка и отладка решений SharePoint в принципе не отличается от сборки и отладки других типов проектов в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. В этом разделе описываются существующие различия.

## <a name="project-output-for-sharepoint-solutions"></a>Выходные данные проекта для решений SharePoint
 При построении решений SharePoint создаются сборки и файл пакета решения (с расширением *WSP*). В следующей таблице показаны расположения этих файлов во время сборки.

|Элемент сборки|Папка выходных данных|
|----------------|-------------------|
|Сборка, база данных программы ( *.pdb*) и файлы *.wsp*.|*\<ProjectName>\bin\debug* или *\<ProjectName>\bin\release*|
|Файлы элементов проекта SharePoint.|*\<ProjectName>\pkg\debug* или *\<ProjectName>\pkg\release*|
|Создание промежуточных файлов.|*\<ProjectName>\obj\debug* или *\<ProjectName>\obj\release*|
|Упаковка промежуточных файлов.|*\<ProjectName>\pkgobj\debug* или *\<ProjectName>\pkgobj\release*|

## <a name="build-sharepoint-solutions"></a>Сборка решений SharePoint
 Для сборки решений SharePoint на компьютере разработчика должна быть установлена правильная версия сервера SharePoint. В остальных отношениях сборка решений SharePoint не отличается от сборки других типов проектов в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Дополнительные сведения см. в разделе [Практическое руководство. Сборка решений SharePoint](../sharepoint/how-to-build-sharepoint-solutions.md).

## <a name="debug-and-test-sharepoint-solutions"></a>Отладка и тестирование решений SharePoint
 Перед отладкой [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] копирует пакет *WSP* на сервер SharePoint, активирует компоненты сайта и веб-компоненты, и в некоторых случаях запускает проект. В других случаях может понадобиться открыть проект вручную. Дополнительные сведения см. в разделах [Устранение неполадок решений SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md) и [Отладка решений SharePoint](../sharepoint/debugging-sharepoint-solutions.md).

## <a name="debug-and-verify-sharepoint-solutions-by-using-azure-devops-services-features"></a>Отладка и проверка решений SharePoint с помощью возможностей Azure DevOps Services
 Возможности Azure DevOps Services, такие как модульное тестирование и IntelliTrace, обеспечивают качественный поиск проблем в решениях SharePoint. Профилирование позволяет найти и определить области с проблемами производительности в решениях SharePoint. Дополнительные сведения см. в разделах [Проверка и отладка кода SharePoint](../sharepoint/verifying-and-debugging-sharepoint-code.md) и [Профилирование производительности приложений SharePoint](../sharepoint/profiling-the-performance-of-sharepoint-applications.md).

## <a name="security-during-the-build-process"></a>Безопасность во время процесса сборки
 Для упаковки или развертывания решений SharePoint [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] должен иметь разрешение на копирование файлов на сервер SharePoint. Необходимо запустить [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] как процесс с повышенными привилегиями, а учетная запись пользователя должна быть администратором семейства сайтов на сервере SharePoint. Кроме того, необходимо указать, является ли проект изолированным решением или решением фермы. Дополнительные сведения см. в разделе [Различия между изолированными решениями и решениями фермы](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).

## <a name="using-the-clean-command"></a>Использование команды очистки
 При установке решения SharePoint на сервере SharePoint для отладки команда **Clean** не удаляет решение. Вместо этой команды необходимо отключить функции с помощью конфигурации SharePoint.

## <a name="see-also"></a>См. также раздел
- [Разработка решений SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Просмотр подключений SharePoint с помощью обозревателя сервера](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)
- [Упаковка и развертывание решений SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
