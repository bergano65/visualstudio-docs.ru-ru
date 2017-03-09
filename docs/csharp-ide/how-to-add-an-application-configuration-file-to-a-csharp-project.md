---
title: "Практическое руководство. Добавление файла конфигурации приложения в проект C# | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "файлы app.config, добавление в проекты C#"
ms.assetid: 9caf6bb0-c2fc-4ab6-ba69-bed3b880fbf8
caps.latest.revision: 20
caps.handback.revision: 20
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Практическое руководство. Добавление файла конфигурации приложения в проект C# #
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Путем добавления файла конфигурации приложения \(app.config\) файла в проект C\-\#, можно настраивать как среда CLR находит и загружает файлы сборки.  Дополнительные сведения о файлах конфигурации приложения см. в разделе [Обнаружение сборок в среде выполнения](../Topic/How%20the%20Runtime%20Locates%20Assemblies.md).  
  
> [!NOTE]
>  Магазин Windows не поддерживает <xref:System.Configuration>.  В результате приложения хранилища не содержат шаблон файла.  
  
 При построении проекта среда разработки автоматически копирует файл файла, изменяет имя файла копии для сопоставления в исполняемый файл, а затем скопировать перемещается в каталог bin.  
  
### Чтобы добавить файл конфигурации приложения в проект C\#  
  
1.  В строке меню выберите **Проект**, **Добавление нового элемента**.  
  
     Открывается диалоговое окно **Добавление нового элемента**.  
  
2.  Разверните узлы **Установлено** и **Элементы Visual C\#**, а затем выберите шаблон **Файл конфигурации приложения**.  
  
3.  В текстовом поле **Имя** введите имя, а затем нажмите кнопку **Добавить**.  
  
     Файл с именем файла будет добавлен в проект.  
  
## См. также  
 [Управление параметрами приложения \(.NET\)](../ide/managing-application-settings-dotnet.md)   
 [Схема файла конфигурации](../Topic/Configuration%20File%20Schema%20for%20the%20.NET%20Framework.md)   
 [Настройка приложений](../Topic/Configuring%20Apps%20by%20using%20Configuration%20Files.md)   
 [How to: Configure an App to Target a .NET Framework Version](http://msdn.microsoft.com/ru-ru/5247b307-89ca-417b-8dd0-e8f9bd2f4717)   
 [Использование среды разработки Visual C\#](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md)