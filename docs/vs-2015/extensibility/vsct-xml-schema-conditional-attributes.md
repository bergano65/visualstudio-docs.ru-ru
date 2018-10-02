---
title: Условные атрибуты схемы VSCT XML | Документация Майкрософт
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
- VSCT XML schema elements, conditional attributes
- conditional attributes (VSCT XML schema)
ms.assetid: 754d4f32-319b-44c9-915f-f7c60e53222e
caps.latest.revision: 6
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 018c78d10af48a946ded543210404f397eee5ca4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47570890"
---
# <a name="vsct-xml-schema-conditional-attributes"></a>Условные атрибуты схемы XML VSCT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [VSCT XML-схема условного атрибуты](https://docs.microsoft.com/visualstudio/extensibility/vsct-xml-schema-conditional-attributes).  
  
Условные атрибуты могут быть применены к все списки и элементы. Логические операторы и выражения расширения символ оценки true или false. Значение true, если связанный список или элемент включается в результат.  
  
 Токен расширения можно протестировать других маркеров расширения или константы. Функция Defined() используется для проверки определенного имени будет определен, даже если он не имеет значения.  
  
 При применении атрибута Condition в список условие применяется к каждый дочерний элемент в списке. Если сам дочерний элемент содержит атрибут Condition, затем его условие в сочетании с родительское выражение, оператор «и».  
  
 Значения «true», "1" и 1 оцениваются как true, и 0, "0" и «false» получено значение false.  
  
## <a name="operators"></a>Операторы  
 Следующие операторы могут использоваться для оценки условных выражений.  
  
|Оператор|Определение|  
|--------------|----------------|  
|(,)|Группирование|  
|!|Логическое НЕ|  
|\<, >, \<=, >=, ==, !=|Операторы отношения и равенства|  
|и|Boolean|  
|или|Boolean|  
  
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
  
## <a name="see-also"></a>См. также  
 [Файлы таблицы команд Visual Studio (VSCT-файлы)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

