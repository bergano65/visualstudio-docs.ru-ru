---
title: Элемент GuidSymbol | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, GuidSymbol
- GuidSymbol element (VSCT XML schema)
ms.assetid: 11fb3545-8974-4776-9a54-6b6e7739ae31
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d8b36df3fe4e546e8391d23ccadc33faf9f2a642
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54992884"
---
# <a name="guidsymbol-element"></a>Элемент GuidSymbol
`GuidSymbol` Элемент содержит идентификатор GUID пары GUID: ID, который представляет меню, группы или команды. Идентификатор поступает из `IDSymbol` элемент в `GuidSymbol` элемент. `GuidSymbol` Элемент имеет `name` атрибут, который содержит понятное имя для идентификатора GUID, который содержится в `value` атрибута.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
<GuidSymbol name="guidMyCommandSet" value="{xxxxxxxxxxxxx-xxxx-xxxx-xxxxxxxxxxxx}">  
  <IDSymbol>... </IDSymbol>  
  <IDSymbol>... </IDSymbol>  
</GuidSymbol>  
```  
  
## <a name="attributes-and-elements"></a>Элементы и атрибуты  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|имя|Обязательный. Имя символа идентификатора GUID.|  
|value|Обязательный. Идентификатор GUID символом GUID.|  
  
### <a name="child-elements"></a>Дочерние элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[Элемент IDSymbol](../extensibility/idsymbol-element.md)|Содержит идентификатор GUID: ID пары, который представляет меню, группы или команды.|  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание:|  
|-------------|-----------------|  
|[Элемент Symbols](../extensibility/symbols-element.md)|Группы `GuidSymbol` элементов в *.vsct* файла.|  
  
## <a name="remarks"></a>Примечания  
 Как правило *.vsct* файл содержит три `GuidSymbol` элементов в его `Symbols` раздела, для самого пакета, по одному для набора команд (набор меню, группы и команды, что пакет делает доступными), и одно для растровых изображений, предоставляющих значки для кнопок и другие визуальные компоненты. Каждый `IDSymbol` элемент в заданной `GuidSymbol` элемент должен иметь уникальный `value`. Тем не менее `IDSymbol` до тех пор, пока они имеют разные родительские элементы, которые имеют одинаковые значения могут существовать в пакете.  
  
## <a name="see-also"></a>См. также  
 [Visual Studio командные файлы table (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)