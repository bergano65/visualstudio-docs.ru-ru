---
title: Условные атрибуты схемы VSCT XML | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, conditional attributes
- conditional attributes (VSCT XML schema)
ms.assetid: 754d4f32-319b-44c9-915f-f7c60e53222e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 975ca2f5fa6f070baf07b26cbfa0d8c3aa3b67d2
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31138360"
---
# <a name="vsct-xml-schema-conditional-attributes"></a>Условные атрибуты схемы VSCT XML
Условные атрибуты могут быть применены к все списки и элементы. Логические операторы и выражения расширения символ вычислить значение true или false. Значение true, если связанный список или элемент включается в результат.  
  
 Токен расширения можно протестировать от других маркеров расширений или константы. Функция Defined() используется для проверки определенного имени определен, даже если он не имеет значения.  
  
 При применении атрибута Condition в список, условие применяется для каждого дочернего элемента в списке. Если сам дочерний элемент содержит атрибут Condition, условия его объединяется в выражение родительского для операции и.  
  
 Значения 1, '1' и 'true' оцениваются как true, и 0, "0" и «false» получено значение false.  
  
## <a name="operators"></a>Операторы  
 Следующие операторы могут использоваться для вычисления условного выражения.  
  
|Оператор|Определение|  
|--------------|----------------|  
|(,)|Группирование|  
|!|Логическое НЕ|  
|\<, >, \<=, >=, ==, !=|Операторы отношения и равенства|  
|и|Boolean|  
|или|Boolean|  
  
## <a name="examples"></a>Примеры  
  
```  
<Menu Condition="Defined(DEBUG)" ...  
</Menu>  
  
<Menu Condition="%(SKU_MODE) = 'Demo'" ...  
</Menu>  
  
<Menus Condition="Defined(DEBUG)">  
    <Menu ...  
    </Menu>  
</Menus>  
  
<Menus Condition="Defined(DEMO_SKU)">  
    <Menus Condition="!Defined(DEBUG)">  
        <Menu ...  
        </Menu>  
    </Menus>  
  
    <Menu ...  
    </Menu>  
</Menus>  
  
<Menus Condition="(Defined(DEMO_SKU) or Defined(SAMPLE_SKU))   
and !Defined(DEBUG)">  
    <Menu ...  
    </Menu>  
</Menus>  
```  
  
## <a name="see-also"></a>См. также  
 [Файлы таблицы команд Visual Studio (VSCT-файлы)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)