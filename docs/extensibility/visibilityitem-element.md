---
title: "Элемент VisibilityItem | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Элемент VisibilityItem (VSCT XML-схемы)"
  - "Элементы схемы VSCT XML, VisibilityItem"
ms.assetid: 0932f551-972d-4194-84bb-426e3e4375e4
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Элемент VisibilityItem
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

`VisibilityItem` Элемент определяет статические видимость команды и панели инструментов. Каждая запись определяет команду или меню, а также контекст связанной команды пользовательского интерфейса. Visual Studio обнаруживает команд, меню и панелей инструментов и их видимости без загрузки пакетов VSPackages, их определения. Интегрированная среда разработки использует <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> метод, чтобы определить, активен ли контекст пользовательского интерфейса командной строки.  
  
 После загрузки VSPackage, Visual Studio ожидает видимость команда будет определяться VSPackage, а не `VisibilityItem`. Чтобы определить видимость вашей команды, можно реализовать <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> обработчика событий или <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> метод в зависимости от реализации вашей команды.  
  
 Команда или меню, который имеет `VisibilityItem` элемент отображается, только когда активна связанного контекста. Одной команды, меню или панель инструментов можно связать с одного контекста команд пользовательского интерфейса, включая запись для каждого сочетания контекст командной строки. Если команда или меню связана с нескольких контекстов пользовательского интерфейса команды, затем команды или меню отображается при активном любого из связанной команды контексты пользовательского интерфейса.  
  
 `VisibilityItem` Элемент применяется только для команд, меню и панели инструментов, а не к группам. Элемент, который не имеет связанного `VisibilityItem` элемент виден при каждом его родительском меню.  
  
## Синтаксис  
  
```  
<VisibilityItem  
  guid ="="cmdGuidMyProductCommands"  
  id=="cmdidAddWidget"  
  context="guidNotViewSourceMode"/>  
```  
  
## Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### Атрибуты  
  
|Атрибут|Описание|  
|-------------|--------------|  
|Идентификатор GUID|Обязательный. Идентификатор GUID идентификатор GUID и идентификатор команды.|  
|id|Обязательный. Идентификатор идентификатор GUID и идентификатор команды.|  
|контекст|Обязательный. Контекст пользовательского интерфейса, в котором отображается команда.|  
|Условие|Необязательный. См. раздел [Условные атрибуты](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### Дочерние элементы  
 Нет  
  
### Родительские элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|[Элемент VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|`VisibilityConstraints` Элемент определяет видимость статических групп, команд и панелей инструментов.|  
  
## Заметки  
 Стандартный пользовательский Интерфейс Visual Studio контексты определяются в *путь установки Visual Studio SDK*файл \\VisualStudioIntegration\\Common\\Inc\\vsshlids.h также как и в <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids> и <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> классы. Более полный набор контекстов пользовательского интерфейса, определенный в <xref:Microsoft.VisualStudio.VSConstants> класса.  
  
## Пример  
  
```  
<VisibilityConstraints> <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget" context="guidNotViewSourceMode"/> </VisibilityConstraints>  
```  
  
## См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A>   
 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus>   
 <xref:Microsoft.VisualStudio.VSConstants>   
 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids>   
 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>   
 [Элемент VisibilityConstraints](../extensibility/visibilityconstraints-element.md)   
 [Таблицы команд Visual Studio \(. Файлы Vsct\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)