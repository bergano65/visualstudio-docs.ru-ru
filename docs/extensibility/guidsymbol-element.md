---
title: Элемент GuidSymbol | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, GuidSymbol
- GuidSymbol element (VSCT XML schema)
ms.assetid: 11fb3545-8974-4776-9a54-6b6e7739ae31
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6d5e3a3f4d33e166d344669dbeb4bc1a877335f0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="guidsymbol-element"></a>Элемент GuidSymbol
`GuidSymbol` Элемент содержит идентификатор GUID, представляющий меню, группы или команды пару. Идентификатор поступают из `IDSymbol` элемент в `GuidSymbol` элемент. `GuidSymbol` Элемент имеет `name` атрибут, который содержит понятное имя для идентификатора GUID, который содержится в `value` атрибута.  
  
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
|[Элемент IDSymbol](../extensibility/idsymbol-element.md)|Содержит идентификатор, представляющий меню, группы или команды пару.|  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[Элемент Symbols](../extensibility/symbols-element.md)|Группы `GuidSymbol` элементов в vsct-файл.|  
  
## <a name="remarks"></a>Примечания  
 Как правило, vsct-файл содержит три `GuidSymbol` элементов в его `Symbols` раздел, для самого пакета, один для набора команд (коллекция меню, группы и команды, которые пакет делает доступными) и один для точечных рисунков, которые предоставляют значки для кнопки и другие визуальные компоненты. Каждый `IDSymbol` элемент в заданной `GuidSymbol` элемент должен иметь уникальный `value`. Тем не менее `IDSymbol` при условии, что они имеют разные родительские элементы, имеющие идентичные значения могут существовать в пакете.  
  
## <a name="see-also"></a>См. также  
 [Файлы таблицы команд Visual Studio (VSCT-файлы)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)