---
title: Справочник по схемам VSCT XML | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio command table configuration files (VSCT), XML schema
- VSCT XML schema elements
ms.assetid: 49e7efae-e713-4762-a824-96fdaf92cdc9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ce5ebac402603a8d26908ea1cd67468bbefea1c8
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53943081"
---
# <a name="vsct-xml-schema-reference"></a>Справочник по схемам VSCT XML
Таблица элементов схемы компилятора таблицы команд, с допустимые дочерние элементы и атрибуты для каждого.  
  
 Файл конфигурации (.vsct) таблицы команд на основе XML определяет командных элементов, предоставляемых VSPackage интегрированной среде разработки (IDE). Эти элементы включают элементы меню, меню, панелей инструментов и поля со списком.  
  
> [!NOTE]
>  Компилятора VSCT можно запустить препроцессора в vsct-файле. Так как это обычно включает препроцессора, можно определить C++ и макросы, имеющие тот же синтаксис, который используется в файлах C++. В качестве примера приведены в vsct-файлом, файл **новый проект** мастер создает для проекта VSPackage.  
  
## <a name="optional-elements"></a>Необязательные элементы  
 Некоторые элементы VSCT являются необязательными. Если `Parent` аргумент не задан, будет неявно Group_Undefined:0. Если `Icon` аргумент не задан, будет неявно guidOfficeIcon:msotcidNoIcon. При определении сочетания клавиш эмуляция, который обычно используется, является необязательным.  
  
 Элементы точечного рисунка могут быть внедренными во время компиляции, указав расположение набора точечных рисунков в `href` аргумент. Наборе точечных рисунков скопированные в процессе слияния, а не извлекаются из библиотеки DLL ресурсов. Когда `href` аргумент указан, `usedList` становится необязательным аргументом, и все слоты в наборе точечных рисунков, считаются используется.  
  
 Все значения GUID и ID должен быть определен с помощью символьные имена. Эти имена могут быть определены в файлах заголовков или в VSCT \<символы > разделах. Символические имена должны быть локальным, добавленной с помощью \<Include > элементов, или ссылается \<Extern > элементы. Символическое имя импортируется из файла заголовка, заданного в \<Extern > элемент за простой шаблон #define значения СИМВОЛА. Значение может быть другой символ, до тех пор, пока этот символ был определен ранее. Идентификатор GUID определения важно следовать формат C++ или OLE. Идентификатор значения могут быть десятичные цифры или шестнадцатеричных цифр, которым предшествует 0 x, как показано в следующих строках:  
  
- {6D484634-E53D-4a2c-ADCB-55145C9362C8}  
  
- {0x6d484634, 0xe53d, 0x4a2c, {0xad, 0xcb, 0x55, 0x14, 0x5c, 0x93, 0x62, 0xc8}}  
  
  Комментарии XML может использоваться, но их может привести к сбросу средства приема-передачи графического пользовательского интерфейса (GUI). Содержимое \<заметки > элементы гарантированно сохраняется вне зависимости от формата.  
  
## <a name="schema-hierarchy"></a>Иерархия схемы  
 Vsct-файл имеет следующие основные элементы.  
  
 [Элемент CommandTable](../extensibility/commandtable-element.md)  
  
 [Элемент extern](../extensibility/extern-element.md)  
  
 [Включить элемент](../extensibility/include-element.md)  
  
 [Определение элемента](../extensibility/define-element.md)  
  
 [Элемент Commands](../extensibility/commands-element.md)  
  
 [Элемент CommandPlacements](../extensibility/commandplacements-element.md)  
  
 [Элемент VisibilityConstraints](../extensibility/visibilityconstraints-element.md)  
  
 [Элемент KeyBindings](../extensibility/keybindings-element.md)  
  
 [Элемент UsedCommands](../extensibility/usedcommands-element.md)  
  
 [Родительский элемент](../extensibility/parent-element.md)  
  
 [Элемент Icon](../extensibility/icon-element.md)  
  
 [Элемент strings](../extensibility/strings-element.md)  
  
 [Элемент Commandflag](../extensibility/command-flag-element.md)  
  
 [Элемент Symbols](../extensibility/symbols-element.md)  
  
 [Условные атрибуты](../extensibility/vsct-xml-schema-conditional-attributes.md)  
  
## <a name="see-also"></a>См. также  
 [Как добавить элементы пользовательского интерфейса в пакеты VSPackage](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Маршрутизация команд в пакеты VSPackage](../extensibility/internals/command-routing-in-vspackages.md)