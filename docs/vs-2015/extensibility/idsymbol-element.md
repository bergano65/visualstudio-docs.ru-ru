---
title: Элемент IDSymbol | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDSymbol element (VSCT XML schema)
- VSCT XML schema elements, IDSymbol
ms.assetid: 760cfd20-3c06-422c-9103-98bfa1f387f8
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7db4e686b5e105b0ea0aa80783137093679d4cad
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58989965"
---
# <a name="idsymbol-element"></a>Элемент IDSymbol
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`IDSymbol` Элемент содержит идентификатор GUID: ID пары, который представляет меню, группы или команды. Идентификатор GUID поступает из родительского `GuidSymbol` элемент. `IDSymbol` Элемент имеет `name` атрибут, который содержит понятное имя для идентификатора, который содержится в `value` атрибута.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<IDSymbol name=ElementName value="0x0010" />  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|имя|Обязательный. Имя символа идентификатора.|  
|value|Обязательный. Числовое значение идентификатора символа идентификатора.|  
  
### <a name="child-elements"></a>Дочерние элементы  
 Отсутствует.  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[Элемент GuidSymbol](../extensibility/guidsymbol-element.md)|Содержит идентификатор GUID пары GUID: ID, который представляет меню, группы или команды. Группирует элементы `IDSymbol`.|  
  
## <a name="remarks"></a>Примечания  
 Каждый `IDSymbol` элемент в заданной `GuidSymbol` элемент должен иметь уникальный `value`. Тем не менее `IDSymbol` до тех пор, пока они имеют разные родительские элементы, которые имеют одинаковые значения могут существовать в пакете.  
  
## <a name="see-also"></a>См. также  
 [Файлы таблицы команд Visual Studio (VSCT-файлы)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
