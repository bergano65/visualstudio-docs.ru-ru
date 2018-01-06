---
title: "Как: Установка команд развертывания SharePoint | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords: SharePoint development in Visual Studio, deploying
ms.assetid: 289c8c33-a603-434e-889f-a0d0a1736ecb
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: d5692195f340ce347df0bc6f8ad2d60225f24e6d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-sharepoint-deployment-commands"></a>Практическое руководство. Установка команд развертывания SharePoint
  Процесс развертывания можно настроить с помощью команды перед развертыванием и после развертывания. Эти команды выполняются до и после других действий по развертыванию при отладке решений SharePoint в Visual Studio.  
  
### <a name="to-add-a-pre-deployment-command"></a>Чтобы добавить команду перед развертыванием  
  
1.  В меню последовательно выберите **Проект**, *ProjectName***Свойства**.  
  
2.  Выберите **SharePoint** вкладки.  
  
3.  В **строка команды до развертывания** текста введите команды MS-DOS или MSBuild для настройки этого шага.  
  
     Например, чтобы вывести содержимое каталога перед завершением развертывания, введите **dir**.  
  
### <a name="to-add-a-post-deployment-command"></a>Добавление команды после развертывания  
  
1.  В меню последовательно выберите **Проект**, *ProjectName***Свойства**.  
  
2.  Выберите **SharePoint** вкладки.  
  
3.  В **командной строки после развертывания** текста введите команды MS-DOS или MSBuild для настройки этого шага.  
  
     Например, чтобы вывести содержимое каталога после завершения развертывания, введите **dir**. Чтобы скопировать сборку из каталога построения с помощью переменной MSBuild, введите **скопируйте $(TargetPath) c:\DeploymentDirectory**.  
  
## <a name="see-also"></a>См. также  
 [Упаковка и развертывание решений SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  