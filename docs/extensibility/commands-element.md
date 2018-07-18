---
title: Команды элемент | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- Commands
helpviewer_keywords:
- Commands element (VSCT XML schema)
- VSCT XML schema elements, Commands
ms.assetid: 47cf16a5-d78b-452e-86f6-b5893856dddf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2d905914c9819671cf8c77d81ec8d51302467a9d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31108486"
---
# <a name="commands-element"></a>Элемент Commands
Представляет коллекцию команд на панели инструментов для VSPackage. Коллекция может иметь до пяти подразделах, следующим образом: меню, группы, кнопки, комбинировать и растровые изображения.  
  
 Каждый подраздел дочерний элемент, например, \<меню >, определяется уникальный идентификатор команды, — это идентификатор GUID и пары числовой идентификатор. Идентификатор GUID определяет набор команд «» и используется для группировки логически связанных команд. Пакет VSPackage необходимо определить свои собственные команды, чтобы избежать возникновения конфликтов с идентификаторы команд, которые определены в других пакетов VSPackage.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<Commands package="GuidMyPackage" >  
  <Menus>... </Menus>  
  <Groups>... </Groups>  
  <Buttons>... </Buttons>  
  <Combos>... </Combos>  
  <Bitmaps>... </Bitmaps>  
</Commands>  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|пакет|Идентификатор GUID, определяющий пакет VSPackage, который предоставляет команды.<br /><br /> Например, пакет = «guidVsPackage1Pkg».|  
  
### <a name="child-elements"></a>Дочерние элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[Элемент Menus](../extensibility/menus-element.md)|Определяет все меню, которые реализует VSPackage.|  
|[Элемент Groups](../extensibility/groups-element.md)|Содержит записи, которые определяют группы команд в VSPackage.|  
|[Элемент Buttons](../extensibility/buttons-element.md)|Группирует элементы кнопки.|  
|[Элемент Bitmaps](../extensibility/bitmaps-element.md)|Группирует элементы растрового изображения.|  
|[Элемент Combos](../extensibility/combos-element.md)|Группирует элементы поля со списком.|  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[Элемент CommandTable](../extensibility/commandtable-element.md)|Определяет все элементы, которые представляют команды, которые VSPackage предоставляет интегрированную среду разработки. Возможные элементы являются пункты меню, меню, панелей инструментов и поля со списком.|  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как использовать [Commands, элемент](../extensibility/commands-element.md).  
  
```  
<Commands package="guidMyPackage">  
    <Menus>  
      <Menu Condition="'%(DEBUG)' != 'true'"   
        guid="cmdSetGuidMyProductCommands" id="menuIDMainMenu"   
        priority="0x0000" type="Menu">  
        <Annotation>  
          <Documentation>this is an annotation</Documentation>  
          <AppInfo>  
            <CustomData>  
              <CustomSubElement>Some data</CustomSubElement>  
            </CustomData>  
          </AppInfo>  
        </Annotation>  
        <CommandFlag>AlwaysCreate</CommandFlag>  
        <Strings>  
          <ButtonText>MainMenu</ButtonText>  
        </Strings>  
      </Menu>  
  </Menus>  
<Commands>  
```  
  
## <a name="see-also"></a>См. также  
 [Как добавить элементы пользовательского интерфейса в пакеты VSPackage](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Команды, меню и панели инструментов](../extensibility/internals/commands-menus-and-toolbars.md)