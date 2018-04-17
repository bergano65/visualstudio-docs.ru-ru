---
title: 'Как: Установка команд развертывания SharePoint | Документы Microsoft'
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
- SharePoint development in Visual Studio, deploying
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8779ba4ee4cf9803982d9849b3af7c83930d8a5b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-set-sharepoint-deployment-commands"></a>Практическое руководство. Установка команд развертывания SharePoint
  Процесс развертывания можно настроить с помощью команды перед развертыванием и после развертывания. Эти команды выполняются до и после других действий по развертыванию при отладке решений SharePoint в Visual Studio.  
  
### <a name="to-add-a-pre-deployment-command"></a>Чтобы добавить команду перед развертыванием  
  
1.  В строке меню выберите **проекта**, * имя_проекта ***свойства**.  
  
2.  Выберите **SharePoint** вкладки.  
  
3.  В **строка команды до развертывания** текста введите команды MS-DOS или MSBuild для настройки этого шага.  
  
     Например, чтобы вывести содержимое каталога перед завершением развертывания, введите **dir**.  
  
### <a name="to-add-a-post-deployment-command"></a>Добавление команды после развертывания  
  
1.  В строке меню выберите **проекта**, * имя_проекта ***свойства**.  
  
2.  Выберите **SharePoint** вкладки.  
  
3.  В **командной строки после развертывания** текста введите команды MS-DOS или MSBuild для настройки этого шага.  
  
     Например, чтобы вывести содержимое каталога после завершения развертывания, введите **dir**. Чтобы скопировать сборку из каталога построения с помощью переменной MSBuild, введите **скопируйте $(TargetPath) c:\DeploymentDirectory**.  
  
## <a name="see-also"></a>См. также  
 [Упаковка и развертывание решений SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  