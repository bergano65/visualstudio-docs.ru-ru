---
title: "Ошибка MSBuild MSB3172 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateManifest.ReadInputManifestFailed"
helpviewer_keywords: 
  - "MSB3172"
ms.assetid: aa7291db-1f36-41e7-a510-90cd4daaa89d
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Ошибка MSBuild MSB3172
**MSB3172: не удается прочесть манифест "\<файл\>". '  "\<ошибка\>"**  
  
 Эта ошибка появляется, если в процессе построения обнаружена общая проблема при чтении файла манифеста.  В сообщении об ошибке указывается имя файла и более подробные сведения о проблеме.  
  
 Возможно, файл сборки или манифеста был добавлен как файл содержимого.  Чтобы создать правильную ссылку на сборку в системе проектов, необходимо использовать команду **Добавить ссылку** вместо команды **Добавить файл**.  В более сложных проектах в качестве файла проекта часто помечается файл .exe.manifest в папке bin, но этого следует избегать.  Скрытый файл app.manifest становится файлом .exe.manifest, и его можно изменять вручную для развернутых сценариев.  
  
## См. также  
 [Элемент \<PackageFiles\>](../deployment/packagefiles-element-bootstrapper.md)