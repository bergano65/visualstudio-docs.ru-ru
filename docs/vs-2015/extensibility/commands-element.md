---
title: Команды элемент | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- Commands
helpviewer_keywords:
- Commands element (VSCT XML schema)
- VSCT XML schema elements, Commands
ms.assetid: 47cf16a5-d78b-452e-86f6-b5893856dddf
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 194768a3b540511996e1d99e6450a7a9b24ebc74
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58989791"
---
# <a name="commands-element"></a>Элемент Commands
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Представляет коллекцию команд на панели инструментов для VSPackage. Коллекция может иметь до пяти подразделах, следующим образом: меню, группы, кнопки, комбинировать и точечные рисунки.  
  
 Каждый подраздел дочерний элемент, к примеру, \<меню >, определяется уникальный идентификатор команды, — это идентификатор GUID и пары числовой идентификатор. Идентификатор GUID определяет набор команд «» и используется для группировки логически связанных команд. VSPackage следует определить свой собственный набор команд для предотвращения конфликтов с идентификаторы команд, которые определяются других пакетов VSPackage.  
  
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
|пакет|GUID, определяющий VSPackage, предоставляющий команды.<br /><br /> Например, пакет = «guidVsPackage1Pkg».|  
  
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
 В следующем примере показано, как использовать [элемент Commands](../extensibility/commands-element.md).  
  
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
