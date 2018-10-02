---
title: Элемент bitmaps | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSCT XML schema elements, Bitmaps
- Bitmaps element (VSCT XML schema)
ms.assetid: 74652e1b-fcfa-421b-aa9f-fbc081d3b476
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fb0e241b3767e8c730438ca29b6874d1a385ef2b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47572942"
---
# <a name="bitmaps-element"></a>Элемент Bitmaps
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [элемент Bitmaps](https://docs.microsoft.com/visualstudio/extensibility/bitmaps-element).  
  
Группы [точечный рисунок элемента](../extensibility/bitmap-element.md) элементов.  
  
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
|Условие|Необязательный. См. в разделе [условные атрибуты](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
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

