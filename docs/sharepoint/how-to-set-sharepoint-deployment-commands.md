---
title: Как выполнить Настройка команд развертывания SharePoint | Документация Майкрософт
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
ms.openlocfilehash: e76a1e4e19f8f3280b6da71dffa19d3a7e2c16a5
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2019
ms.locfileid: "54871784"
---
# <a name="how-to-set-sharepoint-deployment-commands"></a>Как выполнить Настройка команд развертывания SharePoint
  Процесс развертывания можно настроить, задав команды перед развертыванием и после развертывания. Эти команды выполняются до и после других действий по развертыванию, при отладке решений SharePoint в Visual Studio.  
  
### <a name="to-add-a-pre-deployment-command"></a>Чтобы добавить команду перед развертыванием  
  
1.  В строке меню выберите **проекта** > **\<*имя_проекта*> свойства**.  
  
2.  Выберите **SharePoint** вкладки.  
  
3.  В **Командная строка до развертывания** текста введите команды MS-DOS или MSBuild, чтобы настроить этот шаг.  
  
     Например, чтобы вывести список содержимого каталога перед завершением развертывания, введите **dir**.  
  
### <a name="to-add-a-post-deployment-command"></a>Добавление команды после развертывания  
  
1.  В строке меню выберите **проекта** > **\<*имя_проекта*> свойства**.  
  
2.  Выберите **SharePoint** вкладки.  
  
3.  В **строка команды после развертывания** текста введите команды MS-DOS или MSBuild, чтобы настроить этот шаг.  
  
     Например, чтобы вывести содержимое каталога после завершения развертывания, введите **dir**. Чтобы копировать сборку из каталога построения с помощью переменной MSBuild, введите **скопируйте $(TargetPath) c:\DeploymentDirectory**.  
  
## <a name="see-also"></a>См. также
 [Упаковка и развертывание решений SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
