---
title: "Практическое руководство: Добавление зависимости пакета VSIX | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ссылки на пакет"
  - "Сборка пакета"
  - "DLL-файл пакета"
  - "ссылки VSIX"
ms.assetid: 8f20177b-dab9-43a3-b959-81a591b451d6
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Практическое руководство: Добавление зависимости пакета VSIX
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Можно настроить развертывание пакета VSIX, который устанавливает все зависимости, которых еще нет на конечном компьютере. Чтобы добиться этого, включают в файле source.extension.vsixmanifest зависимостей VSIX.  
  
#### Добавление зависимости  
  
1.  Откройте файл в source.extension.vsixmanifest **разработки** представления. Последовательно выберите пункты **зависимости** и нажмите кнопку **New**.  
  
2.  Чтобы добавить установленное расширение: в **добавления новых зависимостей** выберите **установлено расширение** и для **имя**, выберите расширение из списка.  
  
3.  Чтобы добавить другой VSIX, который не установлен:: в **добавления новых зависимостей** установите флажок **файл в файловой системе** а затем использовать **Обзор** кнопку, чтобы выбрать VSIX.  
  
## См. также  
 [Справочник по схеме 1.0 расширения VSIX](http://msdn.microsoft.com/ru-ru/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)   
 [Составляющие пакета VSIX](../extensibility/anatomy-of-a-vsix-package.md)   
 [Подготовка расширения для развертывания установщика Windows](../extensibility/preparing-extensions-for-windows-installer-deployment.md)