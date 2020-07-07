---
title: Как задать команды развертывания SharePoint | Документация Майкрософт
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: c2329efef64e7d8605f8483ff7dce3107cd702fa
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: ru-RU
ms.lasthandoff: 07/06/2020
ms.locfileid: "86015505"
---
# <a name="how-to-set-sharepoint-deployment-commands"></a>Как задать команды развертывания SharePoint
  Процесс развертывания можно настроить, задав команды, выполняемые перед развертыванием и после него. Эти команды выполняются до и после других действий по развертыванию при отладке решений SharePoint из Visual Studio.

### <a name="to-add-a-pre-deployment-command"></a>Добавление команды перед развертыванием

1. В строке меню выберите **Project**  >  ** \<*ProjectName*> Свойства**проекта.

2. Перейдите на вкладку **SharePoint** .

3. В текстовом поле **Командная строка перед развертыванием** введите команды MS-DOS или MSBuild, чтобы настроить этот шаг.

     Например, чтобы вывести содержимое каталога перед завершением развертывания, введите **dir**.

### <a name="to-add-a-post-deployment-command"></a>Добавление команды после развертывания

1. В строке меню выберите **Project**  >  ** \<*ProjectName*> Свойства**проекта.

2. Перейдите на вкладку **SharePoint** .

3. В текстовом поле **Командная строка после развертывания** введите команды MS-DOS или MSBuild для настройки этого шага.

     Например, чтобы получить список содержимого каталога после завершения развертывания, введите **dir**. Чтобы использовать переменную MSBuild для копирования сборки из каталога сборки, введите **Copy $ (TargetPath) к:\деплойментдиректори**.

## <a name="see-also"></a>См. также раздел
- [Упаковка и развертывание решений SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
