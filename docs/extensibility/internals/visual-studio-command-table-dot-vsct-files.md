---
title: "Таблицы команд Visual Studio (. Файлы Vsct) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSCT files, overview
- Visual Studio command table configuration files (VSCT), overview
ms.assetid: 1313adb4-add4-4e74-90e2-f4be522f5259
caps.latest.revision: "22"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 71a202bdb71469e4d6b46eb537147092b1ea9013
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="visual-studio-command-table-vsct-files"></a>Таблицы команд Visual Studio (. Файлы Vsct)
Таблица конфигурации командный файл является файлом, описывающую набор команд, которые содержит пакет VSPackage. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Команда компилятора таблицы (VSCT) компилирует файлы конфигурации на основе XML (vsct-файлами) в файлы вывода (.cto) таблицу команда binary. Итоговый .cto файлы, которые создаются с помощью компилятора таблицы (CTC) команды для компиляции файлов конфигурации .ctc одинаковы. Однако файлы vstc на основе XML имеет некоторые преимущества, например редактора XML и XML IntelliSense.  
  
 Дополнительные сведения о синтаксисе и семантика vsct-файлами см. в разделе [проектирование таблицы команд XML (. Файлы Vsct)](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)  
  
## <a name="in-this-section"></a>В этом разделе  
 [Разработка файлов таблицы команд XML (VSCT-файлы)](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)  
 Содержит описание проектирования vsct-файлами.  
  
 [Практическое руководство. Создание VSCT-файла](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)  
 Сравнение методов для создания vsct-файл. Описание процесса создания нового vsct-файл вручную.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Справочник по схемам XML VSCT](../../extensibility/vsct-xml-schema-reference.md)  
 Предоставляет подробные сведения о каждой части команды таблицы XML-файл конфигурации.  
  
 [Команда конфигурации таблиц (. Файлы ctc)](http://msdn.microsoft.com/en-us/3413dda1-f372-4669-bcf0-c64d3463842c)  
 Представляет обзор устаревшие .ctc формата файла.  
  
 [Как добавить элементы пользовательского интерфейса с помощью пакетов VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 Описывает спецификации формата таблицы команд.  
  
 [Ресурсы в пакетах VSPackage](../../extensibility/internals/resources-in-vspackages.md)  
 Описывает, как использовать управляемые и неуправляемые ресурсы в управляемые пакеты VSPackage.  
  
 [Команды, меню и панели инструментов](../../extensibility/internals/commands-menus-and-toolbars.md)  
 Объясняется, как создать пользовательский интерфейс, включающий меню, панели инструментов и поля со списком команд.