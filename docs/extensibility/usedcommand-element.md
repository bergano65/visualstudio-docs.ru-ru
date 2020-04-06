---
title: ПодержанныйЭлемент Командования (англ.) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 99cd05d3-644a-42ff-b289-8458cd1b20c0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 65030c3fe24c3456b0c4c99a667362d2a4c67703
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698828"
---
# <a name="usedcommand-element"></a>Элемент UsedCommand
Позволяет VSPackage получить доступ к команде, которая определена в другом файле .vsct. Например, если ваш VSPackage использует стандартную команду [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **Copy,** которая определяется оболочкой, можно добавить команду в меню или панель инструментов, не реализовав ее.

## <a name="syntax"></a>Синтаксис

```
<UsedCommand guid="guidMyCommandGroup" id="MyCommand" />
```

## <a name="attributes-and-elements"></a>Атрибуты и элементы
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

|Атрибут|Описание|
|---------------|-----------------|
|guid|Обязательный элемент. GUID пары Идентификаторов GUID, которая идентифицирует команду.|
|идентификатор|Обязательный элемент. Идентификатор пары GUID ID, идентифицирующий команду.|
|Условие|Необязательный параметр. Смотрите [Условные атрибуты](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Дочерние элементы

|Элемент|Описание|
|-------------|-----------------|
|None||

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[Элемент UsedCommands](../extensibility/usedcommands-element.md)|Группы использовалиэлементы команды и другие группировки UsedCommands.|

## <a name="remarks"></a>Примечания
 Добавляя команду в `<UsedCommands>` элемент, VSPackage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] информирует среду о том, что VSPackage требует команды. Следует добавить `<UsedCommand>` элемент для любой команды, который требуется пакету, который не может быть включен во все версии и конфигурации Visual Studio. Например, если ваш пакет вызывает команду, специфичную для Visual C, команда будет недоступна `<UsedCommand>` пользователям Visual Web Developer, если вы не включите элемент для команды.

## <a name="example"></a>Пример

```
<UsedCommands>
  <UsedCommand guid="guidVSStd97" id="cmdidCut"/>
  <UsedCommand guid="guidVSStd97" id="cmdidCopy"/>
  <UsedCommand guid="guidVSStd97" id="cmdidPaste"/>
</UsedCommands>
```

## <a name="see-also"></a>См. также
- [Элемент UsedCommands](../extensibility/usedcommands-element.md)
- [Файлы таблицы команд Visual Studio (VSCT-файлы)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
