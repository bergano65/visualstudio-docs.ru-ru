---
title: Командный стол визуальной студии (. Vsct) Файлы Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, overview
- Visual Studio command table configuration files (VSCT), overview
ms.assetid: 1313adb4-add4-4e74-90e2-f4be522f5259
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d18367436d1ee1b889558a35723e4e3cec865945
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704027"
---
# <a name="visual-studio-command-table-vsct-files"></a>Файлы таблицы команд Visual Studio (VSCT-файлы)
Файл конфигурации командной таблицы — это текстовый файл, описывающий набор команд, содержащийся в VSPackage. Компилятор командной [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] таблицы (VSCT) компилирует файлы конфигурации на основе XML (.vsct- файлы) в двоичные выводные таблицы команд (.cto) файлы. Полученные файлы .cto такие же, как те, которые создаются с помощью компилятора командной таблицы (CTC) для компиляции файлов конфигурации .ctc. Тем не менее, XML-файлы на основе .vsct имеют некоторые преимущества, такие как редактор XML и XML IntelliSense.

 Подробнее о синтаксисе и семантике файлов .vsct можно узнать о таблице [командования XML (. Vsct) Файлы](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)

## <a name="in-this-section"></a>В этом разделе
 [Разработка файлов таблицы команд XML (VSCT-файлы)](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)

 Описывает, как проектировать файлы .vsct.

 [Практическое руководство. Создание VSCT-файла](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)

 Сравнивает методы создания файла .vsct. Описывает процесс ручного создания нового файла .vsct.

## <a name="related-sections"></a>Связанные разделы
 [Справочник по схемам XML VSCT](../../extensibility/vsct-xml-schema-reference.md)

 Предоставляет подробную информацию о каждом разделе файла конфигурации xML таблицы команды.

 [Конфигурация командной таблицы (. Ctc) Файлы](https://msdn.microsoft.com/library/3413dda1-f372-4669-bcf0-c64d3463842c) представляет обзор устаревшного формата файла .ctc.

 [Как добавить элементы пользовательского интерфейса с помощью пакетов VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

 Описывает спецификацию формата таблицы команд.

 [Ресурсы в пакетах VSPackage](../../extensibility/internals/resources-in-vspackages.md)

 Описывает, как использовать управляемые и неуправляемые ресурсы в управляемых VSPackages.

 [Команды, меню и панели инструментов](../../extensibility/internals/commands-menus-and-toolbars.md)

 Объясняется, как создать пользовательский интерфейс, включающий меню, панели инструментов и поля со списком команд.
