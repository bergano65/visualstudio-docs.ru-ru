---
title: Элемент команд (англ.) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- Commands
helpviewer_keywords:
- Commands element (VSCT XML schema)
- VSCT XML schema elements, Commands
ms.assetid: 47cf16a5-d78b-452e-86f6-b5893856dddf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3ea2400cca19a02475caecec3d022e0b78794ae4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739685"
---
# <a name="commands-element"></a>Элемент Commands
Представляет коллекцию команд на панели инструментов VSPackage. Коллекция может иметь до пяти подразделов, следующим образом: меню, группы, кнопки, комбо и бит-карты.

 Каждый элемент подраздела \<ребенка, например, Меню>, идентифицируется по уникальному идентификатору команды, который является GUID и числовой идентификаторной парой. GUID определяет "командный набор" и используется для группы логически связанных команд. VSPackage должен определить свой собственный набор команд, чтобы избежать столкновений с имитизмами команд, которые определяются другими VSPackages.

## <a name="syntax"></a>Синтаксис

```xml
<Commands package="GuidMyPackage" >
  <Menus>... </Menus>
  <Groups>... </Groups>
  <Buttons>... </Buttons>
  <Combos>... </Combos>
  <Bitmaps>... </Bitmaps>
</Commands>
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

|Атрибут|Описание|
|---------------|-----------------|
|пакет|GUID, который идентифицирует VSPackage, который предоставляет команды.<br /><br /> Например, пакет"guidVsPackage1Pkg".|

### <a name="child-elements"></a>Дочерние элементы

|Элемент|Описание|
|-------------|-----------------|
|[Элемент меню](../extensibility/menus-element.md)|Определяет все меню, которые реализует VSPackage.|
|[Элемент группы](../extensibility/groups-element.md)|Содержит записи, определяющие группы команд в VSPackage.|
|[Элемент кнопки](../extensibility/buttons-element.md)|Элементы кнопки групп.|
|[Элемент Bitmaps](../extensibility/bitmaps-element.md)|Элементы Битмап групп.|
|[Элемент комбо](../extensibility/combos-element.md)|Группы Комбо элементов.|

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[Элемент CommandTable](../extensibility/commandtable-element.md)|Определяет все элементы, представляющие команды, которые VSPackage предоставляет IDE. Возможные элементы меню, меню, панели инструментов и комбо-коробки.|

## <a name="example"></a>Пример
 Ниже приводится следующий пример, как использовать [элемент команд.](../extensibility/commands-element.md)

```
<Commands package="guidMyPackage">
    <Menus>
      <Menu Condition="'%(DEBUG)' != 'true'"
        guid="cmdSetGuidMyProductCommands" id="menuIDMainMenu"
        priority="0x0000" type="Menu">
        <Annotation>
          <Documentation>this is an annotation</Documentation>
          <AppInfo>
            <CustomData>
              <CustomSubElement>Some data</CustomSubElement>
            </CustomData>
          </AppInfo>
        </Annotation>
        <CommandFlag>AlwaysCreate</CommandFlag>
        <Strings>
          <ButtonText>MainMenu</ButtonText>
        </Strings>
      </Menu>
  </Menus>
<Commands>
```

## <a name="see-also"></a>См. также
- [Как VSPackages добавляют элементы пользовательского интерфейса](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Команды, меню и панели инструментов](../extensibility/internals/commands-menus-and-toolbars.md)
