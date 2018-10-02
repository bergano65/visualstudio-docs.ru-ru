---
title: Элемент GuidSymbol | Документация Майкрософт
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
- VSCT XML schema elements, GuidSymbol
- GuidSymbol element (VSCT XML schema)
ms.assetid: 11fb3545-8974-4776-9a54-6b6e7739ae31
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4e6e5bab37e9a0b9f0ffdf03778532d9657539c6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47563684"
---
# <a name="guidsymbol-element"></a>Элемент GuidSymbol
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [элемент GuidSymbol](https://docs.microsoft.com/visualstudio/extensibility/guidsymbol-element).  
  
`GuidSymbol` Элемент содержит идентификатор GUID пары GUID: ID, который представляет меню, группы или команды. Идентификатор поступает из `IDSymbol` элемент в `GuidSymbol` элемент. `GuidSymbol` Элемент имеет `name` атрибут, который содержит понятное имя для идентификатора GUID, который содержится в `value` атрибута.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<GuidSymbol name="guidMyCommandSet" value="{xxxxxxxxxxxxx-xxxx-xxxx-xxxxxxxxxxxx}">  
  <IDSymbol>... </IDSymbol>  
  <IDSymbol>... </IDSymbol>  
</GuidSymbol>  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|имя|Обязательно. Имя символа идентификатора GUID.|  
|value|Обязательно. Идентификатор GUID символом GUID.|  
  
### <a name="child-elements"></a>Дочерние элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[Элемент IDSymbol](../extensibility/idsymbol-element.md)|Содержит идентификатор GUID: ID пары, который представляет меню, группы или команды.|  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[Элемент Symbols](../extensibility/symbols-element.md)|Группы `GuidSymbol` элементов в vsct-файл.|  
  
## <a name="remarks"></a>Примечания  
 Как правило, vsct-файл содержит три `GuidSymbol` элементов в его `Symbols` раздел, для самого пакета, один для набора команд (коллекция меню, группы и команды, которые делает доступными пакета) и один для растровых изображений, которые предоставляют значки для кнопок и другие визуальные компоненты. Каждый `IDSymbol` элемент в заданной `GuidSymbol` элемент должен иметь уникальный `value`. Тем не менее `IDSymbol` до тех пор, пока они имеют разные родительские элементы, которые имеют одинаковые значения могут существовать в пакете.  
  
## <a name="see-also"></a>См. также  
 [Файлы таблицы команд Visual Studio (VSCT-файлы)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

