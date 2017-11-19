---
title: "Способ: добавить файл конфигурации приложения в проект C# | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: CSharp
helpviewer_keywords: app.config files, adding to C# projects
ms.assetid: 9caf6bb0-c2fc-4ab6-ba69-bed3b880fbf8
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 097e7a2eac78fe85b2a3ab62d5cdf1fd18908d56
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-add-an-application-configuration-file-to-a-c-project"></a>Практическое руководство. Добавление файла конфигурации приложения в проект C#
Добавление файла конфигурации приложения (файл app.config) в проект C#, можно настроить как общеязыковая среда выполнения находит и загружает файлы сборки. Дополнительные сведения о файлах конфигурации см. в разделе [как среда выполнения находит сборки](/dotnet/framework/deployment/how-the-runtime-locates-assemblies).  
  
> [!NOTE]
>  Приложения UWP не содержится шаблон app.config.
  
 При построении проекта среда разработки автоматически копирует файл app.config, изменяет имя файла копии в соответствии исполняемый файл и затем перемещает ее в папку bin.  
  
### <a name="to-add-an-application-configuration-file-to-your-c-project"></a>Чтобы добавить файл конфигурации приложения в проект C#  
  
1.  В строке меню выберите **проекта**, **Добавление нового элемента**.  
  
     Откроется диалоговое окно **Добавление нового элемента**.  
  
2.  Разверните **установленные**, разверните **элементы Visual C#**и нажмите кнопку **файла конфигурации приложения** шаблона.  
  
3.  В **имя** текстовом поле введите имя и выберите **добавить** кнопки.  
  
     В проект добавляется файл с именем app.config.  
  
## <a name="see-also"></a>См. также  
 [Управление параметрами приложения (.NET)](../ide/managing-application-settings-dotnet.md)   
 [Схема файлов конфигурации для .NET Framework](/dotnet/framework/configure-apps/file-schema/index)   
 [Настройка приложений](/dotnet/framework/configure-apps/index)   
 [Как: настройте приложение для целевой версии .NET Framework](http://msdn.microsoft.com/en-us/5247b307-89ca-417b-8dd0-e8f9bd2f4717)   
 [Использование среды разработки Visual Studio для C#](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md)