---
title: Командная таблица Visual Studio (. Vsct) файлы | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, overview
- Visual Studio command table configuration files (VSCT), overview
ms.assetid: 1313adb4-add4-4e74-90e2-f4be522f5259
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cde3b86e19788c41df6e8f1c79a6bf829f491170
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65675249"
---
# <a name="visual-studio-command-table-vsct-files"></a>Файлы таблицы команд Visual Studio (VSCT-файлы)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Файл конфигурации командной таблицы — это текстовый файл, описывающий набор команд, содержащихся в VSPackage. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]Компилятор командной таблицы (VSCT) компилирует файлы конфигурации на основе XML (VSCT-файлы) в двоичные файлы командных таблиц (. CTO). Результирующие CTO-файлы те же, что создаются с помощью компилятора командной таблицы (CTC) для компиляции файлов конфигурации CTC. Однако vsct-файлы на основе XML имеют некоторые преимущества, такие как редактор XML и IntelliSense XML.  
  
 Дополнительные сведения о синтаксисе и семантике vsct-файлов см. в разделе [Разработка командной таблицы XML (. Vsct) файлы](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)  
  
## <a name="in-this-section"></a>в этом разделе  
 [Разработка файлов таблицы команд XML (VSCT-файлы)](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)  
 Описывает, как проектировать файлы vsct.  
  
 [Практическое руководство. Создание VSCT-файла](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)  
 Сравнивает методы создания vsct-файла. Описывает процесс создания нового vsct-файла вручную.  
  
## <a name="related-sections"></a>См. также  
 [Справочник по схемам XML VSCT](../../extensibility/vsct-xml-schema-reference.md)  
 Предоставляет сведения о каждом разделе XML-файла конфигурации в таблице команд.  
  
 [Конфигурация таблицы команд (. CTC) файлы](https://msdn.microsoft.com/3413dda1-f372-4669-bcf0-c64d3463842c)  
 Содержит обзор нерекомендуемого формата файла CTC.  
  
 [Как добавить элементы пользовательского интерфейса с помощью пакетов VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 Описывает спецификацию формата командной таблицы.  
  
 [Ресурсы в пакетах VSPackage](../../extensibility/internals/resources-in-vspackages.md)  
 Описывает, как использовать управляемые и неуправляемые ресурсы в управляемых пакетах VSPackage.  
  
 [Команды, меню и панели инструментов](../../extensibility/internals/commands-menus-and-toolbars.md)  
 Объясняется, как создать пользовательский интерфейс, включающий меню, панели инструментов и поля со списком команд.
