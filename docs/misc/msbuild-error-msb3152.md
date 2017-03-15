---
title: "Ошибка MSBuild MSB3152 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateBootstrapper.PackageFileNotFound"
helpviewer_keywords: 
  - "MSB3152"
ms.assetid: 5a3859d4-4107-4e46-bb42-04de92b551de
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Ошибка MSBuild MSB3152
**MSB3152: для места установки для необходимых компонентов не выбрано значение "веб\-узел производителя" и файл "\<файл\>" элемента "\<пакет\>" не найден на диске.  Дополнительные сведения см. в справке.**  
  
 Эта ошибка появляется, когда отсутствует файл, который требуется необходимому установщику.  Файлы установщика сохраняются в особой папке, зарезервированной Visual Studio для распространяемых пакетов.  Расположение этой папки зависит от версии Visual Studio, с помощью которой выполняется разработка.  Дополнительные сведения о расположении этой особой папки см. в разделе [Создание пакетов загрузчика](../deployment/creating-bootstrapper-packages.md).  
  
### Чтобы исправить эту ошибку  
  
-   Определите, существует ли файл на диске.  
  
-   Попытайтесь разрешить проблему с пакетом с помощью HomeSite.  
  
-   В файле проекта задайте для атрибута `CopyComponents` значение `false`.  
  
-   Не используйте поврежденный пакет загрузчика.  
  
## См. также  
 [Создание пакетов загрузчика](../deployment/creating-bootstrapper-packages.md)