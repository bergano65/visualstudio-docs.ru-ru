---
title: Элемент IDSymbol | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDSymbol element (VSCT XML schema)
- VSCT XML schema elements, IDSymbol
ms.assetid: 760cfd20-3c06-422c-9103-98bfa1f387f8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 71979bd4f859257555c9d72ac5521a5ae21b9ed4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31127530"
---
# <a name="idsymbol-element"></a>Элемент IDSymbol
`IDSymbol` Элемент содержит идентификатор, представляющий меню, группы или команды пару. Идентификатор GUID поступают из родительского `GuidSymbol` элемента. `IDSymbol` Элемент имеет `name` атрибут, который содержит понятное имя для идентификатора, который содержится в `value` атрибута.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<IDSymbol name=ElementName value="0x0010" />  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|имя|Обязательно. Имя символа идентификатора.|  
|value|Обязательно. Числовое значение идентификатора символа идентификатора.|  
  
### <a name="child-elements"></a>Дочерние элементы  
 Отсутствует.  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[Элемент GuidSymbol](../extensibility/guidsymbol-element.md)|Содержит идентификатор GUID, представляющий меню, группы или команды пару. Группирует элементы `IDSymbol`.|  
  
## <a name="remarks"></a>Примечания  
 Каждый `IDSymbol` элемент в заданной `GuidSymbol` элемент должен иметь уникальный `value`. Тем не менее `IDSymbol` при условии, что они имеют разные родительские элементы, имеющие идентичные значения могут существовать в пакете.  
  
## <a name="see-also"></a>См. также  
 [Файлы таблицы команд Visual Studio (VSCT-файлы)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)