---
title: Элемент GuidSymbol | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, GuidSymbol
- GuidSymbol element (VSCT XML schema)
ms.assetid: 11fb3545-8974-4776-9a54-6b6e7739ae31
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5f11ed48d9dcf961228957cf15db3815c00d14d7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204222"
---
# <a name="guidsymbol-element"></a>Элемент GuidSymbol
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`GuidSymbol`Элемент содержит GUID пары GUID: ID, представляющей меню, группу или команду. Идентификатор берется из `IDSymbol` элемента в `GuidSymbol` элементе. `GuidSymbol`Элемент имеет `name` атрибут, предоставляющий понятное имя GUID, которое содержится в `value` атрибуте.  
  
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
|name|Обязательный. Имя символа GUID.|  
|value|Обязательный. Идентификатор GUID символа GUID.|  
  
### <a name="child-elements"></a>Дочерние элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[Элемент IDSymbol](../extensibility/idsymbol-element.md)|Содержит идентификатор пары GUID: ID, представляющей меню, группу или команду.|  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[Элемент Symbols](../extensibility/symbols-element.md)|Группирует `GuidSymbol` элементы в vsct-файл.|  
  
## <a name="remarks"></a>Remarks  
 Как правило, vsct-файл содержит три `GuidSymbol` элемента в своем `Symbols` разделе: один для самого пакета, один для набора команд (коллекция меню, групп и команд, доступных для пакета), и один для точечных рисунков, которые предоставляют значки для кнопок и других визуальных компонентов. Каждый `IDSymbol` элемент в заданном `GuidSymbol` элементе должен иметь уникальное значение `value` . Однако `IDSymbol` в пакете могут существовать элементы, имеющие одинаковые значения, если они имеют разные родительские объекты.  
  
## <a name="see-also"></a>См. также:  
 [Файлы таблицы команд Visual Studio (VSCT-файлы)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
