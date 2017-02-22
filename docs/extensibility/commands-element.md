---
title: "Элемент Commands | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Commands"
helpviewer_keywords: 
  - "Элемент Commands (VSCT XML-схемы)"
  - "Элементы схемы VSCT XML, команды"
ms.assetid: 47cf16a5-d78b-452e-86f6-b5893856dddf
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# Элемент Commands
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Представляет коллекцию команд на панели инструментов VSPackage. Коллекция может иметь до пяти подразделов следующим образом: меню, групп, кнопки, комбинировать и точечные рисунки.  
  
 Каждый подраздел дочерний элемент, например, \< меню \> определяется уникальный идентификатор команды, идентификатор GUID и пара числовой идентификатор. Идентификатор GUID определяет набор команд «» и используется для группировки логически связанных команд. VSPackage следует определить свой собственный набор команд для предотвращения конфликтов с идентификаторы команд, которые определены в других пакетов VSPackages.  
  
## Синтаксис  
  
```  
<Commands package="GuidMyPackage" >  
  <Menus>... </Menus>  
  <Groups>... </Groups>  
  <Buttons>... </Buttons>  
  <Combos>... </Combos>  
  <Bitmaps>... </Bitmaps>  
</Commands>  
```  
  
## Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### Атрибуты  
  
|Атрибут|Описание|  
|-------------|--------------|  
|пакет|Идентификатор GUID, определяющий VSPackage, который содержит команды.<br /><br /> Например, пакет \= «guidVsPackage1Pkg».|  
  
### Дочерние элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|[Элемент меню](../extensibility/menus-element.md)|Определяет все меню, которые реализует VSPackage.|  
|[Элемент Groups](../extensibility/groups-element.md)|Содержит элементы, которые определяют группы команд в VSPackage.|  
|[Элемент кнопки](../extensibility/buttons-element.md)|Группирует элементы кнопки.|  
|[Растровые изображения элемента](../extensibility/bitmaps-element.md)|Группирует элементы точечного рисунка.|  
|[Комбинировать элемент](../extensibility/combos-element.md)|Группирует элементы поля со списком.|  
  
### Родительские элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|[Элемент CommandTable](../extensibility/commandtable-element.md)|Определяет все элементы, представляющие команды, которые VSPackage предоставляет интегрированную среду разработки. Возможные элементы, элементы меню, меню, панелей инструментов и поля со списком.|  
  
## Пример  
 В следующем примере показано, как использовать [Commands Element](../extensibility/commands-element.md).  
  
```  
<Commands package="guidMyPackage"> <Menus> <Menu Condition="'%(DEBUG)' != 'true'" guid="cmdSetGuidMyProductCommands" id="menuIDMainMenu" priority="0x0000" type="Menu"> <Annotation> <Documentation>this is an annotation</Documentation> <AppInfo> <CustomData> <CustomSubElement>Some data</CustomSubElement> </CustomData> </AppInfo> </Annotation> <CommandFlag>AlwaysCreate</CommandFlag> <Strings> <ButtonText>MainMenu</ButtonText> </Strings> </Menu> </Menus> <Commands>  
```  
  
## См. также  
 [Как добавить элементы пользовательского интерфейса в пакеты VSPackage](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Команды, меню и панелей инструментов](../extensibility/internals/commands-menus-and-toolbars.md)