---
title: Элемент Висибилититем | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VisibilityItem element (VSCT XML schema)
- VSCT XML schema elements, VisibilityItem
ms.assetid: 0932f551-972d-4194-84bb-426e3e4375e4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9129d64e430d661bbdd8f7682e64c93650570211
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80698153"
---
# <a name="visibilityitem-element"></a>Висибилититем, элемент
`VisibilityItem`Элемент определяет статическую видимость команд и панелей инструментов. Каждая запись определяет команду или меню, а также связанный контекст пользовательского интерфейса команды. Visual Studio обнаруживает команды, меню и панели инструментов, а также их видимость, не загружая пакеты VSPackage, которые их определяют. Интегрированная среда разработки использует <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> метод, чтобы определить, активен ли контекст пользовательского интерфейса команды.

 После загрузки VSPackage Visual Studio считает, что видимость команды определяется пакетом VSPackage, а не `VisibilityItem` . Чтобы определить видимость команды, можно реализовать либо <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> обработчик событий <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> , либо метод в зависимости от того, как была реализована команда.

 Команда или меню, имеющие элемент, `VisibilityItem` отображается только в том случае, если связанный контекст является активным. Вы можете связать одну команду, меню или панель инструментов с одним или несколькими контекстами пользовательского интерфейса команды, включив запись для каждой комбинации контекста команды. Если команда или меню связана с несколькими контекстами пользовательского интерфейса командной строки, команда или меню видны, когда любой из связанных контекстов пользовательского интерфейса команды является активным.

 `VisibilityItem`Элемент применяется только к командам, меню и панелям инструментов, а не к группам. Элемент, который не имеет связанного элемента, `VisibilityItem` отображается, если его родительское меню активно.

## <a name="syntax"></a>Синтаксис

```xml
<VisibilityItem
  guid ="="cmdGuidMyProductCommands"
  id=="cmdidAddWidget"
  context="guidNotViewSourceMode"/>
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

|Атрибут|Описание|
|---------------|-----------------|
|guid|Обязательный. Идентификатор GUID идентификатора команды GUID/ID.|
|идентификатор|Обязательный. Идентификатор идентификатора команды GUID/ID.|
|контекст|Обязательный. Контекст пользовательского интерфейса, в котором отображается команда.|
|Условие|Необязательный элемент. См. раздел [Условные атрибуты](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Дочерние элементы
 Нет

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[Висибилитиконстраинтс, элемент](../extensibility/visibilityconstraints-element.md)|`VisibilityConstraints`Элемент определяет статическую видимость групп команд и панелей инструментов.|

## <a name="remarks"></a>Remarks
 Стандартные контексты пользовательского интерфейса Visual Studio определяются в файле \Висуалстудиоинтегратион\коммон\инк\всшлидс.х *пути установки пакета SDK для Visual Studio*, а также в <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids> <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> классах и. Более полный набор контекстов пользовательского интерфейса определяется в <xref:Microsoft.VisualStudio.VSConstants> классе.

## <a name="example"></a>Пример

```xml
<VisibilityConstraints>
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"
    context="guidNotViewSourceMode"/>
</VisibilityConstraints>
```

## <a name="see-also"></a>См. также раздел
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A>
- <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus>
- <xref:Microsoft.VisualStudio.VSConstants>
- <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids>
- <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>
- [Висибилитиконстраинтс, элемент](../extensibility/visibilityconstraints-element.md)
- [Командная таблица Visual Studio (. Vsct) файлы](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
