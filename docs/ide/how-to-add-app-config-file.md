---
title: Добавление к проекту файла app.config
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
helpviewer_keywords:
- app.config files, adding to C# projects
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 3eb813dc5d4389b002851a904d61219b0d5c316e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593646"
---
# <a name="how-to-add-an-application-configuration-file-to-a-c-project"></a>Практическое руководство. Добавление файла конфигурации приложения в проект C#

Добавив файл конфигурации приложения (файл *app.config*) в проект C#, вы можете настроить способ, которым общеязыковая среда выполнения будет находить и загружать файлы сборки. Дополнительные сведения о файлах конфигурации приложения см. в статье [Обнаружение сборок в среде выполнения (.NET Framework)](/dotnet/framework/deployment/how-the-runtime-locates-assemblies).

> [!NOTE]
> Приложения UWP не содержат файл *app.config*.

При сборке проекта среда разработки автоматически копирует файл *app.config*, изменяет имя копии файла в соответствии с исполняемым файлом, а затем перемещает копию в каталог **bin**.

## <a name="to-add-an-application-configuration-file-to-a-c-project"></a>Добавление файла конфигурации приложения в проект C#

1. В строке меню выберите **Проект** > **Добавить новый элемент**.

     Откроется диалоговое окно **Добавление нового элемента**.

1. Разверните пункт **Установленные** > **Элементы Visual C#** , а затем выберите шаблон **Файл конфигурации приложения**.

1. В текстовом поле **Имя** введите имя и нажмите кнопку **Добавить**.

     Файл с именем *app.config* добавится в проект.

## <a name="see-also"></a>См. также раздел

- [Управление параметрами приложения (.NET)](../ide/managing-application-settings-dotnet.md)
- [Схема файла конфигурации (.NET Framework)](/dotnet/framework/configure-apps/file-schema/index)
- [Настройка приложений .NET Framework](/dotnet/framework/configure-apps/index)
