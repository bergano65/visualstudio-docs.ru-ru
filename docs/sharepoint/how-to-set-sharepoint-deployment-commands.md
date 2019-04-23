---
title: Практическое руководство. Настройка команд развертывания SharePoint | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7664dfcfe11d7ab7dc6ab03045533bbd9e69fb9c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60077788"
---
# <a name="how-to-set-sharepoint-deployment-commands"></a>Практическое руководство. Настройка команд развертывания SharePoint
  Процесс развертывания можно настроить, задав команды перед развертыванием и после развертывания. Эти команды выполняются до и после других действий по развертыванию, при отладке решений SharePoint в Visual Studio.

### <a name="to-add-a-pre-deployment-command"></a>Чтобы добавить команду перед развертыванием

1. В строке меню выберите **проекта** > **\<*имя_проекта*> свойства**.

2. Выберите **SharePoint** вкладки.

3. В **Командная строка до развертывания** текста введите команды MS-DOS или MSBuild, чтобы настроить этот шаг.

     Например, чтобы вывести список содержимого каталога перед завершением развертывания, введите **dir**.

### <a name="to-add-a-post-deployment-command"></a>Добавление команды после развертывания

1. В строке меню выберите **проекта** > **\<*имя_проекта*> свойства**.

2. Выберите **SharePoint** вкладки.

3. В **строка команды после развертывания** текста введите команды MS-DOS или MSBuild, чтобы настроить этот шаг.

     Например, чтобы вывести содержимое каталога после завершения развертывания, введите **dir**. Чтобы копировать сборку из каталога построения с помощью переменной MSBuild, введите **скопируйте $(TargetPath) c:\DeploymentDirectory**.

## <a name="see-also"></a>См. также
- [Упаковка и развертывание решений SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
