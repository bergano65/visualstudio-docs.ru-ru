---
title: Создание и отладка решений SharePoint | Документация Майкрософт
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e4b34df23c8cb612d72fed108a6c0aecbf57875c
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: ru-RU
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016365"
---
# <a name="build-and-debug-sharepoint-solutions"></a>Сборка и отладка решений SharePoint
  Как правило, создание и отладка решений SharePoint аналогичны созданию и отладке других типов проектов в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . В этом разделе описываются существующие различия.

## <a name="project-output-for-sharepoint-solutions"></a>Выходные данные проекта для решений SharePoint
 При построении решений SharePoint создаются сборки и файл пакета решения (*WSP*). В следующей таблице показаны расположения этих файлов во время сборки.

|Элемент сборки|Папка выходных данных|
|----------------|-------------------|
|Сборка, база данных программы (*pdb*) и *WSP* -файлы.|* \<ProjectName> \bin\Debug* или * \<ProjectName> \bin\Release*|
|Файлы элементов проекта SharePoint.|* \<ProjectName> \пкг\дебуг* или * \<ProjectName> \пкг\релеасе*|
|Создание промежуточных файлов.|* \<ProjectName> \обж\дебуг* или * \<ProjectName> \обж\релеасе*|
|Промежуточные файлы пакета.|* \<ProjectName> \пкгобж\дебуг* или * \<ProjectName> \пкгобж\релеасе*|

## <a name="build-sharepoint-solutions"></a>Создание решений SharePoint
 Для создания решений SharePoint на компьютере разработчика должна быть установлена правильная версия SharePoint Server. В противном случае создание решений SharePoint аналогично созданию проектов других типов в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Дополнительные сведения см. [в разделе руководство. построение решений SharePoint](../sharepoint/how-to-build-sharepoint-solutions.md).

## <a name="debug-and-test-sharepoint-solutions"></a>Отладка и тестирование решений SharePoint
 Перед отладкой [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] копирует пакет *WSP* на сервер SharePoint, активирует веб-узел и компоненты уровня Интернета, а в некоторых случаях запускает проект. В других случаях может понадобиться открыть проект вручную. Дополнительные сведения см. в разделе [Устранение неполадок решений SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md) и [Отладка решений SharePoint](../sharepoint/debugging-sharepoint-solutions.md).

## <a name="debug-and-verify-sharepoint-solutions-by-using-azure-devops-services-features"></a>Отладка и проверка решений SharePoint с помощью Azure DevOps Services компонентов
 Azure DevOps Services функции, такие как модульное тестирование и IntelliTrace, позволяют более точно выявлять проблемы в решениях SharePoint. Профилирование позволяет найти и определить области с проблемами производительности в решениях SharePoint. Дополнительные сведения см. в статьях [Проверка и отладка кода SharePoint](../sharepoint/verifying-and-debugging-sharepoint-code.md) и [Профилирование производительности приложений SharePoint](../sharepoint/profiling-the-performance-of-sharepoint-applications.md).

## <a name="security-during-the-build-process"></a>Безопасность во время процесса сборки
 Для упаковки или развертывания решений SharePoint [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] необходимо иметь разрешение на копирование файлов на сервер SharePoint. Необходимо запустить [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] в качестве процесса с повышенными привилегиями, а учетная запись пользователя должна быть администратором семейства веб-сайтов на сервере SharePoint. Кроме того, необходимо указать, является ли проект изолированным решением или решением фермы. Дополнительные сведения см. в разделе [различия между песочницами и решениями фермы](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).

## <a name="using-the-clean-command"></a>Использование команды Clean
 При установке решения SharePoint на сервере SharePoint для отладки команда **Clean** не удаляет решение. Вместо этого необходимо отключить функции с помощью конфигурации SharePoint.

## <a name="see-also"></a>См. также раздел
- [Разработка решений SharePoint](../sharepoint/developing-sharepoint-solutions.md)
- [Просмотр подключений SharePoint с помощью обозреватель сервера](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)
- [Упаковка и развертывание решений SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
