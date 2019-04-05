---
title: Определите элемент | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, Define
- Define element (VSCT XML schema)
ms.assetid: 5aee74e3-de41-4dc6-9618-93e158af56dd
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8cc543a07176f307641c53a2ef3e132881821ce7
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58978557"
---
# <a name="define-element"></a>Элемент Define
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Определяет пару имя-значение символа. Этот символ может быть рассчитано условные атрибуты. Дополнительные сведения см. в разделе [условные атрибуты](../extensibility/vsct-xml-schema-conditional-attributes.md). См. также [символы элемент](../extensibility/symbols-element.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<Define name="Mode" value="Standard" />  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|имя|Обязательный. Имя символа:<br /><br /> Имя = «Режим»|  
|value|Обязательный. Значение символа:<br /><br /> value="Standard"|  
|Условие|Необязательный параметр. Дополнительные сведения см. в разделе [условные атрибуты](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Дочерние элементы  
 Отсутствует.  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[Элемент CommandTable](../extensibility/commandtable-element.md)|Определяет все элементы, которые представляют команды, предоставляемых VSPackage интегрированной среды разработки (IDE). Например пункты меню, меню, панелей инструментов и поля со списком.|  
  
## <a name="example"></a>Пример  
  
```  
<Define name="DEMO_UI"/>  
<Define name="MODE" value="Standard"/>  
```  
  
## <a name="see-also"></a>См. также  
 [Файлы таблицы команд Visual Studio (VSCT-файлы)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
