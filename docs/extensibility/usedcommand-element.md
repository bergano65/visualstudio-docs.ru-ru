---
title: Элемент Уседкомманд | Документация Майкрософт
description: Элемент Уседкомманд позволяет VSPackage использовать команду, определенную в другом vsct-файле.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- UsedCommands element (VSCT XML schema)
- VSCT XML schema elements, UsedCommands
ms.assetid: 99cd05d3-644a-42ff-b289-8458cd1b20c0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3c3f4a5f39e7cb999d9b3a86aa791464fca25645
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934107"
---
# <a name="usedcommand-element"></a>Элемент UsedCommand
Включает пакет VSPackage для доступа к команде, определенной в другом vsct-файле. Например, если пакет VSPackage использует стандартную команду **Copy** , определяемую [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] оболочкой, можно добавить команду в меню или на панель инструментов без повторной реализации.

## <a name="syntax"></a>Синтаксис

```
<UsedCommand guid="guidMyCommandGroup" id="MyCommand" />
```

## <a name="attributes-and-elements"></a>Атрибуты и элементы
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

|Атрибут|Описание|
|---------------|-----------------|
|guid|Обязательный элемент. Идентификатор GUID пары ИДЕНТИФИКАТОРов GUID, определяющей команду.|
|идентификатор|Обязательный элемент. Идентификатор пары ИДЕНТИФИКАТОРов GUID, определяющей команду.|
|Условие|Необязательный элемент. См. раздел [Условные атрибуты](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Дочерние элементы

|Элемент|Описание|
|-------------|-----------------|
|Отсутствуют||

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[Элемент UsedCommands](../extensibility/usedcommands-element.md)|Группирует элементы Уседкомманд и другие группирования Уседкоммандс.|

## <a name="remarks"></a>Remarks
 Добавив команду в `<UsedCommands>` элемент, VSPackage информирует [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] среду о том, что пакету VSPackage требуется команда. Необходимо добавить `<UsedCommand>` элемент для любой команды, которая требуется для пакета, которая может не включаться во все версии и конфигурации Visual Studio. Например, если пакет вызывает команду, относящуюся к Visual C++, команда будет недоступна пользователям Visual Web Developer, если не включить `<UsedCommand>` элемент для команды.

## <a name="example"></a>Пример

```
<UsedCommands>
  <UsedCommand guid="guidVSStd97" id="cmdidCut"/>
  <UsedCommand guid="guidVSStd97" id="cmdidCopy"/>
  <UsedCommand guid="guidVSStd97" id="cmdidPaste"/>
</UsedCommands>
```

## <a name="see-also"></a>См. также раздел
- [Элемент UsedCommands](../extensibility/usedcommands-element.md)
- [Файлы таблицы команд Visual Studio (VSCT-файлы)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
