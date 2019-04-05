---
title: Практическое руководство. Добавьте файл конфигурации приложения для C# проекта | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
dev_langs:
- CSharp
helpviewer_keywords:
- app.config files, adding to C# projects
ms.assetid: 9caf6bb0-c2fc-4ab6-ba69-bed3b880fbf8
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 481c1a66f3e025d3a29b2d5a1e39cd29bbb22490
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58990519"
---
# <a name="how-to-add-an-application-configuration-file-to-a-c-project"></a>Практическое руководство. Добавьте файл конфигурации приложения для C# проекта
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
 [Практическое руководство. Настройка приложения для целевой версии .NET Framework](http://msdn.microsoft.com/5247b307-89ca-417b-8dd0-e8f9bd2f4717)   
 [Использование среды разработки Visual Studio для C#](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md)