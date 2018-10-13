---
title: Элемент IDSymbol | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDSymbol element (VSCT XML schema)
- VSCT XML schema elements, IDSymbol
ms.assetid: 760cfd20-3c06-422c-9103-98bfa1f387f8
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3b4876144093d5e937a194095af1b128dc3efabd
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49253049"
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
|имя|Обязательно. Имя символа идентификатора.|  
|value|Обязательно. Числовое значение идентификатора символа идентификатора.|  
  
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

