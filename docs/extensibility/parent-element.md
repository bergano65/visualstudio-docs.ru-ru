---
title: Родительский элемент Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Parent
- Parent element (VSCT XML schema)
ms.assetid: e4624ac8-1b9a-4940-910a-528a661cefad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8c018505ba06762bf8426f266b24ee1835313c29
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702219"
---
# <a name="parent-element"></a>Родительский элемент
Родитель кнопки или комбо-бокса может быть только группой. Родитель меню или группы может быть любым другим меню или группой. В [элементе Командного Помещения](../extensibility/commandplacement-element.md)этот элемент необходим; во всех других случаях это необязательно. Если этот элемент опущен, материнский `Group_Undefined:0` элемент будет подразумеваться.

## <a name="syntax"></a>Синтаксис

```xml
<Parent guid="guidMyCommandSet" id="MyParentGroupOrMenu" />
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

|Атрибут|Описание|
|---------------|-----------------|
|guid|Обязательный элемент. GUID идентификатора команды GUID/ID.|
|идентификатор|Обязательный элемент. Идентификатор идентификатора идентификатора команды GUID/ID.|

### <a name="child-elements"></a>Дочерние элементы
 Отсутствуют

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[Элемент CommandTable](../extensibility/commandtable-element.md)|Определяет все элементы, представляющие команды, которые VSPackage предоставляет интегрированной среде разработки (IDE). Например, пункты меню, меню, панели инструментов и комбо-коробки.|
|[Элемент кнопки](../extensibility/buttons-element.md)|[Элементы элементов кнопки](../extensibility/button-element.md) групп.|
|[Элемент меню](../extensibility/menus-element.md)|Определяет все меню, которые реализует VSPackage.|
|[Элемент группы](../extensibility/groups-element.md)|Содержит записи, определяющие командные группы VSPackage.|

## <a name="see-also"></a>См. также
- [Таблица команд Visual Studio (.vsct) файлов](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
