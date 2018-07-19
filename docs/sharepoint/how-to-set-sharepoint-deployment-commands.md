---
title: 'Практическое: Установка команд развертывания SharePoint | Документация Майкрософт'
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
ms.openlocfilehash: 060acd0164ff7819d2abfb8d92f2394b4bcc0672
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/29/2018
ms.locfileid: "37119969"
---
# <a name="how-to-set-sharepoint-deployment-commands"></a>Практическое: команд развертывания SharePoint набора
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
  
