---
title: "Добавление файла app.config в проект в Visual Studio | Документация Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: CSharp
helpviewer_keywords: app.config files, adding to C# projects
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: d77e86599670ef04b813381da84a03ab1f238af3
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/13/2018
---
# <a name="how-to-add-an-application-configuration-file-to-a-c-project"></a>Практическое руководство. Добавление файла конфигурации приложения в проект C#

Добавив файл конфигурации приложения (файл app.config) в проект C#, вы можете настроить способ, которым общеязыковая среда выполнения будет находить и загружать файлы сборки. Дополнительные сведения о файлах конфигурации см. в описании того, [как среда выполнения находит сборки (.NET Framework)](/dotnet/framework/deployment/how-the-runtime-locates-assemblies).

> [!NOTE]
> Приложения UWP не содержат файл app.config.

При сборке проекта среда разработки автоматически копирует файл app.config, изменяет имя копии файла в соответствии с исполняемым файлом, а затем перемещает копию в каталог **bin**.

## <a name="to-add-an-application-configuration-file-to-a-c-project"></a>Добавление файла конфигурации приложения в проект C#

1. В строке меню выберите **Проект** > **Добавить новый элемент**.

     Откроется диалоговое окно **Добавление нового элемента**.

1. Разверните пункт **Установленные** > **Элементы Visual C#**, а затем выберите шаблон **Файл конфигурации приложения**.

3. В текстовое поле **Имя** введите имя и нажмите **Добавить**.

     A file named app.config is added to your project.

## <a name="see-also"></a>См. также

[Управление параметрами приложения (.NET)](../ide/managing-application-settings-dotnet.md)  
[Схема файла конфигурации (.NET Framework)](/dotnet/framework/configure-apps/file-schema/index)  
[Настройка приложений .NET Framework](/dotnet/framework/configure-apps/index)