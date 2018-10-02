---
title: 'Способ: добавить файл конфигурации приложения в проект C# | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- app.config files, adding to C# projects
ms.assetid: 9caf6bb0-c2fc-4ab6-ba69-bed3b880fbf8
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 29386381679c02d3f4c7772e79f1da4a64705e3a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47569060"
---
# <a name="how-to-add-an-application-configuration-file-to-a-c-project"></a>Практическое руководство. Добавление файла конфигурации приложения в проект C#
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Добавив файл конфигурации приложения (файл app.config) в проект C#, вы можете настроить способ, которым общеязыковая среда выполнения будет находить и загружать файлы сборки. Дополнительные сведения о файлах конфигурации см. в разделе [Обнаружение сборок в среде выполнения](http://msdn.microsoft.com/library/772ac6f4-64d2-4cfb-92fd-58096dcd6c34).  
  
> [!NOTE]
>  Не поддерживает Windows Store <xref:System.Configuration>. В результате приложения Store не содержат шаблон app.config.  
  
 При построении проекта среда разработки автоматически копирует файл app.config, изменяет имя файла копии в соответствии с исполняемым файлом и затем перемещает копию в каталог bin.  
  
### <a name="to-add-an-application-configuration-file-to-your-c-project"></a>Чтобы добавить файл конфигурации приложения в проект C#  
  
1.  В строке меню выберите **проекта**, **Добавление нового элемента**.  
  
     Откроется диалоговое окно **Добавление нового элемента**.  
  
2.  Разверните **установленные**, разверните **элементы Visual C#**, а затем выберите **файла конфигурации приложения** шаблона.  
  
3.  В текстовом поле **Имя** введите имя и нажмите кнопку **Добавить**.  
  
     В проект добавляется файл с именем app.config.  
  
## <a name="see-also"></a>См. также  
 [Управление параметрами приложения (.NET)](../ide/managing-application-settings-dotnet.md)   
 [Схема файлов конфигурации для .NET Framework](http://msdn.microsoft.com/library/69003d39-dc8a-460c-a6be-e6d93e690b38)   
 [Настройка приложений](http://msdn.microsoft.com/library/86bd26d3-737e-4484-9782-19b17f34cd1f)   
 [Практическое: Настройка приложения для целевой версии .NET Framework](http://msdn.microsoft.com/en-us/5247b307-89ca-417b-8dd0-e8f9bd2f4717)   
 [Использование среды разработки Visual Studio для C#](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md)