---
title: Элемент Symbols | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- Symbols element (VSCT XML schema)
- VSCT XML schema elements, Symbols
ms.assetid: 1cda43d8-42a5-4b1b-a3c8-cf0401c3202f
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c8d28d225bd3a8d5c105bf54b9c63574002aed15
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160462"
---
# <a name="symbols-element"></a>Элемент Symbols
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Определяет идентификаторы GUID и идентификаторы, используемые другими элементами VSCT. Для неуправляемого кода эти сведения обычно поступают из файлов заголовков, которые задаются с помощью [внешнего элемента](../extensibility/extern-element.md). Для определения этих сведений управляемый код использует дочерние элементы элемента Symbols.  
  
 Если создать vsct-файл из существующего CTO-файла, символы будут созданы как дочерние элементы элемента Symbols. Дополнительные сведения см. в разделе [инструкции. Создание. Vsct файл из существующего. Файл CTO](../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file.md).  
  
 Элемент Symbols не следует путать с [элементом define](../extensibility/define-element.md), который определяет пары «имя-значение» для использования препроцессором.  
  
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
|None||  
  
### <a name="child-elements"></a>Дочерние элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|GuidSymbol|Определяет символ GUID. GuidSymbol имеет два обязательных атрибута: Name и value. Имя — это имя символа, а значение — значение GUID в виде строки.<br /><br /> Пример: \<GuidSymbol name="guidVsPackage1Pkg"   value="{c5f54698-101a-4846-84d3-dc748f9cd848}" />|  
|IDSymbol|Определяет символ. IDSymbol имеет два обязательных атрибута: Name и value. Имя — это имя символа, а значение — значение символа в виде строки.<br /><br /> Пример: \<IDSymbol name="MyMenuGroup" value="0x1020" />|  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[Элемент CommandTable](../extensibility/commandtable-element.md)|Корневой элемент файла. vsct.|  
  
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
  
## <a name="see-also"></a>См. также:  
 [Файлы таблицы команд Visual Studio (VSCT-файлы)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
