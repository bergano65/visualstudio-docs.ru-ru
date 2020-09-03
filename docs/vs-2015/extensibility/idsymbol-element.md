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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203970"
---
# <a name="idsymbol-element"></a>Элемент IDSymbol
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`IDSymbol`Элемент содержит идентификатор пары GUID: ID, представляющей меню, группу или команду. Идентификатор GUID поступает из родительского `GuidSymbol` элемента. `IDSymbol`Элемент имеет `name` атрибут, который предоставляет понятное имя для идентификатора, содержащегося в `value` атрибуте.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<IDSymbol name=ElementName value="0x0010" />  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|name|Обязательный. Имя символа идентификатора.|  
|value|Обязательный. Числовое значение идентификатора символа идентификатора.|  
  
### <a name="child-elements"></a>Дочерние элементы  
 Отсутствует.  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[Элемент GuidSymbol](../extensibility/guidsymbol-element.md)|Содержит идентификатор GUID пары GUID: ID, представляющей меню, группу или команду. Группирует элементы `IDSymbol`.|  
  
## <a name="remarks"></a>Remarks  
 Каждый `IDSymbol` элемент в заданном `GuidSymbol` элементе должен иметь уникальное значение `value` . Однако `IDSymbol` в пакете могут существовать элементы, имеющие одинаковые значения, если они имеют разные родительские объекты.  
  
## <a name="see-also"></a>См. также:  
 [Файлы таблицы команд Visual Studio (VSCT-файлы)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
