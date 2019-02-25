---
title: Включите элемент | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- Include
helpviewer_keywords:
- Include element (VSCT XML schema)
- VSCT XML schema elements, Include
ms.assetid: c923dfe6-084a-4105-aec1-f0a3f8399c54
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d77cca0b197f939170fc92f4d7d07bcadae8b53d
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56722399"
---
# <a name="include-element"></a>Включить элемент
Элемент Include указывает файл, который можно найти на указанном экземпляре включить путь для вставки в текущем файле.  Все символы и типы, определенные станут частью скомпилированного результата.

## <a name="syntax"></a>Синтаксис

```csharp
<Include href="stdidcmd.h" />
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

|Атрибут|Описание:|
|---------------|-----------------|
|href|Обязательный. Путь к файлу заголовка:<br /><br /> href="stdidcmd.h"|
|Условие|Необязательный параметр. См. в разделе [условные атрибуты](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Дочерние элементы

|Элемент|Описание:|
|-------------|-----------------|
|Отсутствует.|Отсутствует.|

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание:|
|-------------|-----------------|
|[Элемент CommandTable](../extensibility/commandtable-element.md)|Определяет все элементы, которые представляют команды — то есть пунктов меню, меню, панелей инструментов и поля со списком, что VSPackage предоставляет интегрированную среду разработки.|

## <a name="example"></a>Пример

```
<Include href="PackagePlacements.vsct"/>
```

## <a name="see-also"></a>См. также
- [Visual Studio командные файлы table (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)