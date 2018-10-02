---
title: Элемент Symbols | Документация Майкрософт
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
- Symbols element (VSCT XML schema)
- VSCT XML schema elements, Symbols
ms.assetid: 1cda43d8-42a5-4b1b-a3c8-cf0401c3202f
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d36bcf22d012d4543267d1b57d41567baf3e85b1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47563475"
---
# <a name="symbols-element"></a>Элемент Symbols
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [элемент Symbols](https://docs.microsoft.com/visualstudio/extensibility/symbols-element).  
  
Определяет идентификаторы GUID и идентификаторы, которые используются другими элементами VSCT. Для неуправляемого кода, эти сведения обычно берутся из файлов заголовков, которые определяются [элемент Extern](../extensibility/extern-element.md). Управляемый код использует дочерние элементы элемента символы для определения этой информации.  
  
 При создании vsct-файл из существующего файла cto, символы будут создаваться как дочерние элементы элемента символы. Дополнительные сведения см. в разделе [как: создание. Vsct-файл из существующего. Руководитель технологического отдела компании файл](../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file.md).  
  
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
  
|Атрибут|Описание|  
|---------------|-----------------|  
|Нет||  
  
### <a name="child-elements"></a>Дочерние элементы  
  
|Элемент|Описание|  
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

