---
title: ВидимостьПункт Элемент (англ.) Документы Майкрософт
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698153"
---
# <a name="visibilityitem-element"></a>Элемент VisibilityItem
Элемент `VisibilityItem` определяет статическую видимость команд и панелей инструментов. Каждая запись определяет команду или меню, а также связанный контекст uI- управления. Visual Studio обнаруживает команды, меню и панели инструментов, а также их видимость, не загружая VSPackages, которые определяют их. IDE использует <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> метод для определения активности контекста командного uI.

 После загрузки VSPackage Visual Studio ожидает, что видимость команды будет `VisibilityItem`определяться VSPackage, а не . Чтобы определить видимость вашей команды, можно <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> реализовать обработчик событий или <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> метод, в зависимости от того, как вы реализовали команду.

 Команда или меню с `VisibilityItem` элементом отосвазались только при активной активности связанного контекста. Можно связать одну команду, меню или панель инструментов с одним или несколько контекстами командного uI, включив запись для каждой комбинации командно-контекстного. Если команда или меню связаны с несколькими контекстами командного uI, то команда или меню видны при активном иомы, связанном с ними.

 Элемент `VisibilityItem` применяется только к командам, меню и панели инструментов, а не к группам. Элемент, не имеюв `VisibilityItem` связанного элемента, отображается всякий раз, когда его родительское меню активируется.

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
|guid|Обязательный элемент. GUID идентификатора команды GUID/ID.|
|идентификатор|Обязательный элемент. Идентификатор идентификатора идентификатора команды GUID/ID.|
|контекст|Обязательный элемент. Контекст uI, в котором отображается команда.|
|Условие|Необязательный параметр. Посмотреть [условные атрибуты.](../extensibility/vsct-xml-schema-conditional-attributes.md)|

### <a name="child-elements"></a>Дочерние элементы
 Отсутствуют

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[Элемент VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|Элемент `VisibilityConstraints` определяет статическую видимость групп команд и панели инструментов.|

## <a name="remarks"></a>Примечания
 Стандартные контексты визуальной студии uI определяются в *пути установки Visual Studio SDK*(VisualStudioIntegration)-Common-Inc'vsshlids.h файла, а также в классах <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids> и <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> классах. В <xref:Microsoft.VisualStudio.VSConstants> классе определяется более полный набор контекстов uI.

## <a name="example"></a>Пример

```xml
<VisibilityConstraints>
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"
    context="guidNotViewSourceMode"/>
</VisibilityConstraints>
```

## <a name="see-also"></a>См. также
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A>
- <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus>
- <xref:Microsoft.VisualStudio.VSConstants>
- <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids>
- <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>
- [Элемент VisibilityConstraints](../extensibility/visibilityconstraints-element.md)
- [Командный стол Visual Studio (. Vsct) Файлы](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
