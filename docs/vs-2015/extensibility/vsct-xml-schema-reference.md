---
title: Справочник по XML-схеме VSCT | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- Visual Studio command table configuration files (VSCT), XML schema
- VSCT XML schema elements
ms.assetid: 49e7efae-e713-4762-a824-96fdaf92cdc9
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e56de828d3b357762da98cde3b9591033c6b5d19
ms.sourcegitcommit: fb8babf5cd72f1fc2f97ffe4ad7b62d91f325f61
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/07/2020
ms.locfileid: "90842781"
---
# <a name="vsct-xml-schema-reference"></a>Справочник по схемам XML VSCT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Предоставляет таблицу элементов схемы компилятора командной таблицы с допустимыми дочерними элементами и атрибутами для каждого из них.  
  
 Файл конфигурации таблицы команд на основе XML (. vsct) определяет элементы команды, предоставляемые пакетом VSPackage в интегрированной среде разработки (IDE). К таким элементам относятся пункты меню, меню, панели инструментов и поля со списком.  
  
> [!NOTE]
> Компилятор VSCT может запускать препроцессор в VSCT-файле. Так как это обычно препроцессор C++, можно определять включения и макросы с тем же синтаксисом, который используется в файлах C++. Примеры приведены в файле. vsct, который создается мастером **создания проектов** для проекта VSPackage.  
  
## <a name="optional-elements"></a>Необязательные элементы  
 Некоторые элементы VSCT являются необязательными. Если `Parent` аргумент не указан, Group_Undefined: 0 будет подразумеваемым. Если `Icon` аргумент не указан, гуидоффицеикон: мсотЦидноикон будет подразумеваемым. При определении сочетания клавиш Эмуляция, которая обычно не используется, является необязательной.  
  
 Элементы растрового изображения могут быть внедрены во время компиляции путем указания расположения полосы битовой карты в `href` аргументе. Панель растрового изображения копируется во время слияния, а не извлекается из ресурсов библиотеки DLL. При `href` указании аргумента `usedList` аргумент становится необязательным, и все слоты в полосе битовой карты считаются используемыми.  
  
 Все значения GUID и ID должны быть определены с помощью символьных имен. Эти имена могут быть определены в файлах заголовков или в \<Symbols> РАЗДЕЛАХ VSCT. Символьные имена должны быть локальными, включаемыми через \<Include> элементы или на которые ссылаются \<Extern> элементы. Символьное имя импортируется из файла заголовка, указанного в \<Extern> элементе, если он соответствует простому шаблону #define значение символа. Значение может быть другим символом, если этот символ был ранее определен. Определения GUID должны соответствовать формату OLE или C++. Значения ИДЕНТИФИКАТОРов могут быть десятичными или шестнадцатеричными цифрами, которым предшествует 0x, как показано в следующих строках:  
  
- {6D484634-E53D-4a2c-ADCB-55145C9362C8}  
  
- {0x6d484634, 0xe53d, 0x4a2c, {0xad, 0xcb, 0x55, 0x14, 0x5c, 0x93, 0x62, 0xc8}}  
  
  Можно использовать комментарии XML, но средства графического пользовательского интерфейса для приема-передачи могут отклонять их. Гарантируется, что содержимое \<Annotation> элементов будет поддерживаться независимо от формата.  
  
## <a name="schema-hierarchy"></a>Схема иерархии  
 Vsct-файл содержит следующие основные элементы.  
  
 [Элемент CommandTable](../extensibility/commandtable-element.md)  
  
 [Элемент Extern](../extensibility/extern-element.md)  
  
 [Включить элемент](../extensibility/include-element.md)  
  
 [Элемент Define](../extensibility/define-element.md)  
  
 [Commands, элемент](../extensibility/commands-element.md)  
  
 [Элемент CommandPlacements](../extensibility/commandplacements-element.md)  
  
 [Элемент VisibilityConstraints](../extensibility/visibilityconstraints-element.md)  
  
 [Элемент KeyBindings](../extensibility/keybindings-element.md)  
  
 [Элемент UsedCommands](../extensibility/usedcommands-element.md)  
  
 [Родительский элемент](../extensibility/parent-element.md)  
  
 [Элемент Icon](../extensibility/icon-element.md)  
  
 [Элемент Strings](../extensibility/strings-element.md)  
  
 [Элемент CommandFlag](../extensibility/command-flag-element.md)  
  
 [Элемент Symbols](../extensibility/symbols-element.md)  
  
 [Атрибуты Conditional](../extensibility/vsct-xml-schema-conditional-attributes.md)  
  
## <a name="see-also"></a>См. также:  
 [Как пакеты VSPackage добавляют элементы пользовательского интерфейса](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Маршрутизация команд в пакетах VSPackage](../extensibility/internals/command-routing-in-vspackages.md)
