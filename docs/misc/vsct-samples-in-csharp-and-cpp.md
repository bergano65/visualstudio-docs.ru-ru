---
title: "Примеры VSCT в C# и C++ | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSCT-файлы, примеры"
ms.assetid: 3218584b-c619-487c-9486-514b04937020
caps.latest.revision: 6
caps.handback.revision: 6
manager: "douge"
---
# Примеры VSCT в C# и C++
VSCT было новым способом определения команд.  Вследствие этого, произошло изменение в образце VSCT как компилировать в c\# и C\+\+.  Теперь команды определяются в C\+\+ с внешними файлами и c\# с разделом символов в файле .vsct.  
  
## Указание команд  
  
### Внешние файлы C\+\+  
 В образцах C\+\+ компилятор VSCT включает внешние файлы, чтобы задать константы, используемые внутри определений конкретных команд.  Способ включения эти файлы и таким образом определить константы в определениях пользовательских команд добавить `Extern` тег в .vsct и задает имя файла внешних файловых референций in  `href` атрибут.  Эти файлы включают:  
  
-   Guids.h  
  
-   CommandIDs.h  
  
-   Resources.h  
  
 Следующий фрагмент из файла c\+\+ .vsct показано, как включить эти файлы:  
  
 `<!--This is the file with the definition of the Guids specific for this sample.-->`  
  
 `<Extern href="Guids.h"/>`  
  
 `<!--Definition of the IDs of the commands and VSCT elements specific for this sample.-->`  
  
 `<Extern href="CommandIds.h"/>`  
  
 `<!--Definition of the resources exposed by this package.  Here it is used for the ID of the bitmap.-->`  
  
 `<Extern href="Resource.h"/>`  
  
### Символы C\#  
 В образцах c\# присутствует файл .vsct `Symbols` сам раздел в файле позволяют указать команды.  Определение символов в файле .vsct в стержнях c\# от способа идентификаторы элементов определяется таблицей команды.  Следующий фрагмент из файла c\# .vsct, указывающий команды и константы, связанные с ними:  
  
 `<Symbols>`  
  
 `<!--The first GUID defined here is the one for the package.  It does not contain numeric IDs.-->`  
  
 `<GuidSymbol name="guidMenuAndCommandsPkg" value="{746D5114-B030-4D64-9A6D-E2ABE1E78E56}" />`  
  
 `<!--The GUID for the command set is the one that contains the numeric IDs used in this sample`  
  
 `with the only exception of the one used for the bitmap.-->`  
  
 `<GuidSymbol name="guidMenuAndCommandsCmdSet" value="{10A79DAE-B33C-4FDB-8922-B056628858A1}">`  
  
 `<!--Menus-->`  
  
 `<IDSymbol name="MyToolbar" value="0x101" />`  
  
 `<!--Groups-->`  
  
 `<IDSymbol name="MyMenuGroup" value="0x1010" />`  
  
 `<IDSymbol name="MyToolbarGroup" value="0x1011" />`  
  
 `<IDSymbol name="MyMainToolbarGroup" value="0x1012" />`  
  
 `<IDSymbol name="MyEditorCtxGroup" value="0x1013" />`  
  
 `<!--Commands-->`  
  
 `<IDSymbol name="cmdidMyCommand" value="0x2001" />`  
  
 `<IDSymbol name="cmdidMyGraph" value="0x2002" />`  
  
 `<IDSymbol name="cmdidMyZoom" value="0x2003" />`  
  
 `<IDSymbol name="cmdidDynamicTxt" value="0x2004" />`  
  
 `<IDSymbol name="cmdidDynVisibility1" value="0x2005" />`  
  
 `<IDSymbol name="cmdidDynVisibility2" value="0x2006" />`  
  
 `</GuidSymbol>`  
  
 `<!--Last is the definition of the GUID used for the Bitmap and the ID of its used slots.-->`  
  
 `<GuidSymbol name="guidGenericCmdBmp" value="{0A4C51BD-3239-4370-8869-16E0AE8C0A46}">`  
  
 `<IDSymbol name="bmpArrow" value="1" />`  
  
 `</GuidSymbol>`  
  
 `</Symbols>`  
  
## Внедрение растровые изображения  
  
### C\#  
 Растровые изображения в binary настройке по порядку C\+\+ и c\#, сохраняются внешне на диске.  Идентификатор растрового изображения определено таким образом, что определение должно предоставить атрибут GUID для растрового изображения, a `resID` атрибут полосы растрового изображения, содержащий растровые изображения, а затем числовые идентификаторы элементов, используемых внутри определения кнопок \(`usedList` атрибут\).  Важным аспектом этого объявления, что идентификатор элемента должно быть реальным индексом \(нумерация начинается с 1\) растрового изображения в полосы растрового изображения.  
  
 В следующем примере прокладка растрового изображения включены, что содержит только один элемент.  Идентификатор для данного элемента задан как guidMenuAndCommandsCmdSet: bmpArrow, поэтому bmpArrow должен быть определен как 1.  Также объявление растрового изображения.  
  
 `<Bitmap guid="guidGenericCmdBmp" href="GenericCmd.bmp"    usedList="bmpArrow"/>`  
  
## См. также  
 [Таблицы команд Visual Studio \(. Файлы Vsct\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)