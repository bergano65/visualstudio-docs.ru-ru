---
title: Элемент Экстерна Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- Extern
helpviewer_keywords:
- VSCT XML schema elements, Extern
- Extern element (VSCT XML schema)
ms.assetid: db6c3ddd-a1ba-450a-897a-bb568a5377fc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2cf6f9db77abaa7034af8d074b9833a4c1560f07
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711491"
---
# <a name="extern-element"></a>Элемент Экстерн
Элемент Extern ссылается на любые внешние заголовки *(.h)* файлы для слияния с файлом *.vsct* во время компиляции. Файлы, которые должны быть объединены, должны находиться на пути включения, данном компилятором VSCT или на который ссылается [элемент Включить.](../extensibility/include-element.md) Файлы могут быть другими *файлами .vsct* или файлами заголовка C.

 Определения в файлах заголовка должны быть формы "#define "Символ" Значение может быть еще одним символом, если оно было ранее определено. Определения могут использоваться в условных заявлениях командных элементов. Любой символ, фактически не используемый, будет отброшен.

 Элемент CommandTable Элемент Экстерн

## <a name="syntax"></a>Синтаксис

```xml
<Extern href="stdidcmd.h" />
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

|Атрибут|Описание|
|---------------|-----------------|
|href|Обязательный элемент. Путь к файлу заголовка:<br /><br /> хрефе "stdidcmd.h"|
|Условие|Необязательный параметр. Посмотреть [условные атрибуты.](../extensibility/vsct-xml-schema-conditional-attributes.md)|
|Язык|Необязательный параметр. Язык по умолчанию всех [ \<струнных>](../extensibility/strings-element.md) элементов в таблице команд:<br /><br /> язык "ан-нас"|

### <a name="child-elements"></a>Дочерние элементы

|Элемент|Описание|
|-------------|-----------------|
|Нет.|Нет.|

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[Элемент CommandTable](../extensibility/commandtable-element.md)|Определяет все элементы, представляющие команды, т.е. пункты меню, меню, панели инструментов и комбо-коробки, которые VSPackage предоставляет IDE.|

## <a name="example"></a>Пример

```xml
<?xml version="1.0" encoding="utf-8"?>
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-
  18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">
    <Extern href="C:\VSCore\vscommon\inc\vsshlids.h"/>
    ...
  <Commands package="guidMyPackage">
</CommandTable>
```

## <a name="see-also"></a>См. также
- [Таблица команд Visual Studio (.vsct) файлов](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Как VSPackages добавляют элементы пользовательского интерфейса](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Команды, меню и панели инструментов](../extensibility/internals/commands-menus-and-toolbars.md)
