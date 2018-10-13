---
title: Visual Studio Command Table (. Файлы Vsct) | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSCT files, overview
- Visual Studio command table configuration files (VSCT), overview
ms.assetid: 1313adb4-add4-4e74-90e2-f4be522f5259
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4bac7d9ce3c4fc0af02366f1b325faf6412759cc
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49268963"
---
# <a name="visual-studio-command-table-vsct-files"></a>Файлы таблицы команд Visual Studio (VSCT-файлы)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Файл конфигурации таблицы команды — это текстовый файл, описывающий набор команд, которые содержит пакет VSPackage. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Команда компилятора таблицы (VSCT) компилирует файлы конфигурации на основе XML (vsct-файлов) в файлы вывода (.cto) таблицы команда binary. Итоговый .cto файлы, которые создаются с помощью компилятора команды (CTC) таблицы для компиляции файлов конфигурации .ctc одинаковы. Тем не менее файлы vstc на основе XML имеет некоторые преимущества, такие как редактор XML и XML IntelliSense.  
  
 Дополнительные сведения о синтаксисе и семантике vsct-файлы, см. в разделе [проектирование таблицы команд XML (. Файлы Vsct)](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)  
  
## <a name="in-this-section"></a>В этом разделе  
 [Разработка файлов таблицы команд XML (VSCT-файлы)](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)  
 Содержит инструкции по определению vsct-файлы.  
  
 [Практическое руководство. Создание VSCT-файла](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)  
 Сравнение методов для создания vsct-файл. Описание процесса создания нового vsct-файл вручную.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Справочник по схемам XML VSCT](../../extensibility/vsct-xml-schema-reference.md)  
 Подробное описание каждого раздела файла конфигурации XML таблицы команд.  
  
 [Конфигурации таблицы команды (. Файлах ctc)](http://msdn.microsoft.com/en-us/3413dda1-f372-4669-bcf0-c64d3463842c)  
 Представляет обзор устаревшие .ctc формата файла.  
  
 [Как добавить элементы пользовательского интерфейса с помощью пакетов VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 Описывает спецификации формата таблицы команд.  
  
 [Ресурсы в пакетах VSPackage](../../extensibility/internals/resources-in-vspackages.md)  
 В этой статье описывается использование управляемых и неуправляемых ресурсов в управляемые пакеты VSPackage.  
  
 [Команды, меню и панели инструментов](../../extensibility/internals/commands-menus-and-toolbars.md)  
 Объясняется, как создать пользовательский интерфейс, включающий меню, панели инструментов и поля со списком команд.

