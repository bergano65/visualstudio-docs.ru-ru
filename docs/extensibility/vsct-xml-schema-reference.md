---
title: "Справочник по схемам VSCT XML | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Таблица команд Visual Studio – файлы конфигурации (VSCT), XML-схемы"
  - "Элементы схемы VSCT XML"
ms.assetid: 49e7efae-e713-4762-a824-96fdaf92cdc9
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# Справочник по схемам VSCT XML
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Таблица элементов схемы таблицы компилятора командной разрешенных дочерних элементов и атрибутов для каждого.  
  
 Файл конфигурации \(.vsct\) таблицы команд на основе XML определяет элементы команды, которые предоставляет VSPackage интегрированную среду разработки \(IDE\). Эти элементы включают элементы меню, меню, панелей инструментов и поля со списком.  
  
> [!NOTE]
>  Компилятор VSCT можно запустить препроцессора в файл .vsct. Так как это обычно препроцессора, можно определить C\+\+ включает и макросы, имеющие тот же синтаксис, используемый в файлах C\+\+. В качестве примера приведены в .vsct файла, который **Новый проект** мастером для проекта VSPackage.  
  
## Необязательные элементы  
 Некоторые элементы VSCT являются необязательными. Если `Parent` аргумент не указан, будет неявно Group\_Undefined:0. Если `Icon` аргумент не указан, будет неявно guidOfficeIcon:msotcidNoIcon. При определении сочетания клавиш эмуляции, который обычно используется, является необязательным.  
  
 Элементы растрового изображения может быть внедрен во время компиляции, указав расположение панель изображений в `href` аргумент. Панель изображений скопирован во время слияния, а не извлекаются из библиотеки DLL ресурсов. Когда `href` указывать аргумент `usedList` становится необязательным аргументом, и всех областей в полосе точечного рисунка, считаются используется.  
  
 Все значения GUID и идентификатор должны быть определены с помощью символьные имена. Эти имена могут быть определены в файлах заголовков или в разделах VSCT \< символы \>. Символические имена должен быть локальным, добавленной с помощью элементов \< Include \> или ссылаться на элементы \< Extern \>. Символическое имя импортируется из файла заголовка, указываются в элементе \< Extern \>, если он соответствует простое шаблону \#define значение СИМВОЛА. Значение может быть другой символ, при условии, что этот символ определен ранее. Определения GUID должны иметь формат OLE или C\+\+. Идентификатор значения могут быть десятичные цифры или шестнадцатеричных цифр, которым предшествует 0 x, как показано в следующих строках:  
  
-   {6D484634\-E53D\-4a2c\-ADCB\-55145C9362C8}  
  
-   {0x6d484634, 0xe53d, 0x4a2c, {0xad, 0xcb, 0x55, 0x14, 0x5c, 0x93, 0x62, 0xc8}}  
  
 Комментарии XML может использоваться, но средства приема\-передачи графического пользовательского интерфейса \(GUI\) может отбросить их. Содержимое элементов \< Annotation \> гарантированно сохраняется вне зависимости от формата.  
  
## Схема иерархии  
 Файл .vsct имеет следующие основные элементы.  
  
 [Элемент CommandTable](../extensibility/commandtable-element.md)  
  
 [Внешний элемент](../extensibility/extern-element.md)  
  
 [Включить элемент](../extensibility/include-element.md)  
  
 [Определение элемента](../extensibility/define-element.md)  
  
 [Элемент Commands](../extensibility/commands-element.md)  
  
 [Элемент CommandPlacements](../extensibility/commandplacements-element.md)  
  
 [Элемент VisibilityConstraints](../extensibility/visibilityconstraints-element.md)  
  
 [Элемент привязки клавиш](../extensibility/keybindings-element.md)  
  
 [Элемент UsedCommands](../extensibility/usedcommands-element.md)  
  
 [Элемент Parent](../extensibility/parent-element.md)  
  
 [Значок элемента](../extensibility/icon-element.md)  
  
 [Элемент строки](../extensibility/strings-element.md)  
  
 [Элемент Command флаг](../extensibility/command-flag-element.md)  
  
 [Элемент символы](../extensibility/symbols-element.md)  
  
 [Условные атрибуты](../extensibility/vsct-xml-schema-conditional-attributes.md)  
  
## См. также  
 [Как добавить элементы пользовательского интерфейса в пакеты VSPackage](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Маршрутизация команд в пакеты VSPackage](../extensibility/internals/command-routing-in-vspackages.md)