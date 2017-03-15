---
title: "Таблицы команд Visual Studio (. Файлы Vsct) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Файлы VSCT, общие сведения"
  - "Таблица команд Visual Studio – файлы конфигурации (VSCT), общие сведения"
ms.assetid: 1313adb4-add4-4e74-90e2-f4be522f5259
caps.latest.revision: 22
caps.handback.revision: 22
ms.author: "gregvanl"
manager: "ghogen"
---
# Таблицы команд Visual Studio (. Файлы Vsct)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Файл конфигурации команды таблицы — текстовый файл, описывающий набор команд, содержащих VSPackage.[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Команда компилятора таблицы \(VSCT\) компилирует файлы конфигурации на основе XML \(vsct\-файлы\) в файлы вывода \(.cto\) таблицы двоичная команда. Результирующий .cto файлы, которые создаются с помощью компилятора командной таблицы \(CTC\) для компиляции файлов конфигурации .ctc одинаковы. Однако файлы .vsct на основе XML имеет некоторые преимущества, такие как редактор XML и XML IntelliSense.  
  
 Дополнительные сведения о синтаксисе и семантика vsct\-файлах см. [Разработка таблицы команд XML \(. Файлы Vsct\)](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)  
  
## В этом подразделе  
 [Разработка таблицы команд XML \(. Файлы Vsct\)](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)  
 Инструкции по разработке vsct\-файлы.  
  
 [Практическое руководство: создание. Файл Vsct](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)  
 Сравнение методов для создания файла .vsct. Описание процесса создания нового файла .vsct вручную.  
  
## Связанные подразделы  
 [Справочник по схемам VSCT XML](../../extensibility/vsct-xml-schema-reference.md)  
 Подробное описание каждого раздела команду таблицы XML\-файл конфигурации.  
  
 [Command Table Configuration \(.Ctc\) Files](http://msdn.microsoft.com/ru-ru/3413dda1-f372-4669-bcf0-c64d3463842c)  
 Представляет обзор формата файла .ctc не рекомендуется.  
  
 [Как добавить элементы пользовательского интерфейса в пакеты VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 Описывает спецификации формата команды таблицы.  
  
 [Ресурсы в пакеты VSPackage](../../extensibility/internals/resources-in-vspackages.md)  
 Описывает способы использования управляемых и неуправляемых ресурсов в управляемых пакетов VSPackages.  
  
 [Команды, меню и панелей инструментов](../../extensibility/internals/commands-menus-and-toolbars.md)  
 Объясняется, как создать пользовательский Интерфейс, который включает меню, панелей инструментов и команд со списком.