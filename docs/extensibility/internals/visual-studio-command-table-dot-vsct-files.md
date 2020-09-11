---
title: Командная таблица Visual Studio (. Vsct) файлы | Документация Майкрософт
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
ms.openlocfilehash: 24ebac7aee2294d2ad8cee06cd88102bb8d3fd78
ms.sourcegitcommit: 4b29efeb3a5f05888422417c4ee236e07197fb94
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/11/2020
ms.locfileid: "90012351"
---
# <a name="visual-studio-command-table-vsct-files"></a>Файлы таблицы команд Visual Studio (VSCT-файлы)
Файл конфигурации командной таблицы — это текстовый файл, описывающий набор команд, содержащихся в VSPackage. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Компилятор командной таблицы (VSCT) компилирует файлы конфигурации на основе XML (VSCT-файлы) в двоичные файлы командных таблиц (. CTO). Результирующие CTO-файлы те же, что создаются с помощью компилятора командной таблицы (CTC) для компиляции файлов конфигурации CTC. Однако vsct-файлы на основе XML имеют некоторые преимущества, такие как редактор XML и IntelliSense XML.

 Дополнительные сведения о синтаксисе и семантике vsct-файлов см. в разделе [Разработка командной таблицы XML (. Vsct) файлы](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)

## <a name="in-this-section"></a>в этом разделе
 [Разработка файлов таблицы команд XML (VSCT-файлы)](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)

 Описывает, как проектировать файлы vsct.

 [Практическое руководство. Создание VSCT-файла](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)

 Сравнивает методы создания vsct-файла. Описывает процесс создания нового vsct-файла вручную.

## <a name="related-sections"></a>См. также
 [Справочник по схемам XML VSCT](../../extensibility/vsct-xml-schema-reference.md)

 Предоставляет сведения о каждом разделе XML-файла конфигурации в таблице команд.

 [Конфигурация таблицы команд (. CTC)](/previous-versions/bb165153(v=vs.100)) содержит общие сведения о нерекомендуемом формате файла CTC.

 [Как добавить элементы пользовательского интерфейса с помощью пакетов VSPackage](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

 Описывает спецификацию формата командной таблицы.

 [Ресурсы в пакетах VSPackage](../../extensibility/internals/resources-in-vspackages.md)

 Описывает, как использовать управляемые и неуправляемые ресурсы в управляемых пакетах VSPackage.

 [Команды, меню и панели инструментов](../../extensibility/internals/commands-menus-and-toolbars.md)

 Объясняется, как создать пользовательский интерфейс, включающий меню, панели инструментов и поля со списком команд.