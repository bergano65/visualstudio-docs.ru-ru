---
title: "Практическое руководство. Создание пакета решения SharePoint с помощью задач MSBuild | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "разработка приложений SharePoint в Visual Studio, пакеты"
ms.assetid: c3880bdd-f0a1-4d53-9a97-5767cb3f7b8e
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# Практическое руководство. Создание пакета решения SharePoint с помощью задач MSBuild
  Построение, очистку и проверку пакетов SharePoint \(WSP\-файлов\) можно выполнять с помощью задач командной строки MSBuild на компьютере разработчика.  Эти команды также позволяют автоматизировать процесс построения с помощью Team Foundation Server или компьютера построения.  
  
## Построение пакета SharePoint  
  
#### Построение пакета SharePoint  
  
1.  В меню **Старт** Windows, выберите **Все программы**, **Периферийные устройства**, **Окно командной строки**.  
  
2.  Перейдите в каталог, где находится проект SharePoint.  
  
3.  Чтобы создать пакет для проекта, введите следующую команду.  Замените *ProjectFileName* именем проекта.  
  
    ```  
    msbuild /t:Package ProjectFileName  
    ```  
  
     Например, создать пакет проекта SharePoint с именем ListDefinition1 можно с помощью любой из следующих команд.  
  
    ```  
    msbuild /t:Package ListDefinition1.vbproj  
    msbuild /t:Package ListDefinition1.csproj  
    ```  
  
## Очистка пакета SharePoint  
  
#### Очистка пакета SharePoint  
  
1.  Откройте окно командной строки.  
  
2.  Перейдите в каталог, где находится проект SharePoint.  
  
3.  Чтобы очистить пакет для проекта, введите следующую команду.  Замените *ProjectFileName* именем проекта.  
  
    ```  
    msbuild /t:CleanPackage ProjectFileName  
    ```  
  
     Например, очистить проект SharePoint с именем ListDefinition1 можно с помощью любой из следующих команд.  
  
    ```  
    msbuild /t:CleanPackage ListDefinition1.vbproj  
    msbuild /t:CleanPackage ListDefinition1.csproj  
    ```  
  
## Проверка пакета SharePoint  
  
#### Проверка пакета SharePoint  
  
1.  Откройте окно командной строки.  
  
2.  Перейдите в каталог, где находится проект SharePoint.  
  
3.  Чтобы проверить пакет для проекта, введите следующую команду.  Замените *ProjectFileName* именем проекта.  
  
    ```  
    msbuild /t:ValidatePackage ProjectFileName  
    ```  
  
     Например, проверить проект SharePoint с именем ListDefinition1 можно с помощью любой из следующих команд.  
  
    ```  
    msbuild /t:ValidatePackage ListDefinition1.vbproj  
    msbuild /t:ValidatePackage ListDefinition1.csproj  
    ```  
  
## Настройка свойств пакета SharePoint  
  
#### Настройка свойств пакета SharePoint  
  
1.  Откройте окно командной строки.  
  
2.  Перейдите в каталог, где находится проект SharePoint.  
  
3.  Чтобы задать свойство в пакете проекта, введите следующую команду.  Замените *PropertyName* именем свойства, которое требуется задать.  
  
    ```  
    msbuild /property:PropertyName=Value  
    ```  
  
     Например, задать порог предупреждений можно с помощью любой из следующих команд.  
  
    ```  
    msbuild /property:WarningLevel = 2  
    ```  
  
## См. также  
 [Создание компонентов SharePoint](../sharepoint/creating-sharepoint-features.md)   
 [Практическое руководство. Настройка компонента SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [Практическое руководство. Добавление и удаление элементов в компонентах SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)  
  
  