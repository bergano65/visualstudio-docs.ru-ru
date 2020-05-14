---
title: Элемент символов Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Symbols element (VSCT XML schema)
- VSCT XML schema elements, Symbols
ms.assetid: 1cda43d8-42a5-4b1b-a3c8-cf0401c3202f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5c24c3f84df23a07b6b16272b66b29e32ad7b911
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699351"
---
# <a name="symbols-element"></a>Элемент Symbols
Определяет GUIDи и идентифицированные идентифицируются, которые используются другими элементами VSCT. Для неуправляемого кода эта информация обычно поступает из файлов заголовка, указанных [Extern Element.](../extensibility/extern-element.md) Управляемый код использует элемент «ребенок» элемента символов для определения этой информации.

 При создании файла .vsct из существующего файла .cto символы будут создаваться как дети элемента символов. Для получения дополнительной информации [см. Vsct файл из существующего . Cto Файл](../extensibility/internals/how-to-create-a-dot-vsct-file.md#how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file).

 Элемент символов не следует путать с [элементом определения,](../extensibility/define-element.md)который определяет пары значения имени для использования препроцессором.

## <a name="syntax"></a>Синтаксис

```
<Symbols>
  <GuidSymbol>... </GuidSymbol>
  <GuidSymbol>... </GuidSymbol>
</Symbols>
```

## <a name="attributes-and-elements"></a>Атрибуты и элементы
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

|Атрибут|Описание|
|---------------|-----------------|
|None||

### <a name="child-elements"></a>Дочерние элементы

|Элемент|Описание|
|-------------|-----------------|
|ГидСимвол|Определяет символ GUID. GuidSymbol имеет два необходимых атрибута: имя и значение. Название — это имя символа, а значение — значение GUID как строки.<br /><br /> Например:\<имя GuidSymbol'"guidVsPackage1Pkg" значение "c5f54698-101a-4846-84d3-dc748f9cd848" />|
|IDСимвол|Определяет символ. IDSymbol имеет два необходимых атрибута: имя и значение. Название — это имя символа, а значение — значение символа как строки.<br /><br /> Например:\<название IDSymbol "MyMenuGroup" значение "0x1020" />|

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[Элемент CommandTable](../extensibility/commandtable-element.md)|Корневой элемент файла .vsct.|

## <a name="example"></a>Пример

```
<Symbols>
  <GuidSymbol name="guidVsPackage1Pkg" value="{c5f54698-101a-4846-84d3-dc748f9cd848}" />
  <GuidSymbol name="guidVsPackage1CmdSet" value="{cb9dfd7f-2fcc-4a3e-aae8-f7fe30b1cfac}">
    <IDSymbol name="MyMenuGroup" value="0x1020" />
    <IDSymbol name="cmdidMyCommand" value="0x0100" />
    <IDSymbol name="cmdidMyTool" value="0x0101" />
  </GuidSymbol>
</Symbols>
```

## <a name="see-also"></a>См. также
- [Файлы таблицы команд Visual Studio (VSCT-файлы)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
