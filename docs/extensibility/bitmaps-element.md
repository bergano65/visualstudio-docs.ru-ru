---
title: Растровые изображения элемента | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Bitmaps
- Bitmaps element (VSCT XML schema)
ms.assetid: 74652e1b-fcfa-421b-aa9f-fbc081d3b476
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ea89ae212a85ed2a164ce133d055aebe551cf545
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="bitmaps-element"></a>Растровые изображения элемента
Группы [растровое изображение элемента](../extensibility/bitmap-element.md) элементов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<Bitmaps>  
  <Bitmap>... </Bitmap>  
  <Bitmap>... </Bitmap>  
</Bitmaps>  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|Условие|Необязательный. В разделе [условные атрибуты](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Дочерние элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[Элемент Bitmaps](../extensibility/bitmaps-element.md)|Группирует элементы растрового изображения.|  
|[Элемент Bitmap](../extensibility/bitmap-element.md)|Определяет растрового изображения.|  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[Элемент Commands](../extensibility/commands-element.md)|Представляет коллекцию команд на панели инструментов для VSPackage.|  
  
## <a name="example"></a>Пример  
  
```  
<Bitmaps>  
  <Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" />  
  <Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS"  
    usedList="1, 2, 3, 4"/>  
</Bitmaps>  
```  
  
## <a name="see-also"></a>См. также  
 [Как добавить элементы пользовательского интерфейса в пакеты VSPackage](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Команды, меню и панели инструментов](../extensibility/internals/commands-menus-and-toolbars.md)