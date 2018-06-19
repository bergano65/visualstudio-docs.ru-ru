---
title: Добавление файла app.config в проект в Visual Studio
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
dev_langs:
- CSharp
helpviewer_keywords:
- app.config files, adding to C# projects
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: b2182b0175d57d7283e63bdf408249fa7566da00
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31941978"
---
# <a name="how-to-add-an-application-configuration-file-to-a-c-project"></a>Практическое руководство. Добавление файла конфигурации приложения в проект C#

Добавив файл конфигурации приложения (файл *app.config*) в проект C#, вы можете настроить способ, которым общеязыковая среда выполнения будет находить и загружать файлы сборки. Дополнительные сведения о файлах конфигурации приложения см. в статье [Обнаружение сборок в среде выполнения (.NET Framework)](/dotnet/framework/deployment/how-the-runtime-locates-assemblies).

> [!NOTE]
> Приложения UWP не содержат файл *app.config*.

При сборке проекта среда разработки автоматически копирует файл *app.config*, изменяет имя копии файла в соответствии с исполняемым файлом, а затем перемещает копию в каталог **bin**.

## <a name="to-add-an-application-configuration-file-to-a-c-project"></a>Добавление файла конфигурации приложения в проект C#

1. В строке меню выберите **Проект** > **Добавить новый элемент**.

     Откроется диалоговое окно **Добавление нового элемента**.

1. Разверните пункт **Установленные** > **Элементы Visual C#**, а затем выберите шаблон **Файл конфигурации приложения**.

1. В текстовом поле **Имя** введите имя и нажмите кнопку **Добавить**.

     Файл с именем *app.config* добавится в проект.

## <a name="see-also"></a>См. также

- [Управление параметрами приложения (.NET)](../ide/managing-application-settings-dotnet.md)
- [Схема файла конфигурации (.NET Framework)](/dotnet/framework/configure-apps/file-schema/index)
- [Настройка приложений .NET Framework](/dotnet/framework/configure-apps/index)