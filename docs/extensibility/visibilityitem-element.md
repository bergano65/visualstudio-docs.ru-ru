---
title: Элемент VisibilityItem | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VisibilityItem element (VSCT XML schema)
- VSCT XML schema elements, VisibilityItem
ms.assetid: 0932f551-972d-4194-84bb-426e3e4375e4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 85cc2a3d65d5a4763aeca231175201cf55a74b3e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31143469"
---
# <a name="visibilityitem-element"></a>Элемент VisibilityItem
`VisibilityItem` Элемент определяет статические видимость команды и панели инструментов. Каждая запись определяет команду или меню, а также связанная команда контекста пользовательского интерфейса. Visual Studio обнаруживает команд, меню и панелей инструментов и их видимости без загрузки пакетов VSPackage, их определения. Интегрированная среда разработки использует <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> метод, чтобы определить, активен ли контекст пользовательского интерфейса командной строки.  
  
 После загрузки VSPackage, Visual Studio ожидает видимость команды должны определяться в пакете VSPackage, а не `VisibilityItem`. Чтобы определить видимость вашей команды, можно реализовать <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> обработчика событий или <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> метод в зависимости от реализации вашей команды.  
  
 Команда или меню, которое содержит `VisibilityItem` элемент отображается, только когда активна связанного контекста. Одной команды, меню или панели инструментов можно связать с одного контекста команды пользовательского интерфейса, включая запись для каждого сочетания контекста команды. Если команды или меню не связан с несколько контекстов команды пользовательского интерфейса, затем команду или меню отображается при активном любого из пользовательского интерфейса контекстов связанная команда.  
  
 `VisibilityItem` Элемент применяется только к команд, меню и панелей инструментов, а не к группам. Элемент, который не имеет связанный с ним `VisibilityItem` элемент является видимым, когда активно его родительском меню.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<VisibilityItem  
  guid ="="cmdGuidMyProductCommands"  
  id=="cmdidAddWidget"  
  context="guidNotViewSourceMode"/>  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|guid|Обязательно. Идентификатор GUID идентификатор GUID или идентификатор команды.|  
|id|Обязательно. Идентификатор идентификатор GUID или идентификатор команды.|  
|контекст|Обязательно. Контекст пользовательского интерфейса, в котором отображается команда.|  
|Условие|Необязательный. В разделе [условные атрибуты](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Дочерние элементы  
 Нет  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[Элемент VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|`VisibilityConstraints` Элемент определяет видимость статических групп, команд и панелей инструментов.|  
  
## <a name="remarks"></a>Примечания  
 Определенные стандартные контексты пользовательского интерфейса Visual Studio в *путь установки Visual Studio SDK*\VisualStudioIntegration\Common\Inc\vsshlids.h также файл в качестве <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids> и <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> классы. Более полный набор контекстов пользовательского интерфейса, определенные в <xref:Microsoft.VisualStudio.VSConstants> класса.  
  
## <a name="example"></a>Пример  
  
```  
<VisibilityConstraints>  
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"  
    context="guidNotViewSourceMode"/>  
</VisibilityConstraints>  
```  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A>   
 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus>   
 <xref:Microsoft.VisualStudio.VSConstants>   
 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids>   
 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>   
 [Элемент VisibilityConstraints](../extensibility/visibilityconstraints-element.md)   
 [Файлы таблицы команд Visual Studio (VSCT-файлы)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)