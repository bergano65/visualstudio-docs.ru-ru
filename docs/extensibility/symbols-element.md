---
title: Элемент Symbols | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Symbols element (VSCT XML schema)
- VSCT XML schema elements, Symbols
ms.assetid: 1cda43d8-42a5-4b1b-a3c8-cf0401c3202f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 201faded164eba9a82ef412924b327aba762b14b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55027026"
---
# <a name="symbols-element"></a>Элемент Symbols
Определяет идентификаторы GUID и идентификаторы, которые используются другими элементами VSCT. Для неуправляемого кода, эти сведения обычно берутся из файлов заголовков, которые определяются [элемент Extern](../extensibility/extern-element.md). Управляемый код использует дочерние элементы элемента символы для определения этой информации.  
  
 При создании vsct-файл из существующего файла cto, символы будут создаваться как дочерние элементы элемента символы. Дополнительные сведения см. в разделе [Как Создать. Vsct-файл из существующего. Руководитель технологического отдела компании файл](../extensibility/internals/how-to-create-a-dot-vsct-file.md#how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file).  
  
 Элемент Symbols не следует путать с [определить элемент](../extensibility/define-element.md), который определяет пары имя значение для использования препроцессором.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<Symbols>  
  <GuidSymbol>... </GuidSymbol>  
  <GuidSymbol>... </GuidSymbol>  
</Symbols>  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание:|  
|---------------|-----------------|  
|Нет||  
  
### <a name="child-elements"></a>Дочерние элементы  
  
|Элемент|Описание:|  
|-------------|-----------------|  
|GuidSymbol|Определяет символ GUID. GuidSymbol имеет два обязательных атрибута: имя и значение. Имя является именем символа, а значение является значением идентификатора GUID как строка.<br /><br /> Например:\<GuidSymbol имя = значение «guidVsPackage1Pkg» = «{c5f54698-101a-4846-84d3-dc748f9cd848}» / >|  
|IDSymbol|Определяет символ. IDSymbol имеет два обязательных атрибута: имя и значение. Имя является именем символа, а значение является значением символа как строка.<br /><br /> Например:\<IDSymbol имя = значение «MyMenuGroup» = «0x1020» / >|  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[Элемент CommandTable](../extensibility/commandtable-element.md)|Корневой элемент файла .vsct.|  
  
## <a name="example"></a>Пример  
  
```  
<Symbols>  
  <GuidSymbol name="guidVsPackage1Pkg" value="{c5f54698-101a-4846-84d3-dc748f9cd848}" />  
  <GuidSymbol name="guidVsPackage1CmdSet" value="{cb9dfd7f-2fcc-4a3e-aae8-f7fe30b1cfac}">  
    <IDSymbol name="MyMenuGroup" value="0x1020" />  
    <IDSymbol name="cmdidMyCommand" value="0x0100" />  
    <IDSymbol name="cmdidMyTool" value="0x0101" />  
  </GuidSymbol>  
</Symbols>  
```  
  
## <a name="see-also"></a>См. также  
 [Файлы таблицы команд Visual Studio (VSCT-файлы)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)