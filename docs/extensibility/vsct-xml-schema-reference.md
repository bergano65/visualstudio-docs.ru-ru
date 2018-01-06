---
title: "Справочник по схеме VSCT XML | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio command table configuration files (VSCT), XML schema
- VSCT XML schema elements
ms.assetid: 49e7efae-e713-4762-a824-96fdaf92cdc9
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e02d4ad31a4877dd88dca941c06e38f7eeac82f7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="vsct-xml-schema-reference"></a>Справочник по схеме VSCT XML
Таблица элементов схемы компилятора таблицы команд с разрешенные дочерние элементы и атрибуты для каждого.  
  
 Файл конфигурации (.vsct) таблицы команд на основе XML определяет элементы команды, которые VSPackage предоставляет интегрированную среду разработки (IDE). Эти элементы включают элементы меню, меню, панелей инструментов и поля со списком.  
  
> [!NOTE]
>  Компилятор VSCT можно запускать препроцессора в vsct-файле. Так как это обычно включает C++ препроцессора, можно определить и макросы, имеющие тот же синтаксис, используемый в файлах C++. В качестве примера приведены в vsct-файлом, файл **новый проект** мастером для проекта VSPackage.  
  
## <a name="optional-elements"></a>Необязательные элементы  
 Некоторые элементы VSCT являются необязательными. Если `Parent` аргумент не указан, будет подразумеваемых Group_Undefined:0. Если `Icon` аргумент не указан, будет подразумеваемых guidOfficeIcon:msotcidNoIcon. При определении сочетания клавиш эмуляции, который обычно используется, является необязательным.  
  
 Элементы растрового изображения может быть внедрен во время компиляции, указав расположение полосы точечный рисунок в `href` аргумент. Растрового изображения полосковой скопированные в процессе слияния, а не извлекаются из ресурсов библиотеки DLL. Когда `href` аргумент задан, `usedList` аргумент становится необязательным, и все слоты в полосе растрового изображения, считаются используется.  
  
 Все значения GUID и ID должны быть определены с помощью символьные имена. Эти имена могут быть определены в файлах заголовков или в VSCT \<символы > разделов. Символические имена должны быть локальным, добавленной с помощью \<Include > элементов, или ссылается \<Extern > элементов. Символическое имя импортируется из файла заголовка, указанного в \<Extern > элемент за простой шаблон #define значение СИМВОЛА. Значение может быть другим символом при условии, что ранее был определен этот символ. Определения GUID должна иметь формат OLE или C++. Значения Идентификаторов может быть десятичные цифры или шестнадцатеричных цифр, которые начинаются с 0 x, как показано в следующих строках:  
  
-   {6D484634-E53D-4a2c-ADCB-55145C9362C8}  
  
-   {0x6d484634, 0xe53d, 0x4a2c, {0xad, 0xcb, 0x55, 0x14, 0x5c, 0x93, 0x62, 0xc8}}  
  
 Комментарии XML может использоваться, но средства приема-передачи графического пользовательского интерфейса (GUI) может отбросить их. Содержимое \<заметки > элементы гарантированно сохраняется независимо от формата.  
  
## <a name="schema-hierarchy"></a>Схема иерархии  
 Vsct-файл имеет следующие основные элементы.  
  
 [Элемент CommandTable](../extensibility/commandtable-element.md)  
  
 [Элемент Extern](../extensibility/extern-element.md)  
  
 [Элемент Include](../extensibility/include-element.md)  
  
 [Элемент Define](../extensibility/define-element.md)  
  
 [Элемент Commands](../extensibility/commands-element.md)  
  
 [Элемент CommandPlacements](../extensibility/commandplacements-element.md)  
  
 [Элемент VisibilityConstraints](../extensibility/visibilityconstraints-element.md)  
  
 [Элемент KeyBindings](../extensibility/keybindings-element.md)  
  
 [Элемент UsedCommands](../extensibility/usedcommands-element.md)  
  
 [Элемент Parent](../extensibility/parent-element.md)  
  
 [Элемент Icon](../extensibility/icon-element.md)  
  
 [Элемент Strings](../extensibility/strings-element.md)  
  
 [Элемент CommandFlag](../extensibility/command-flag-element.md)  
  
 [Элемент Symbols](../extensibility/symbols-element.md)  
  
 [Условные атрибуты](../extensibility/vsct-xml-schema-conditional-attributes.md)  
  
## <a name="see-also"></a>См. также  
 [Как добавить элементы пользовательского интерфейса в пакеты VSPackage](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Маршрутизация команд в пакетах VSPackage](../extensibility/internals/command-routing-in-vspackages.md)