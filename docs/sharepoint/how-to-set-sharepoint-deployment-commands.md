---
title: Как задать команды развертывания SharePoint | Документация Майкрософт
description: Узнайте, как настроить процесс развертывания, задав команды, выполняемые перед развертыванием SharePoint и после него.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 72938f316be22cd9b2eab2d7dab893c9370fb0ad
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965854"
---
# <a name="how-to-set-sharepoint-deployment-commands"></a>Как задать команды развертывания SharePoint
  Процесс развертывания можно настроить, задав команды, выполняемые перед развертыванием и после него. Эти команды выполняются до и после других действий по развертыванию при отладке решений SharePoint из Visual Studio.

### <a name="to-add-a-pre-deployment-command"></a>Добавление команды перед развертыванием

1. В строке меню выберите   >  **\<*ProjectName*> Свойства** проекта.

2. Перейдите на вкладку **SharePoint** .

3. В текстовом поле **Командная строка перед развертыванием** введите команды MS-DOS или MSBuild, чтобы настроить этот шаг.

     Например, чтобы вывести содержимое каталога перед завершением развертывания, введите **dir**.

### <a name="to-add-a-post-deployment-command"></a>Добавление команды после развертывания

1. В строке меню выберите   >  **\<*ProjectName*> Свойства** проекта.

2. Перейдите на вкладку **SharePoint** .

3. В текстовом поле **Командная строка после развертывания** введите команды MS-DOS или MSBuild для настройки этого шага.

     Например, чтобы получить список содержимого каталога после завершения развертывания, введите **dir**. Чтобы использовать переменную MSBuild для копирования сборки из каталога сборки, введите **Copy $ (TargetPath) к:\деплойментдиректори**.

## <a name="see-also"></a>См. также раздел
- [Упаковка и развертывание решений SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
