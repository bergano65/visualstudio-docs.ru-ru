---
title: VSCT XML Схема Справка (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio command table configuration files (VSCT), XML schema
- VSCT XML schema elements
ms.assetid: 49e7efae-e713-4762-a824-96fdaf92cdc9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 923a0c4b64fcae3a409a2298d6d481f6e1bb14db
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697902"
---
# <a name="vsct-xml-schema-reference"></a>Ссылка на схему VSCT XML
Предоставляет таблицу элементов схемы таблицы командного состава с допустимыми элементами и атрибутами для каждого из них.

 Конфигурация таблицы команднаxml на основе XML (.vsct) определяет элементы команды, которые VSPackage предоставляет интегрированной среде разработки (IDE). Эти элементы включают в себя пункты меню, меню, панели инструментов и комбо-коробки.

> [!NOTE]
> Компилятор VSCT может запускать препроцессор в файле .vsct. Поскольку это, как правило, препроцессор СЗ, можно определить, включает в себя и макросы, которые имеют тот же синтаксис, который используется в файлах СЗ. Примеры этого приведены в файле .vsct, который мастер **нового проекта** создает для проекта VSPackage.

## <a name="optional-elements"></a>Дополнительные элементы
 Некоторые элементы VSCT не являются обязательными. Если `Parent` аргумент не указан, Group_Undefined:0 будет подразумеваться. Если `Icon` аргумент не указан, подразумевается guidOfficeIcon:msotcidNoIcon. Когда определяется ключ ярлыка, эмуляция, которая обычно не используется, является необязательной.

 Элементы Bitmap могут быть встроены во время компиляции, указав местоположение полосы биткарты в аргументе. `href` Полоса битной карты копируется во время слияния, а не извлекается из ресурсов DLL. При `href` наличии `usedList` аргумента аргумент становится необязательным, и все слоты в полосе bitmap считаются использованными.

 Все значения GUID и ID должны быть определены с помощью символических имен. Эти имена могут быть определены в \<файлах заголовка или в разделах VSCT Symbols>. Символические названия должны быть \<локальными, включаться \<через элементы «Включить>» или ссылаться на элементы Extern>. Символическое имя импортируется из файла \<заголовка, указанного в элементе Extern>, если оно соответствует простому шаблону #define SYMBOL VALUE. Значение может быть еще одним символом до тех пор, пока этот символ был ранее определен. Определения GUID должны быть либо в формате OLE, либо в формате СЗЗ. Значения идентификатора могут быть как десятичными цифрами, так и гексадецичными цифрами, которым предшествует 0x, как показано в следующих строках:

- 6D484634-E53D-4a2c-ADCB-55145C9362C8

- 0x6d484634, 0xe53d, 0x4a2c, 0xad, 0xcb, 0x55, 0x14, 0x5c, 0x93, 0x62, 0xc8

  Комментарии XML могут быть использованы, но инструменты графического пользовательского интерфейса (GUI) в оба конца могут отказаться от них. Содержимое \<аннотации> элементы гарантированно сохраняются независимо от формата.

## <a name="schema-hierarchy"></a>Иерархия схемы
 Файл .vsct имеет следующие основные элементы.

- [Элемент CommandTable](../extensibility/commandtable-element.md)

- [Элемент Экстерн](../extensibility/extern-element.md)

- [Включить элемент](../extensibility/include-element.md)

- [Определить элемент](../extensibility/define-element.md)

- [Элемент команд](../extensibility/commands-element.md)

- [Элемент командных мест](../extensibility/commandplacements-element.md)

- [Элемент VisibilityConstraints](../extensibility/visibilityconstraints-element.md)

- [Элемент KeyBindings](../extensibility/keybindings-element.md)

- [Элемент подержанных команд](../extensibility/usedcommands-element.md)

- [Родительский элемент](../extensibility/parent-element.md)

- [Элемент значка](../extensibility/icon-element.md)

- [Элемент струн](../extensibility/strings-element.md)

- [Элемент флага командования](../extensibility/command-flag-element.md)

- [Элемент символов](../extensibility/symbols-element.md)

- [Условные атрибуты](../extensibility/vsct-xml-schema-conditional-attributes.md)

## <a name="see-also"></a>См. также
- [Как VSPackages добавляют элементы пользовательского интерфейса](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Командная размытая в VSPackages](../extensibility/internals/command-routing-in-vspackages.md)
