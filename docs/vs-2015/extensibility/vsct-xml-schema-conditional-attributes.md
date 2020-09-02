---
title: Условные атрибуты схемы XML VSCT | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, conditional attributes
- conditional attributes (VSCT XML schema)
ms.assetid: 754d4f32-319b-44c9-915f-f7c60e53222e
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6294ee8027b61840149096561efc91b8a4a3c3ec
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62422167"
---
# <a name="vsct-xml-schema-conditional-attributes"></a>Условные атрибуты схемы XML VSCT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Условные атрибуты могут применяться ко всем спискам и элементам. Логические операторы и выражения расширения символов имеют значение true или false. Если значение — true, связанный список или элемент включается в результирующие выходные данные.  
  
 Расширения маркеров можно протестировать по другим расширениям или константам. Определенная функция () используется для проверки того, определено ли определенное имя, даже если оно не имеет значения.  
  
 При применении к списку атрибута Condition условие применяется к каждому дочернему элементу в списке. Если дочерний элемент содержит атрибут Condition, то его условие объединяется с родительским выражением операцией и.  
  
 Значения 1, "1" и "true" оцениваются как true, а 0, "0" и "false" вычисляются как "false".  
  
## <a name="operators"></a>Операторы  
 Для вычисления условных выражений можно использовать следующие операторы.  
  
|Оператор|Определение|  
|--------------|----------------|  
|(,)|Группирование|  
|!|Логическое НЕ|  
|\<, >, \<=, >=, ==, !=|Операторы отношения и равенства|  
|и|Логическое|  
|или|Логическое|  
  
## <a name="examples"></a>Примеры  
  
```  
<Menu Condition="Defined(DEBUG)" …  
</Menu>  
  
<Menu Condition="%(SKU_MODE) = 'Demo'" …  
</Menu>  
  
<Menus Condition="Defined(DEBUG)">  
    <Menu …  
    </Menu>  
</Menus>  
  
<Menus Condition="Defined(DEMO_SKU)">  
    <Menus Condition="!Defined(DEBUG)">  
        <Menu …  
        </Menu>  
    </Menus>  
  
    <Menu …  
    </Menu>  
</Menus>  
  
<Menus Condition="(Defined(DEMO_SKU) or Defined(SAMPLE_SKU))   
and !Defined(DEBUG)">  
    <Menu …  
    </Menu>  
</Menus>  
```  
  
## <a name="see-also"></a>См. также:  
 [Файлы таблицы команд Visual Studio (VSCT-файлы)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
