---
title: Определите элемент | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Define
- Define element (VSCT XML schema)
ms.assetid: 5aee74e3-de41-4dc6-9618-93e158af56dd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 69177b035ee8e0c162a629873110df9f7ec7917f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53889160"
---
# <a name="define-element"></a>Определение элемента
Определяет пару имя-значение символа. Этот символ может быть рассчитано условные атрибуты. Дополнительные сведения см. в разделе [условные атрибуты](../extensibility/vsct-xml-schema-conditional-attributes.md). См. также [элемент Symbols](../extensibility/symbols-element.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<Define name="Mode" value="Standard" />  
```  
  
## <a name="attributes-and-elements"></a>Элементы и атрибуты  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|имя|Обязательный. Имя символа:<br /><br /> Имя = «Режим»|  
|value|Обязательный. Значение символа:<br /><br /> значение = «Стандартный»|  
|Условие|Необязательный параметр. Дополнительные сведения см. в разделе [условные атрибуты](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Дочерние элементы  
 Отсутствует.  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание:|  
|-------------|-----------------|  
|[Элемент CommandTable](../extensibility/commandtable-element.md)|Определяет все элементы, которые представляют команды, предоставляемых VSPackage интегрированной среды разработки (IDE). Например пункты меню, меню, панелей инструментов и поля со списком.|  
  
## <a name="example"></a>Пример  
  
```  
<Define name="DEMO_UI"/>  
<Define name="MODE" value="Standard"/>  
```  
  
## <a name="see-also"></a>См. также  
 [Visual Studio командные файлы table (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)